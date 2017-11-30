---
title: "Nasıl yapılır: Bir Metin Dosyasına Yazma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="043c1-102">Nasıl yapılır: Bir Metin Dosyasına Yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="043c1-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="043c1-103">Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="043c1-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="043c1-104">İlk iki örnek statik kullanışlı yöntemler kullanın <xref:System.IO.File?displayProperty=nameWithType> herhangi IEnumerable her öğeye yazmak için sınıf\<dize > ve bir metin dosyasına bir dize.</span><span class="sxs-lookup"><span data-stu-id="043c1-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="043c1-105">Örnek 3 veya dosyaya yazmak gibi her satır ayrı ayrı işlemek varsa bir dosyaya metin eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="043c1-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="043c1-106">Örnek 1-3 dosyasındaki tüm var olan içeriğin üzerine ancak örnek 4 varolan bir dosyaya metin ekleneceği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="043c1-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="043c1-107">Tüm bu örneklerde dize değişmez değerleri dosyalara yazmasını ancak büyük olasılıkla kullanmak istersiniz <xref:System.String.Format%2A> ile veya olmadan doldurma ve benzeri bir alanda farklı türlerdeki değerleri sağa veya sola hizalı yazmak için birçok denetimleri olan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043c1-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="043c1-108">Ayrıca C# kullanabilirsiniz [dize ilişkilendirme](../../../csharp/language-reference/keywords/interpolated-strings.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="043c1-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="043c1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="043c1-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 <span data-ttu-id="043c1-110">Tüm bu örneklerde dize değişmez değerleri dosyalara yazmasını ancak büyük olasılıkla kullanmak istersiniz <xref:System.String.Format%2A> ile veya olmadan doldurma ve benzeri bir alanda farklı türlerdeki değerleri sağa veya sola hizalı yazmak için birçok denetimleri olan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043c1-110">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="043c1-111">Ayrıca C# kullanabilirsiniz [dize ilişkilendirme](../../../csharp/language-reference/keywords/interpolated-strings.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="043c1-111">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="043c1-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="043c1-112">Robust Programming</span></span>  
 <span data-ttu-id="043c1-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="043c1-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="043c1-114">Dosya mevcut ve salt okunur.</span><span class="sxs-lookup"><span data-stu-id="043c1-114">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="043c1-115">Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="043c1-115">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="043c1-116">Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="043c1-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043c1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="043c1-117">See Also</span></span>  
 [<span data-ttu-id="043c1-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="043c1-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="043c1-119">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="043c1-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="043c1-120">Örnek: bir koleksiyon uygulama depoya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="043c1-120">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
