---
title: 'Nasıl yapılır: Dosya İndirme'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4923feb46ff638de9514a4d70fc00367491a6f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345628"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="8ecb1-102">Nasıl Yapılır: Visual Basic'te Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="8ecb1-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="8ecb1-103">Yöntemi <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> , uzak bir dosyayı indirmek ve belirli bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="8ecb1-104">`ShowUI` Parametresi olarak `True`ayarlandıysa, indirmenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal edebilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="8ecb1-105">Varsayılan olarak, aynı ada sahip var olan dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız `overwrite` parametresini olarak `True`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="8ecb1-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ecb1-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="8ecb1-107">Sürücü adı geçerli değil (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8ecb1-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="8ecb1-108">Gerekli kimlik doğrulaması sağlanmadı (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="8ecb1-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="8ecb1-109">Sunucu belirtilen `connectionTimeout` (<xref:System.TimeoutException>) içinde yanıt vermiyor.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="8ecb1-110">İstek Web sitesi (<xref:System.Net.WebException>) tarafından reddedildi.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="8ecb1-111">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="8ecb1-112">Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="8ecb1-113">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="8ecb1-114">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="8ecb1-115">Bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="8ecb1-115">To download a file</span></span>

- <span data-ttu-id="8ecb1-116">Hedef dosyanın `DownloadFile` konumunu bir DIZE veya URI olarak belirterek ve dosyanın kaydedileceği konumu belirterek dosyayı indirmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="8ecb1-117">Bu örnek dosyasını `WineList.txt` konumundan `http://www.cohowinery.com/downloads` indirir ve öğesine `C:\Documents and Settings\All Users\Documents`kaydeder:</span><span class="sxs-lookup"><span data-stu-id="8ecb1-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="8ecb1-118">Bir dosya indirmek için bir zaman aşımı aralığı belirtme</span><span class="sxs-lookup"><span data-stu-id="8ecb1-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="8ecb1-119">Dosyayı indirmek `DownloadFile` için yöntemini kullanın, hedef dosyanın konumunu bir DIZE veya URI olarak belirterek, dosyanın kaydedileceği konumu belirterek ve zaman aşımı aralığını milisaniye cinsinden (varsayılan olarak 1000) belirterek.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="8ecb1-120">Bu örnek, ' dan `WineList.txt` `http://www.cohowinery.com/downloads` dosyayı indirir ve 500 milisaniyelik bir zaman aşımı aralığı belirterek öğesine `C:\Documents and Settings\All Users\Documents`kaydeder:</span><span class="sxs-lookup"><span data-stu-id="8ecb1-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="8ecb1-121">Bir dosyayı indirmek için Kullanıcı adı ve parola sağlama</span><span class="sxs-lookup"><span data-stu-id="8ecb1-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="8ecb1-122">Hedef dosyanın `DownLoadFile` konumunu bir DIZE veya URI olarak belirterek ve dosyanın kaydedileceği konumu, Kullanıcı adını ve parolayı belirterek dosyayı indirmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="8ecb1-123">Bu `WineList.txt` örnek, dosyasını `http://www.cohowinery.com/downloads` `C:\Documents and Settings\All Users\Documents`' dan indirir ve Kullanıcı adı `anonymous` ve boş bir parolayla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="8ecb1-124">`DownLoadFile` Yöntemi tarafından kullanılan FTP protokolü, parolalar da dahil olmak üzere bilgileri düz metin olarak gönderir ve hassas bilgilerin iletilmesi için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ecb1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ecb1-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="8ecb1-126">Nasıl yapılır: Karşıya Dosya Yükleme</span><span class="sxs-lookup"><span data-stu-id="8ecb1-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="8ecb1-127">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="8ecb1-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
