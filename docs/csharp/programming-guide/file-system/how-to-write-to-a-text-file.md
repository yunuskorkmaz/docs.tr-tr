---
title: Metin dosyasına nasıl yazılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712253"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="25f49-102">Metin dosyasına nasıl yazılır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="25f49-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="25f49-103">Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="25f49-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="25f49-104">İlk iki örnek, herhangi bir <xref:System.IO.File?displayProperty=nameWithType> metin dosyasına herhangi `IEnumerable<string>` bir ve bir dize her öğeyi yazmak için sınıfta statik kolaylık yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="25f49-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="25f49-105">Örnek 3, dosyaya yazarken her satırı ayrı ayrı işlemeniz gerektiğinde dosyaya nasıl metin ekleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="25f49-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="25f49-106">Örnekler 1-3 dosyadaki varolan tüm içeriğin üzerine yazılır, ancak örnek 4, varolan bir dosyaya metin ekini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25f49-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="25f49-107">Bu örneklerin tümü dosyalara dize edebi yazılır.</span><span class="sxs-lookup"><span data-stu-id="25f49-107">These examples all write string literals to files.</span></span> <span data-ttu-id="25f49-108">Bir dosyaya yazılan metni biçimlendirmek <xref:System.String.Format%2A> istiyorsanız, yöntem veya C# [dize enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25f49-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25f49-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="25f49-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="25f49-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="25f49-110">Robust Programming</span></span>  
 <span data-ttu-id="25f49-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="25f49-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="25f49-112">Dosya mevcut ve salt okunur.</span><span class="sxs-lookup"><span data-stu-id="25f49-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="25f49-113">Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="25f49-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="25f49-114">Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="25f49-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f49-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25f49-115">See also</span></span>

- [<span data-ttu-id="25f49-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="25f49-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="25f49-117">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="25f49-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="25f49-118">Örnek: Koleksiyonu Uygulama Depolamasına Kaydet</span><span class="sxs-lookup"><span data-stu-id="25f49-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
