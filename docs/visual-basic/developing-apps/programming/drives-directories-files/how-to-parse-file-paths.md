---
title: "Nasıl yapılır: Visual Basic'te dosya yollarını ayrıştırma"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 2b31dedbdd33ddfb3c15863a45b93148fd722faa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707758"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="1140c-102">Nasıl yapılır: Visual Basic'te dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="1140c-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="1140c-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> Nesnesi, dosya yolları ayrıştırılırken çeşitli kullanışlı yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="1140c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="1140c-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Yöntemi iki yolu alır ve düzgün şekilde biçimlendirilmiş bir birleşik yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1140c-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="1140c-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Yöntemi üst öğesinin sağlanan yol mutlak yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1140c-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="1140c-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Yöntemi döndürür bir <xref:System.IO.FileInfo> adı ve yolu gibi dosya özelliklerini belirlemek için sorgulanabilir bir nesne.</span><span class="sxs-lookup"><span data-stu-id="1140c-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="1140c-107">Dosya adı uzantısına göre dosyasının içeriği hakkında kararlar yapmayın.</span><span class="sxs-lookup"><span data-stu-id="1140c-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="1140c-108">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1140c-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="1140c-109">Bir dosyanın adı ve yolu belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1140c-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="1140c-110">Kullanım <xref:System.IO.FileInfo.DirectoryName%2A> ve <xref:System.IO.FileInfo.Name%2A> özelliklerini <xref:System.IO.FileInfo> bir dosyanın adı ve yolu belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="1140c-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="1140c-111">Bu örnek adını ve yolunu belirler ve bunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1140c-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="1140c-112">Bir dosyanın adı ve tam yolunu oluşturulacağı dizin birleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1140c-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="1140c-113">Kullanım `CombinePath` yöntemi, dizin ve ad sağlama.</span><span class="sxs-lookup"><span data-stu-id="1140c-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="1140c-114">Bu örnek, dizeleri alan `folderPath` ve `fileName` önceki örnekte oluşturulan, bunları bir araya getirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1140c-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1140c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1140c-115">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="1140c-116">Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="1140c-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
