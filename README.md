# bar-code-detection-using-python
# Convert the image to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Detect barcodes in the grayscale image
barcodes = decode(gray)

if barcodes:
    for barcode in barcodes:
        # Extract barcode data and type
        barcode_data = barcode.data.decode('utf-8')
        barcode_type = barcode.type
        
        # Draw a rectangle around the barcode on the original image
        x, y, w, h = barcode.rect
        cv2.rectangle(image, (x, y), (x + w, y + h), (0, 255, 0), 2)
        
        # Display barcode data and type
        print(f"Detected Barcode Type: {barcode_type}, Data: {barcode_data}")

else:
    print("No barcodes detected in the image.")

# Display the image with detected barcodes
cv2_imshow(image)
