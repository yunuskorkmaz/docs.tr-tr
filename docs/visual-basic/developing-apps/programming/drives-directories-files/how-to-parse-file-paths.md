---
title: "Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 7479f368558a8a8a07c1e6ed588bdfef21a0b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585950"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="12ca7-102">Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="12ca7-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="12ca7-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> Nesnesi, dosya yolları ayrıştırılırken çeşitli kullanışlı yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="12ca7-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="12ca7-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Yöntemi iki yolu alır ve düzgün şekilde biçimlendirilmiş bir birleşik yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="12ca7-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="12ca7-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Yöntemi döndürür ve sağlanan yolun üst mutlak yolu.</span><span class="sxs-lookup"><span data-stu-id="12ca7-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="12ca7-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Yöntemi döndürür bir <xref:System.IO.FileInfo> adı ve yolu gibi dosya özelliklerini belirlemek için sorgulanan nesne.</span><span class="sxs-lookup"><span data-stu-id="12ca7-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="12ca7-107">Dosya adı uzantısına göre dosyasının içeriği hakkında kararlar yapmayın.</span><span class="sxs-lookup"><span data-stu-id="12ca7-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="12ca7-108">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="12ca7-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="12ca7-109">Bir dosyanın adı ve yolu belirlemek için</span><span class="sxs-lookup"><span data-stu-id="12ca7-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="12ca7-110">Kullanım <xref:System.IO.FileInfo.DirectoryName%2A> ve <xref:System.IO.FileInfo.Name%2A> özelliklerini <xref:System.IO.FileInfo> bir dosyanın adı ve yolu belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="12ca7-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="12ca7-111">Bu örnek adını ve yolunu belirler ve bunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12ca7-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="12ca7-112">Bir dosyanın adı ve tam yolu oluşturmak için dizin birleştirmek için</span><span class="sxs-lookup"><span data-stu-id="12ca7-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="12ca7-113">Kullanım `CombinePath` yöntemi, ad ve dizin sağlama.</span><span class="sxs-lookup"><span data-stu-id="12ca7-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="12ca7-114">Bu örnek dizeyi alır `folderPath` ve `fileName` önceki örnekte oluşturulan, bunları birleştirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12ca7-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="12ca7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12ca7-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [<span data-ttu-id="12ca7-116">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="12ca7-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
