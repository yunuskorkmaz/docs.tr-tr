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
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="c555a-102">Metin dosyası tek satır okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c555a-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="c555a-103">Bu örnek, `ReadLine` `StreamReader` sınıf yöntemini kullanarak bir dize içine bir metin dosyası, bir satır bir satırı içeriğini okur.</span><span class="sxs-lookup"><span data-stu-id="c555a-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="c555a-104">Her metin satırı dize `line` içine depolanır ve ekranda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c555a-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c555a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c555a-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c555a-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c555a-106">Compiling the Code</span></span>  
 <span data-ttu-id="c555a-107">Kodu kopyalayın ve konsol `Main` uygulamasının yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c555a-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="c555a-108">Gerçek `"c:\test.txt"` dosya adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c555a-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c555a-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c555a-109">Robust Programming</span></span>  
 <span data-ttu-id="c555a-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c555a-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c555a-111">Dosya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c555a-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c555a-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c555a-112">.NET Framework Security</span></span>  
 <span data-ttu-id="c555a-113">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="c555a-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="c555a-114">Örneğin, dosya `myFile.cs` C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c555a-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c555a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c555a-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="c555a-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c555a-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c555a-117">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c555a-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
