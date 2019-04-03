---
title: "Nasıl yapılır: Başka bir dizine Visual Basic'te bir dizini kopyalama"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: e45de705eb25d58857239cc549125c524765aaa5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816583"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="2c7a9-102">Nasıl yapılır: Başka bir dizine Visual Basic'te bir dizini kopyalama</span><span class="sxs-lookup"><span data-stu-id="2c7a9-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="2c7a9-103">Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> başka bir dizini kopyalama için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="2c7a9-104">Bu yöntem, dizini ve bunun yanı sıra dizin içeriğini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="2c7a9-105">Hedef dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="2c7a9-106">Hedef konumda aynı adda bir dizin olup olmadığını ve `overwrite` ayarlanır `False`, iki dizin içeriğini birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="2c7a9-107">İşlem sırasında dizini için yeni bir ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="2c7a9-108">Dizindeki dosyaları kopyalarken, özel durumların neden olduğu birleştirme sırasında var olan bir dosya gibi belirli dosya tarafından oluşturulabilir `overwrite` ayarlanır `False`.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="2c7a9-109">Bu tür özel durumlar oluşturulduğunda, tek bir özel durum birleştirilir, `Data` anahtar dosya veya dizin yoludur ve karşılık gelen değer belirli bir özel durum iletisi yer alan girişleri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="2c7a9-110">Bir dizini diğerine kopyalama için</span><span class="sxs-lookup"><span data-stu-id="2c7a9-110">To copy a directory to another directory</span></span>  
  
-   <span data-ttu-id="2c7a9-111">Kullanım `CopyDirectory` yöntemi, kaynak ve hedef dizin adlarını belirleme.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="2c7a9-112">Aşağıdaki örnekte adlı dizine kopyalanır `TestDirectory1` içine `TestDirectory2`, mevcut dosyaların üzerine.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]  
  
     <span data-ttu-id="2c7a9-113">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2c7a9-114">Kod parçacığı Seçici'de bulunur **dosya sistemi - işleme sürücüler, klasörler ve dosyaları**.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="2c7a9-115">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2c7a9-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2c7a9-116">Robust Programming</span></span>  
 <span data-ttu-id="2c7a9-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="2c7a9-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2c7a9-118">Dizin bir iki nokta üst üste (:) veya eğik çizgi içeriyor. belirtilen yeni adı (\ veya /) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-119">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-120">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-121">`destinationDirectoryName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2c7a9-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="2c7a9-122">Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-123">Kaynak dizini kök dizindir (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-124">Birleşik yolu varolan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-125">Kaynak yolu ve hedef yolu aynıdır (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-126">`ShowUI` ayarlanır `UIOption.AllDialogs` ve kullanıcı işlemi iptal ya da bir veya daha fazla dosyalarını şu dizinde kopyalanamaz (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-127">Döngüsel bir işlemdir (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-128">Yol, iki nokta üst üste (:) içeriyor. (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-129">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-130">Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-131">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="2c7a9-132">Bir hedef dosya var, ancak erişilemez (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="2c7a9-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c7a9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c7a9-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="2c7a9-134">Nasıl yapılır: Belirli bir desendeki alt dizinleri bulma</span><span class="sxs-lookup"><span data-stu-id="2c7a9-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="2c7a9-135">Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="2c7a9-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
