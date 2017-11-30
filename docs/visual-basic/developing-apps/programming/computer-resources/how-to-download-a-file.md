---
title: "Nasıl Yapılır: Visual Basic'te Dosya İndirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc67d28b870f86c6464e86f7682f71e6e36ea9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="d98c2-102">Nasıl Yapılır: Visual Basic'te Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="d98c2-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="d98c2-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Yöntemi, bir uzak dosya karşıdan yüklemek ve belirli bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d98c2-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="d98c2-104">Varsa `ShowUI` parametrenin ayarlanmış `True`, yükleme ilerlemesini gösteren ve kullanıcıların işlemi iptal etmek bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d98c2-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="d98c2-105">Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; var olan dosyaların üzerine yazmak istiyorsanız, Ayarla `overwrite` parametresi `True`.</span><span class="sxs-lookup"><span data-stu-id="d98c2-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="d98c2-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d98c2-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d98c2-107">Sürücü adı geçerli değil (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d98c2-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d98c2-108">Gerekli kimlik doğrulaması olmayan sağlanmış (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d98c2-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d98c2-109">Sunucu belirtilen içinde yanıt vermezse `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="d98c2-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="d98c2-110">İstek Web sitesi tarafından reddedilir (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="d98c2-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="d98c2-111">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="d98c2-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="d98c2-112">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d98c2-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="d98c2-113">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d98c2-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="d98c2-114">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="d98c2-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="d98c2-115">Bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="d98c2-115">To download a file</span></span>  
  
-   <span data-ttu-id="d98c2-116">Kullanım `DownloadFile` yöntemi bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosyasının depolanacağı konumu belirtme dosyasını indirin.</span><span class="sxs-lookup"><span data-stu-id="d98c2-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="d98c2-117">Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="d98c2-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="d98c2-118">Bir zaman aşımı aralığı belirterek, bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="d98c2-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="d98c2-119">Kullanım `DownloadFile` yöntemi bir dize veya URI olarak hedef dosyanın konumunu belirtme, dosyasının depolanacağı konumu belirtme ve zaman aşımı aralığı (varsayılan değer 1000) milisaniye cinsinden belirten dosyasını indirin.</span><span class="sxs-lookup"><span data-stu-id="d98c2-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="d98c2-120">Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, 500 milisaniye zaman aşımı aralığı belirtme:</span><span class="sxs-lookup"><span data-stu-id="d98c2-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="d98c2-121">Bir kullanıcı adı ve parola sağlayarak bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="d98c2-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="d98c2-122">Kullanım `DownLoadFile` yöntemi bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosya, kullanıcı adı ve parola depolanacağı konumu belirtme dosyasını indirin.</span><span class="sxs-lookup"><span data-stu-id="d98c2-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="d98c2-123">Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, kullanıcı adı ile `anonymous` ve boş bir parola.</span><span class="sxs-lookup"><span data-stu-id="d98c2-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d98c2-124">Tarafından kullanılan FTP protokolünü `DownLoadFile` yöntemi bilgilerini, parolalar düz metin olarak gönderir ve hassas bilgiler iletmek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d98c2-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98c2-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d98c2-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [<span data-ttu-id="d98c2-126">Nasıl yapılır: bir dosyayı karşıya yüklemek</span><span class="sxs-lookup"><span data-stu-id="d98c2-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [<span data-ttu-id="d98c2-127">Nasıl yapılır: dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="d98c2-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
