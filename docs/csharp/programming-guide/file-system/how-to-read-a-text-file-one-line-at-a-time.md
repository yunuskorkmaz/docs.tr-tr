---
title: Her seferinde bir metin dosyasını okuma-C# programlama kılavuzunda bir satır
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241779"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Bir metin dosyasını tek seferde bir satır okuma (C# Programlama Kılavuzu)
Bu örnek, bir metin dosyasının içeriğini, tek seferde bir satırı, sınıfının yöntemini kullanarak bir dizeye okur `ReadLine` `StreamReader` . Her metin satırı, dizede depolanır `line` ve ekranda görüntülenir.  
  
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
 Kodu kopyalayın ve `Main` konsol uygulamasının yöntemine yapıştırın.  
  
 `"c:\test.txt"`Gerçek dosya adıyla değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya mevcut olmayabilir.  
  
## <a name="net-security"></a>.NET güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
