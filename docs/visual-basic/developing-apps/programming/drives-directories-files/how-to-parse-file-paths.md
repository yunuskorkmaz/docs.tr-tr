---
title: 'Nasıl Yapılır: Dosya Yollarını Ayrıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 6a959994be3a57795dc9f7e3447fa54bf075d3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335345"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="8041c-102">Nasıl Yapılır: Visual Basic'te Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="8041c-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="8041c-103">Nesne, <xref:Microsoft.VisualBasic.FileIO.FileSystem> dosya yollarını ayrışdırırken bir dizi yararlı yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="8041c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="8041c-104">Yöntem <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> iki yol alır ve düzgün biçimlendirilmiş bir birleşik yol döndürür.</span><span class="sxs-lookup"><span data-stu-id="8041c-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="8041c-105">Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> sağlanan yolun üst yolunun mutlak yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8041c-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="8041c-106">Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> dosyanın adı ve yolu gibi özelliklerini belirlemek için sorgulanabilecek bir <xref:System.IO.FileInfo> nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="8041c-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="8041c-107">Dosya adı uzantısına dayalı olarak dosyanın içeriği hakkında karar verme.</span><span class="sxs-lookup"><span data-stu-id="8041c-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="8041c-108">Örneğin, Form1.vb dosyası Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8041c-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="8041c-109">Bir dosyanın adını ve yolunu belirlemek için</span><span class="sxs-lookup"><span data-stu-id="8041c-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="8041c-110">Dosyanın <xref:System.IO.FileInfo.DirectoryName%2A> <xref:System.IO.FileInfo.Name%2A> adını ve <xref:System.IO.FileInfo> yolunu belirlemek için nesnenin özelliklerini ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8041c-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="8041c-111">Bu örnek, adı ve yolu belirler ve bunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8041c-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="8041c-112">Tam yol oluşturmak için bir dosyanın adını ve dizinini birleştirmek için</span><span class="sxs-lookup"><span data-stu-id="8041c-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="8041c-113">Dizini `CombinePath` ve adı sağlayarak yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8041c-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="8041c-114">Bu örnek, dizeleri alır `folderPath` ve `fileName` önceki örnekte oluşturulan, bunları birleştirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8041c-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="8041c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8041c-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="8041c-116">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="8041c-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
