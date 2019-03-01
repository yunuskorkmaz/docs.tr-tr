---
title: "Nasıl yapılır: Visual Basic'te dosya yollarını ayrıştırma"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 4e3cfca9a84ef56ceb9ac0785af039f9b24603e2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971994"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="ab1ad-102">Nasıl yapılır: Visual Basic'te dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="ab1ad-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="ab1ad-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> Nesnesi, dosya yolları ayrıştırılırken çeşitli kullanışlı yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="ab1ad-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> Yöntemi iki yolu alır ve düzgün şekilde biçimlendirilmiş bir birleşik yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="ab1ad-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> Yöntemi üst öğesinin sağlanan yol mutlak yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="ab1ad-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> Yöntemi döndürür bir <xref:System.IO.FileInfo> adı ve yolu gibi dosya özelliklerini belirlemek için sorgulanabilir bir nesne.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="ab1ad-107">Dosya adı uzantısına göre dosyasının içeriği hakkında kararlar yapmayın.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="ab1ad-108">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="ab1ad-109">Bir dosyanın adı ve yolu belirlemek için</span><span class="sxs-lookup"><span data-stu-id="ab1ad-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="ab1ad-110">Kullanım <xref:System.IO.FileInfo.DirectoryName%2A> ve <xref:System.IO.FileInfo.Name%2A> özelliklerini <xref:System.IO.FileInfo> bir dosyanın adı ve yolu belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="ab1ad-111">Bu örnek adını ve yolunu belirler ve bunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="ab1ad-112">Bir dosyanın adı ve tam yolunu oluşturulacağı dizin birleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ab1ad-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="ab1ad-113">Kullanım `CombinePath` yöntemi, dizin ve ad sağlama.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="ab1ad-114">Bu örnek, dizeleri alan `folderPath` ve `fileName` önceki örnekte oluşturulan, bunları bir araya getirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="ab1ad-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab1ad-115">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="ab1ad-116">Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="ab1ad-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
