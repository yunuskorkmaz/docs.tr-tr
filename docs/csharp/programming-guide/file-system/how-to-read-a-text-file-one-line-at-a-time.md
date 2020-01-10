---
title: Bir metin dosyasını, zaman C# programlama kılavuzunda bir satır olarak okuma
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: a6af48cdacd836465d776a3fd4e1d17aa0298b77
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635346"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="4a127-102">Bir metin dosyasını tek seferde bir satır okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4a127-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="4a127-103">Bu örnek, bir metin dosyasının içeriğini, bir kerede bir satırı, `StreamReader` sınıfının `ReadLine` yöntemini kullanarak bir dizeye okur.</span><span class="sxs-lookup"><span data-stu-id="4a127-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="4a127-104">Her metin satırı `line` dize içinde depolanır ve ekranda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4a127-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a127-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a127-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4a127-106">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="4a127-106">Compiling the Code</span></span>  
 <span data-ttu-id="4a127-107">Kodu kopyalayın ve bir konsol uygulamasının `Main` yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="4a127-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="4a127-108">`"c:\test.txt"` gerçek dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4a127-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4a127-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4a127-109">Robust Programming</span></span>  
 <span data-ttu-id="4a127-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="4a127-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4a127-111">Dosya mevcut olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4a127-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4a127-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4a127-112">.NET Framework Security</span></span>  
 <span data-ttu-id="4a127-113">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="4a127-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="4a127-114">Örneğin, `myFile.cs` dosyası bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4a127-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a127-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a127-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4a127-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4a127-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4a127-117">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4a127-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
