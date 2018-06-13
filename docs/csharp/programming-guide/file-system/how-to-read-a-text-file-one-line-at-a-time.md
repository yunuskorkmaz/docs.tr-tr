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
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="c44b9-102">Nasıl yapılır: Bir Defada bir Satır Olarak bir Metin Dosyasını Okuma (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="c44b9-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="c44b9-103">Bu örnek bir dize kullanarak her seferinde bir satır bir metin dosyasının içeriğini okur `ReadLine` yöntemi `StreamReader` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c44b9-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="c44b9-104">Her metin satırının dizeye depolanan `line` ve ekranında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c44b9-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c44b9-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c44b9-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c44b9-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c44b9-106">Compiling the Code</span></span>  
 <span data-ttu-id="c44b9-107">Kodu kopyalayın ve yapıştırın `Main` bir konsol uygulaması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c44b9-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="c44b9-108">Değiştir `"c:\test.txt"` gerçek dosya adına sahip.</span><span class="sxs-lookup"><span data-stu-id="c44b9-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c44b9-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c44b9-109">Robust Programming</span></span>  
 <span data-ttu-id="c44b9-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c44b9-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c44b9-111">Dosya var olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c44b9-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c44b9-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c44b9-112">.NET Framework Security</span></span>  
 <span data-ttu-id="c44b9-113">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="c44b9-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="c44b9-114">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c44b9-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44b9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c44b9-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="c44b9-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c44b9-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c44b9-117">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c44b9-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
