import cv2
import numpy as np

img=cv2.imread('C:/Users/kiranvemula/Downloads/secb.jpg')
img=cv2.resize(img,(0,0),fx=2,fy=2)
hsv=cv2.cvtColor(img,cv2.COLOR_BGR2HLS)
lower=np.array([0,200,0])
upper=np.array([255,255,255])

mask=cv2.inRange(hsv,lower,upper)
cv2.imshow('original',mask)

result=cv2.bitwise_and(hsv,hsv,mask=mask)
result[mask>0]=(0,0,255)
cv2.imshow('red',result)

r1=cv2.bitwise_and(hsv,hsv,mask=mask)
r1[mask>0]=(0,255,0)
cv2.imshow('green',r1)

r2=cv2.bitwise_and(hsv,hsv,mask=mask)
r2[mask>0]=(255,0,0)
cv2.imshow('blue',r2)

cv2.waitKey(0)
cv2.destroyAllWindows()
