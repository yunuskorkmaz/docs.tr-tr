---
title: 'Nasıl yapılır: Metin dosyasına yazma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: d08fe23f2dbfe46c0a58084b05610dfe7db3dda9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589924"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="6f3b1-102">Nasıl yapılır: Metin dosyasına yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6f3b1-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="6f3b1-103">Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="6f3b1-104">İlk iki örnek, bir metin dosyasına bir <xref:System.IO.File?displayProperty=nameWithType> `IEnumerable<string>` ve dizesinin her bir öğesini yazmak için sınıfında statik kolay yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="6f3b1-105">Örnek 3 ' te, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="6f3b1-106">Örnekler 1-3 dosyadaki tüm varolan içeriğin üzerine yazılır, ancak örnek 4 ' te varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="6f3b1-107">Bu örneklerin tümü dosyalara dize değişmez değerleri yazar.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-107">These examples all write string literals to files.</span></span> <span data-ttu-id="6f3b1-108">Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya [](../../language-reference/tokens/interpolated.md) C# dize ilişkilendirme özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f3b1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f3b1-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6f3b1-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6f3b1-110">Robust Programming</span></span>  
 <span data-ttu-id="6f3b1-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="6f3b1-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6f3b1-112">Dosya mevcut ve salt okunur.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="6f3b1-113">Yol adı çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="6f3b1-114">Disk dolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3b1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f3b1-115">See also</span></span>

- [<span data-ttu-id="6f3b1-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6f3b1-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6f3b1-117">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6f3b1-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="6f3b1-118">Örnekli Bir koleksiyonu uygulama depolamasına kaydetme</span><span class="sxs-lookup"><span data-stu-id="6f3b1-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
