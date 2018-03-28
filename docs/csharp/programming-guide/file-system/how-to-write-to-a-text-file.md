---
title: 'Nasıl yapılır: Bir Metin Dosyasına Yazma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fa6de76e3981e0f05b5b192045043422a8a912aa
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="ca7d5-102">Nasıl yapılır: Bir Metin Dosyasına Yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ca7d5-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="ca7d5-103">Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="ca7d5-104">İlk iki örnek statik kullanışlı yöntemler kullanın <xref:System.IO.File?displayProperty=nameWithType> herhangi her öğeye yazmak için sınıf `IEnumerable<string>` ve bir metin dosyasına bir dize.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="ca7d5-105">Örnek 3 veya dosyaya yazmak gibi her satır ayrı ayrı işlemek varsa bir dosyaya metin eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="ca7d5-106">Örnek 1-3 dosyasındaki tüm var olan içeriğin üzerine ancak örnek 4 varolan bir dosyaya metin ekleneceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="ca7d5-107">Tüm bu örneklerde dize değişmez değerleri dosyalara yazma.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-107">These examples all write string literals to files.</span></span> <span data-ttu-id="ca7d5-108">Bir dosyaya yazılır Metin biçimlendirmek istediğiniz kullanırsanız <xref:System.String.Format%2A> yöntemi veya C# [dize ilişkilendirme](../../../csharp/language-reference/tokens/interpolated.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca7d5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca7d5-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ca7d5-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ca7d5-110">Robust Programming</span></span>  
 <span data-ttu-id="ca7d5-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ca7d5-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ca7d5-112">Dosya mevcut ve salt okunur.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-112">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="ca7d5-113">Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-113">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="ca7d5-114">Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7d5-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-115">See Also</span></span>  
 [<span data-ttu-id="ca7d5-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ca7d5-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ca7d5-117">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ca7d5-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="ca7d5-118">Örnek: bir koleksiyon uygulama depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ca7d5-118">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
