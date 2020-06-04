---
title: 'Nasıl yapılır: Dosya Yollarını Ayrıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: eb7714a8594c0bce344eb2e48ebc5053dc3bfbb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359948"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="a1d54-102">Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a1d54-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="a1d54-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem>Nesnesi, dosya yollarını ayrıştırırken bazı yararlı yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="a1d54-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="a1d54-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>Yöntemi iki yol alır ve düzgün şekilde biçimlendirilen Birleşik yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1d54-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="a1d54-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A>Yöntemi, belirtilen yolun üst öğesinin mutlak yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1d54-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="a1d54-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>Yöntemi, <xref:System.IO.FileInfo> dosyanın adı ve yolu gibi özelliklerinin belirlenmesi için sorgulanabilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1d54-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="a1d54-107">Dosya adı uzantısına bağlı olarak dosyanın içeriğiyle ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="a1d54-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="a1d54-108">Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a1d54-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="a1d54-109">Bir dosyanın adını ve yolunu belirleme</span><span class="sxs-lookup"><span data-stu-id="a1d54-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="a1d54-110"><xref:System.IO.FileInfo.DirectoryName%2A> <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> Bir dosyanın adını ve yolunu öğrenmek için nesnesinin ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1d54-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="a1d54-111">Bu örnek, adı ve yolu belirler ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1d54-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="a1d54-112">Tam yolu oluşturmak üzere bir dosyanın adını ve dizinini birleştirmek için</span><span class="sxs-lookup"><span data-stu-id="a1d54-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="a1d54-113">`CombinePath`Dizinini, dizin ve adı sağlayarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1d54-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="a1d54-114">Bu örnek, dizeleri alır `folderPath` ve `fileName` Önceki örnekte oluşturulur, bunları birleştirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1d54-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="a1d54-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d54-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="a1d54-116">Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="a1d54-116">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
