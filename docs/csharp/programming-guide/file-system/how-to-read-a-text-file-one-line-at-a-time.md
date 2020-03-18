---
title: Metin dosyası tek satır okuma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: e4a9ba2da2548991f442c2f5ab09d39243137875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167526"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Metin dosyası tek satır okuma (C# Programlama Kılavuzu)
Bu örnek, `ReadLine` `StreamReader` sınıf yöntemini kullanarak bir dize içine bir metin dosyası, bir satır bir satırı içeriğini okur. Her metin satırı dize `line` içine depolanır ve ekranda görüntülenir.  
  
## <a name="example"></a>Örnek  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu kopyalayın ve konsol `Main` uygulamasının yöntemine yapıştırın.  
  
 Gerçek `"c:\test.txt"` dosya adı ile değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya olmayabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya `myFile.cs` C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
