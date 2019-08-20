---
title: 'Nasıl yapılır: Bir Defada bir Satır Olarak bir Metin Dosyasını Okuma (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 75274d93ee29feb5f79dfc29c24109f25fd98a5c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589966"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="8a282-102">Nasıl yapılır: Bir Defada bir Satır Olarak bir Metin Dosyasını Okuma (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="8a282-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="8a282-103">Bu örnek, bir metin dosyasının içeriğini, tek seferde bir satırı, `ReadLine` `StreamReader` sınıfının yöntemini kullanarak bir dizeye okur.</span><span class="sxs-lookup"><span data-stu-id="8a282-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="8a282-104">Her metin satırı, dizede `line` depolanır ve ekranda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8a282-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a282-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a282-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a282-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8a282-106">Compiling the Code</span></span>  
 <span data-ttu-id="8a282-107">Kodu kopyalayın ve konsol uygulamasının `Main` yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="8a282-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="8a282-108">Gerçek `"c:\test.txt"` dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8a282-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8a282-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8a282-109">Robust Programming</span></span>  
 <span data-ttu-id="8a282-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8a282-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8a282-111">Dosya mevcut olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8a282-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8a282-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8a282-112">.NET Framework Security</span></span>  
 <span data-ttu-id="8a282-113">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="8a282-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="8a282-114">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8a282-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a282-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a282-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="8a282-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8a282-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8a282-117">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8a282-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
