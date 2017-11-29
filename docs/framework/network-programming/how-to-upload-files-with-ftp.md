---
title: "Nasıl yapılır: FTP dosyaları karşıya yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 08002bf223d96d49cffb67ec744659747fa49e26
ms.sourcegitcommit: 32f5e1db8755ed7dfac0b4ec764fa809e5a7548c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2017
---
# <a name="how-to-upload-files-with-ftp"></a>Nasıl yapılır: FTP dosyaları karşıya yükleme
Bu örnek, bir FTP sunucusuna bir dosyayı karşıya gösterilmektedir.  
  
## <a name="example"></a>Örnek  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");  
            request.Method = WebRequestMethods.Ftp.UploadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            // Copy the contents of the file to the request stream.  
            StreamReader sourceStream = new StreamReader("testfile.txt");  
            byte [] fileContents = Encoding.UTF8.GetBytes(sourceStream.ReadToEnd());  
            sourceStream.Close();  
            request.ContentLength = fileContents.Length;  
  
            Stream requestStream = request.GetRequestStream();  
            requestStream.Write(fileContents, 0, fileContents.Length);  
            requestStream.Close();  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Console.WriteLine("Upload File Complete, status {0}", response.StatusDescription);  
  
            response.Close();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular **System.Net** ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği
