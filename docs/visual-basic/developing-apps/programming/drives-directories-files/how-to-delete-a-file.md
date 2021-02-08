---
description: 'Hakkında daha fazla bilgi için: nasıl yapılır: Visual Basic dosya silme'
title: 'Nasıl yapılır: Dosya Silme'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 49bfe2e4a0d9114e2f653ae14dab303e35e2dfeb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797581"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="68a60-103">Nasıl Yapılır: Visual Basic'te Dosya Silme</span><span class="sxs-lookup"><span data-stu-id="68a60-103">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="68a60-104">`DeleteFile` `My.Computer.FileSystem` Nesnesinin yöntemi bir dosyayı silmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68a60-104">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="68a60-105">Bunun sunduğu seçenekler arasında: Silinen dosyanın **geri dönüşüm kutusu**'na gönderilmesi, kullanıcıdan dosyanın silinip silinmeyeceğini ve Kullanıcı işlemi iptal ettiğinde ne yapılacağını onaylamasını isteyip istemediğini sorar.</span><span class="sxs-lookup"><span data-stu-id="68a60-105">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="68a60-106">Bir metin dosyasını silmek için</span><span class="sxs-lookup"><span data-stu-id="68a60-106">To delete a text file</span></span>  
  
- <span data-ttu-id="68a60-107">`DeleteFile`Dosyayı silmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="68a60-107">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="68a60-108">Aşağıdaki kod, adlı dosyanın nasıl silineceğini gösterir `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="68a60-108">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="68a60-109">Bir metin dosyasını silmek ve kullanıcıdan dosyanın silinmesi gerektiğini doğrulamasını istemek için</span><span class="sxs-lookup"><span data-stu-id="68a60-109">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="68a60-110">`DeleteFile`' İ ' olarak ayarlayarak dosyayı silmek için yöntemini `showUI` kullanın `AllDialogs` .</span><span class="sxs-lookup"><span data-stu-id="68a60-110">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="68a60-111">Aşağıdaki kod, adlı dosyanın nasıl silineceğini `test.txt` ve kullanıcının dosyanın silinmesi gerektiğini onaylamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="68a60-111">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="68a60-112">Bir metin dosyasını silmek ve geri dönüşüm kutusu 'na göndermek için</span><span class="sxs-lookup"><span data-stu-id="68a60-112">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="68a60-113">`DeleteFile`Parametresi için belirterek dosyayı silmek için yöntemini kullanın `SendToRecycleBin` `recycle` .</span><span class="sxs-lookup"><span data-stu-id="68a60-113">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="68a60-114">Aşağıdaki kod, adlı dosyanın nasıl silineceğini `test.txt` ve **geri dönüşüm** kutusu 'na nasıl gönderileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="68a60-114">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="68a60-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="68a60-115">Robust Programming</span></span>  

 <span data-ttu-id="68a60-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="68a60-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="68a60-117">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="68a60-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="68a60-118">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="68a60-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="68a60-119">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="68a60-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="68a60-120">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="68a60-120">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="68a60-121">Dosya kullanımda ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="68a60-121">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="68a60-122">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="68a60-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="68a60-123">Dosya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="68a60-123">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="68a60-124">Kullanıcının dosyayı silme izni yok veya dosya salt okunurdur ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="68a60-124">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="68a60-125">Kullanıcının yeterli izinlere () sahip olmadığı kısmi güven durumu vardır <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="68a60-125">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="68a60-126">Kullanıcı işlemi iptal etti ve `onUserCancel` () olarak ayarlandı `ThrowException` <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="68a60-126">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a60-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68a60-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="68a60-128">Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="68a60-128">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
