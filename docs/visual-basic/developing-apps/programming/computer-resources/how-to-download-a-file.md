---
title: 'Nasıl yapılır: Visual Basic bir dosyayı indirin'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 9986a784e73f12698281f17a9d8e022e806504cb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957827"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="eb828-102">Nasıl yapılır: Visual Basic bir dosyayı indirin</span><span class="sxs-lookup"><span data-stu-id="eb828-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="eb828-103">Yöntemi <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> , uzak bir dosyayı indirmek ve belirli bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb828-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="eb828-104">`ShowUI` Parametresi olarak`True`ayarlandıysa, indirmenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal edebilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="eb828-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="eb828-105">Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız `overwrite` parametresini olarak `True`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb828-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="eb828-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="eb828-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="eb828-107">Sürücü adı geçerli değil (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="eb828-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="eb828-108">Gerekli kimlik doğrulaması sağlanmadı (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="eb828-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="eb828-109">Sunucu belirtilen `connectionTimeout` (<xref:System.TimeoutException>) içinde yanıt vermiyor.</span><span class="sxs-lookup"><span data-stu-id="eb828-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
- <span data-ttu-id="eb828-110">İstek Web sitesi (<xref:System.Net.WebException>) tarafından reddedildi.</span><span class="sxs-lookup"><span data-stu-id="eb828-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
> <span data-ttu-id="eb828-111">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="eb828-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="eb828-112">Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb828-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="eb828-113">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="eb828-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="eb828-114">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb828-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="eb828-115">Bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="eb828-115">To download a file</span></span>  
  
- <span data-ttu-id="eb828-116">Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu belirterek dosyayı indirmek için yönteminikullanın.`DownloadFile`</span><span class="sxs-lookup"><span data-stu-id="eb828-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="eb828-117">Bu örnek dosyasını `WineList.txt` konumundan `http://www.cohowinery.com/downloads` indirir ve öğesine `C:\Documents and Settings\All Users\Documents`kaydeder:</span><span class="sxs-lookup"><span data-stu-id="eb828-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="eb828-118">Bir dosya indirmek için bir zaman aşımı aralığı belirtme</span><span class="sxs-lookup"><span data-stu-id="eb828-118">To download a file, specifying a time-out interval</span></span>  
  
- <span data-ttu-id="eb828-119">Dosyayı indirmek için yöntemini kullanın, hedef dosyanın konumunu bir dize veya URI olarak belirterek, dosyanın kaydedileceği konumu belirterek ve zaman aşımı aralığını milisaniye cinsinden (varsayılan olarak 1000) belirterek. `DownloadFile`</span><span class="sxs-lookup"><span data-stu-id="eb828-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="eb828-120">Bu örnek, ' dan `WineList.txt` `http://www.cohowinery.com/downloads` dosyayı indirir ve 500 milisaniyelik bir zaman aşımı aralığı belirterek öğesine `C:\Documents and Settings\All Users\Documents`kaydeder:</span><span class="sxs-lookup"><span data-stu-id="eb828-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="eb828-121">Bir dosyayı indirmek için Kullanıcı adı ve parola sağlama</span><span class="sxs-lookup"><span data-stu-id="eb828-121">To download a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="eb828-122">Hedef dosyanın konumunu bir dize veya URI olarak belirterek ve dosyanın kaydedileceği konumu, Kullanıcı adını ve parolayı belirterek dosyayı indirmek için yönteminikullanın.`DownLoadFile`</span><span class="sxs-lookup"><span data-stu-id="eb828-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="eb828-123">Bu örnek `WineList.txt` , dosyasını `C:\Documents and Settings\All Users\Documents`' dan `http://www.cohowinery.com/downloads` indirir ve Kullanıcı adı `anonymous` ve boş bir parolayla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eb828-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="eb828-124">`DownLoadFile` Yöntemi tarafından kullanılan FTP protokolü, parolalar da dahil olmak üzere bilgileri düz metin olarak gönderir ve hassas bilgilerin iletilmesi için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb828-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb828-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb828-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="eb828-126">Nasıl yapılır: Karşıya dosya yükleme</span><span class="sxs-lookup"><span data-stu-id="eb828-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="eb828-127">Nasıl yapılır: Dosya yollarını Ayrıştır</span><span class="sxs-lookup"><span data-stu-id="eb828-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
