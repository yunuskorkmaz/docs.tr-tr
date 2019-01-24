---
title: "Nasıl yapılır: Visual Basic'te dosya silme"
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 2222c06b71b3063c848495aec52fd4acf0674073
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520626"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="4b2d9-102">Nasıl yapılır: Visual Basic'te dosya silme</span><span class="sxs-lookup"><span data-stu-id="4b2d9-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="4b2d9-103">`DeleteFile` Yöntemi `My.Computer.FileSystem` nesnesinin bir dosyayı silmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="4b2d9-104">Sunduğu seçenekler arasında: silinen dosyanın gönderilip gönderilmeyeceğini **geri dönüşüm kutusu**dosyasının silinip silinmediğini doğrulamak için kullanıcıya sor verilip verilmeyeceğini ve kullanıcı işlemi iptal ne yapılacağını.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="4b2d9-105">Bir metin dosyası silinemedi</span><span class="sxs-lookup"><span data-stu-id="4b2d9-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="4b2d9-106">Kullanım `DeleteFile` dosyayı silmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="4b2d9-107">Aşağıdaki kodu adlı dosyayı nasıl silineceği `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="4b2d9-108">Bir metin dosyası silip dosyasının silinip silinmediğini doğrulamak için kullanıcıya sor</span><span class="sxs-lookup"><span data-stu-id="4b2d9-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="4b2d9-109">Kullanım `DeleteFile` ayarlama, dosyayı silmek için yöntemi `showUI` için `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="4b2d9-110">Aşağıdaki kodu adlı dosyayı nasıl silineceği `test.txt` ve dosya silinip silinmediğini doğrulayın izin verin.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="4b2d9-111">Bir metin dosyasını silin ve Geri Dönüşüm Kutusu'na göndermek için</span><span class="sxs-lookup"><span data-stu-id="4b2d9-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="4b2d9-112">Kullanım `DeleteFile` dosyayı silmek için yöntemi belirtme `SendToRecycleBin` için `recycle` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="4b2d9-113">Aşağıdaki kodu adlı dosyayı nasıl silineceği `test.txt` ve göndermeden **Geri Dönüşüm Kutusu'nu**.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4b2d9-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4b2d9-114">Robust Programming</span></span>  
 <span data-ttu-id="4b2d9-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="4b2d9-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="4b2d9-116">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-117">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-118">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-119">Yolda bir dosya veya klasör adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-120">Dosyanın kullanımda olup (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-121">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-122">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-123">Kullanıcının dosyayı silme izni yok veya dosya salt okunur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-124">Hangi kullanıcı olmayan yeterli izinlere sahip bir kısmi güven durum var (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="4b2d9-125">Kullanıcı işlemi iptal edildi ve `onUserCancel` ayarlanır `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="4b2d9-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b2d9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b2d9-126">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="4b2d9-127">Nasıl yapılır: Bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="4b2d9-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
