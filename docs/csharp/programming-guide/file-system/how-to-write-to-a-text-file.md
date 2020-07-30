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
ms.openlocfilehash: 4108163121d56268b810121ca3ae2b2c1338aeab
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301651"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="88735-104">Metin dosyasına yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="88735-104">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="88735-105">Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="88735-105">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="88735-106">İlk iki örnek, bir <xref:System.IO.File?displayProperty=nameWithType> metin dosyasına bir ve dizesinin her bir öğesini yazmak için sınıfında statik kolay yöntemler kullanır `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="88735-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="88735-107">Örnek 3 ' te, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="88735-107">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="88735-108">Örnekler 1-3 dosyadaki tüm varolan içeriğin üzerine yazılır, ancak örnek 4 ' te varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="88735-108">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="88735-109">Bu örneklerin tümü dosyalara dize değişmez değerleri yazar.</span><span class="sxs-lookup"><span data-stu-id="88735-109">These examples all write string literals to files.</span></span> <span data-ttu-id="88735-110">Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya C# [String enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="88735-110">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88735-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="88735-111">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="88735-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="88735-112">Robust Programming</span></span>  
 <span data-ttu-id="88735-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="88735-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="88735-114">Dosya mevcut ve salt okunur.</span><span class="sxs-lookup"><span data-stu-id="88735-114">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="88735-115">Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="88735-115">The path name may be too long.</span></span>  
  
- <span data-ttu-id="88735-116">Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="88735-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88735-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88735-117">See also</span></span>

- [<span data-ttu-id="88735-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="88735-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88735-119">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="88735-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="88735-120">Örnek: bir koleksiyonu uygulama depolamasına kaydetme</span><span class="sxs-lookup"><span data-stu-id="88735-120">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
