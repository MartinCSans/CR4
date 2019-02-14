#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Wed Feb 13 20:34:13 2019
Reference: https://github.com/bozhu/RC4-Python/blob/master/rc4.py
@author: martin
"""

import fileinput 

def ChangeToInteger(key):
    NewKey = []
    
    NewKey = [ord(i)for i in key]
      
    return NewKey
    
def KSA(key):
    S = []
    keylength = len(key)
    j = 0
    
    for i in range(256):
        S.append(i)
    
    for i in range(256):
        j = (j + S[i] + key[i % keylength]) % 256
        S[i], S[j] = S[j], S[i]
        
    
    return S


def PRGA(Strm):
    i = 0
    j = 0
    
    
    while True:
        i = (i + 1) % 256
        j = (j + Strm[i]) % 256
        Strm[i], Strm[j] = Strm[j], Strm[i]
        K = Strm[(Strm[i] + Strm[j]) % 256]
        yield K
        


def Xor(text,Stream):
    total = ''
 
    
    for j in text:
        d = (ord(j) ^ Stream.__next__())
        total += format(d,'02X')
       
        
    print(total)
    

def main():
    
    file_input = fileinput.input()
    key = file_input[0]
    key = key.replace('\n','')
    
    NewKey = ChangeToInteger(key)
    
    
    Strm = KSA(NewKey)
    
    Stream = PRGA(Strm)
    
    
    text = file_input[1]
    text = text.replace('\n','')
    
    Xor(text,Stream)
    
   

if __name__ == "__main__":
	main()
