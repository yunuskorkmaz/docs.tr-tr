---
description: ': Nasıl yapılır: Visual Basic dosya yollarını ayrıştırma hakkında daha fazla bilgi edinin'
title: 'Nasıl yapılır: Dosya Yollarını Ayrıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: dff423679324974d64c613a292c253d99d668c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797503"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="84f69-103">Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="84f69-103">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="84f69-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem>Nesnesi, dosya yollarını ayrıştırırken bazı yararlı yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="84f69-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="84f69-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>Yöntemi iki yol alır ve düzgün şekilde biçimlendirilen Birleşik yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="84f69-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="84f69-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A>Yöntemi, belirtilen yolun üst öğesinin mutlak yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="84f69-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="84f69-107"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>Yöntemi, <xref:System.IO.FileInfo> dosyanın adı ve yolu gibi özelliklerinin belirlenmesi için sorgulanabilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="84f69-107">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="84f69-108">Dosya adı uzantısına bağlı olarak dosyanın içeriğiyle ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="84f69-108">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="84f69-109">Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="84f69-109">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="84f69-110">Bir dosyanın adını ve yolunu belirleme</span><span class="sxs-lookup"><span data-stu-id="84f69-110">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="84f69-111"><xref:System.IO.FileInfo.DirectoryName%2A> <xref:System.IO.FileInfo.Name%2A> <xref:System.IO.FileInfo> Bir dosyanın adını ve yolunu öğrenmek için nesnesinin ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="84f69-111">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="84f69-112">Bu örnek, adı ve yolu belirler ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84f69-112">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="84f69-113">Tam yolu oluşturmak üzere bir dosyanın adını ve dizinini birleştirmek için</span><span class="sxs-lookup"><span data-stu-id="84f69-113">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="84f69-114">`CombinePath`Dizinini, dizin ve adı sağlayarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="84f69-114">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="84f69-115">Bu örnek, dizeleri alır `folderPath` ve `fileName` Önceki örnekte oluşturulur, bunları birleştirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84f69-115">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="84f69-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84f69-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="84f69-117">Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="84f69-117">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
