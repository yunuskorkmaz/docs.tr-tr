---
title: "Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 9b6e095d061619cf9d2e2d87a7247cbdbc51cbe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588590"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="77f23-102">Nasıl Yapılır: Visual Basic'te bir Dizini Diğerine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="77f23-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="77f23-103">Kullanım <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> yöntemi bir dizin başka bir dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="77f23-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="77f23-104">Bu yöntem, dizini ve bunun yanı sıra dizin içeriğini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="77f23-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="77f23-105">Hedef dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77f23-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="77f23-106">Hedef konumda aynı adı taşıyan bir dizin olup olmadığını ve `overwrite` ayarlanır `False`, iki dizin içeriğini birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="77f23-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="77f23-107">İşlem sırasında dizin için yeni bir ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77f23-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="77f23-108">Bir dizindeki dosya kopyalarken, özel durumlar neden olduğu birleştirme sırasında var olan bir dosya gibi belirli dosya tarafından durum oluşturulabilir `overwrite` ayarlanır `False`.</span><span class="sxs-lookup"><span data-stu-id="77f23-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="77f23-109">Bu tür özel durumlar, tek bir özel durum birleştirilir, `Data` özelliği dosya veya dizin yolunu anahtarıdır ve belirli özel durum iletisi içinde karşılık gelen değerle yer alan girişleri içerir.</span><span class="sxs-lookup"><span data-stu-id="77f23-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="77f23-110">Bir dizini diğerine kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="77f23-110">To copy a directory to another directory</span></span>  
  
-   <span data-ttu-id="77f23-111">Kullanım `CopyDirectory` yöntemi, kaynak ve hedef dizin adlarını belirtme.</span><span class="sxs-lookup"><span data-stu-id="77f23-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="77f23-112">Aşağıdaki örnek adlı dizine kopyalar `TestDirectory1` içine `TestDirectory2`, var olan dosyaların üzerine yazılması.</span><span class="sxs-lookup"><span data-stu-id="77f23-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     <span data-ttu-id="77f23-113">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77f23-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="77f23-114">Kod parçacığı Seçici bulunur **dosya sistemi - işleme sürücüleri, klasörleri ve dosyaları**.</span><span class="sxs-lookup"><span data-stu-id="77f23-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="77f23-115">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="77f23-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="77f23-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="77f23-116">Robust Programming</span></span>  
 <span data-ttu-id="77f23-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="77f23-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="77f23-118">İki nokta üst üste (:) veya eğik çizgi dizini içeren için belirtilen yeni adı (\ veya /) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="77f23-119">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="77f23-120">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="77f23-121">`destinationDirectoryName` olan `Nothing` ya da boş bir dize (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="77f23-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="77f23-122">Kaynak dizin yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="77f23-123">Kaynak dizini olan bir kök dizini (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="77f23-124">Birleşik yolu varolan bir dosyaya işaret (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="77f23-125">Kaynak yolu ve hedef yolu aynıdır (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="77f23-126">`ShowUI` ayarlanmış `UIOption.AllDialogs` ve kullanıcı işlemi iptal ya da dizindeki bir veya daha fazla dosya kopyalanamıyor (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="77f23-127">Döngüsel bir işlemdir (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
-   <span data-ttu-id="77f23-128">Yol, iki nokta üst üste (:) içeriyor. (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="77f23-129">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="77f23-130">Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="77f23-131">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="77f23-132">Bir hedef dosya varsa, ancak erişilemiyor (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="77f23-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f23-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77f23-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>  
 [<span data-ttu-id="77f23-134">Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="77f23-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [<span data-ttu-id="77f23-135">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="77f23-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
