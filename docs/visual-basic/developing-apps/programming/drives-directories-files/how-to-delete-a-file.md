---
title: 'Nasıl Yapılır: Dosya Silme'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348789"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="bf6ec-102">Nasıl Yapılır: Visual Basic'te Dosya Silme</span><span class="sxs-lookup"><span data-stu-id="bf6ec-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="bf6ec-103">Nesnenin `DeleteFile` `My.Computer.FileSystem` yöntemi bir dosyayı silmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="bf6ec-104">Sunduğu seçenekler arasında: silinen dosyayı Geri **Dönüşüm Kutusu'na**gönderip göndermeme, kullanıcıdan dosyanın silinmesi gerektiğini onaylamasını isteyip istememesi ve kullanıcı işlemi iptal ettiğinde ne yapması gerektiği.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="bf6ec-105">Metin dosyasını silmek için</span><span class="sxs-lookup"><span data-stu-id="bf6ec-105">To delete a text file</span></span>  
  
- <span data-ttu-id="bf6ec-106">Dosyayı `DeleteFile` silmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="bf6ec-107">Aşağıdaki kod, adlı `test.txt`dosyanın nasıl silinecek olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="bf6ec-108">Bir metin dosyasını silmek ve kullanıcıdan dosyanın silinmesi gerektiğini onaylamasını istemek için</span><span class="sxs-lookup"><span data-stu-id="bf6ec-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="bf6ec-109">Dosyayı `DeleteFile` silmek için yöntemi `showUI` `AllDialogs`kullanın, ayar .</span><span class="sxs-lookup"><span data-stu-id="bf6ec-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="bf6ec-110">Aşağıdaki kod, adlandırılmış `test.txt` dosyanın nasıl silineceğini gösterir ve kullanıcının dosyanın silinmesi gerektiğini onaylamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="bf6ec-111">Bir metin dosyasını silmek ve Geri Dönüşüm Kutusu'na göndermek için</span><span class="sxs-lookup"><span data-stu-id="bf6ec-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="bf6ec-112">Parametre `DeleteFile` için belirterek `SendToRecycleBin` dosyayı silmek için yöntemi kullanın. `recycle`</span><span class="sxs-lookup"><span data-stu-id="bf6ec-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="bf6ec-113">Aşağıdaki kod, adlı `test.txt` dosyanın nasıl silinip Geri Dönüşüm **Kutusu'na**gönderilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bf6ec-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="bf6ec-114">Robust Programming</span></span>  

 <span data-ttu-id="bf6ec-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="bf6ec-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="bf6ec-116">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="bf6ec-117">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="bf6ec-118">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="bf6ec-119">Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="bf6ec-120">Dosya kullanımda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="bf6ec-121">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="bf6ec-122">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="bf6ec-123">Kullanıcının dosyayı silme izni yoktur veya dosya salt okunur<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="bf6ec-124">Kullanıcının yeterli izine sahip olmadığı kısmi güven durumu<xref:System.Security.SecurityException>vardır ( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="bf6ec-125">Kullanıcı işlemi iptal etti `onUserCancel` ve `ThrowException` ayarlanır<xref:System.OperationCanceledException>( ).</span><span class="sxs-lookup"><span data-stu-id="bf6ec-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6ec-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf6ec-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="bf6ec-127">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="bf6ec-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
