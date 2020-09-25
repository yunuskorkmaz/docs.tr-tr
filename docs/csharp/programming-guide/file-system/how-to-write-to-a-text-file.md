---
title: Metin dosyasına yazma-C# Programlama Kılavuzu
description: C# ile bir metin dosyası yazmayı öğrenin. Çeşitli kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 48739852cd1730d71c3b20ae6a9394b57785faa6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170408"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="a8558-104">Metin dosyasına yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a8558-104">How to write to a text file (C# Programming Guide)</span></span>

<span data-ttu-id="a8558-105">Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a8558-105">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="a8558-106">İlk iki örnek, bir <xref:System.IO.File?displayProperty=nameWithType> metin dosyasına bir ve dizesinin her bir öğesini yazmak için sınıfında statik kolay yöntemler kullanır `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="a8558-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="a8558-107">Örnek 3 ' te, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a8558-107">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="a8558-108">Örnekler 1-3 dosyadaki tüm varolan içeriğin üzerine yazılır, ancak örnek 4 ' te varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a8558-108">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="a8558-109">Bu örneklerin tümü dosyalara dize değişmez değerleri yazar.</span><span class="sxs-lookup"><span data-stu-id="a8558-109">These examples all write string literals to files.</span></span> <span data-ttu-id="a8558-110">Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya C# [String enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8558-110">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8558-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8558-111">Example</span></span>  

 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a8558-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a8558-112">Robust Programming</span></span>  

 <span data-ttu-id="a8558-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="a8558-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a8558-114">Dosya mevcut ve salt okunur.</span><span class="sxs-lookup"><span data-stu-id="a8558-114">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="a8558-115">Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8558-115">The path name may be too long.</span></span>  
  
- <span data-ttu-id="a8558-116">Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8558-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8558-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8558-117">See also</span></span>

- [<span data-ttu-id="a8558-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8558-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a8558-119">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a8558-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="a8558-120">Örnek: bir koleksiyonu uygulama depolamasına kaydetme</span><span class="sxs-lookup"><span data-stu-id="a8558-120">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
