---
title: 'Nasıl yapılır: Bir Defada bir Satır Olarak bir Metin Dosyasını Okuma (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 2ed0069f9313955edc2cc46ecfd395a5f1ac2852
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339741"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a>Nasıl yapılır: Bir Defada bir Satır Olarak bir Metin Dosyasını Okuma (Visual C#)
Bu örnek bir dize kullanarak her seferinde bir satır bir metin dosyasının içeriğini okur `ReadLine` yöntemi `StreamReader` sınıfı. Her metin satırının dizeye depolanan `line` ve ekranında görüntülenir.  
  
## <a name="example"></a>Örnek  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu kopyalayın ve yapıştırın `Main` bir konsol uygulaması yöntemi.  
  
 Değiştir `"c:\test.txt"` gerçek dosya adına sahip.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dosya var olmayabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
