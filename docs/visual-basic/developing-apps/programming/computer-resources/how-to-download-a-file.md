---
title: "Nasıl yapılır: Visual Basic'te dosya indirme"
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: bebb40a732415312742116b0b94743495049c477
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826658"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="b7d99-102">Nasıl yapılır: Visual Basic'te dosya indirme</span><span class="sxs-lookup"><span data-stu-id="b7d99-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="b7d99-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Yöntemi, uzak bir dosyaya indirin ve belirli bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7d99-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="b7d99-104">Varsa `ShowUI` parametrenin ayarlanmış `True`, indirme işleminin ilerleme durumunu gösterir ve kullanıcı işlemi iptal etme iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7d99-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="b7d99-105">Varsayılan olarak, aynı ada sahip mevcut dosyaların üzerine yazılmaz; Varolan dosyaların üzerine yazmak istiyorsanız ayarlayın `overwrite` parametresi `True`.</span><span class="sxs-lookup"><span data-stu-id="b7d99-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="b7d99-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b7d99-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b7d99-107">Sürücü adı geçerli değil (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b7d99-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b7d99-108">Gerekli kimlik doğrulama yok sağlanmış (<xref:System.UnauthorizedAccessException> veya <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b7d99-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="b7d99-109">Sunucu belirtilen içinde yanıt vermezse `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="b7d99-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="b7d99-110">İstek Web sitesi tarafından reddedilir (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="b7d99-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7d99-111">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="b7d99-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b7d99-112">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b7d99-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="b7d99-113">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b7d99-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="b7d99-114">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7d99-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="b7d99-115">Bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="b7d99-115">To download a file</span></span>  
  
-   <span data-ttu-id="b7d99-116">Kullanım `DownloadFile` bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosyasının depolanacağı konumu belirtin dosyayı indirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7d99-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="b7d99-117">Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="b7d99-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="b7d99-118">Bir zaman aşımı aralığı belirterek, bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="b7d99-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="b7d99-119">Kullanım `DownloadFile` zaman aşımı aralığı (varsayılan değer 1000) milisaniye cinsinden belirten bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosyasının depolanacağı konumu belirtme dosyasını indirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7d99-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="b7d99-120">Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, aralığını 500 milisaniyenin bir zaman aşımı aralığı belirtme:</span><span class="sxs-lookup"><span data-stu-id="b7d99-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="b7d99-121">Bir kullanıcı adı ve parola sağlayan, bir dosyayı indirmek için</span><span class="sxs-lookup"><span data-stu-id="b7d99-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="b7d99-122">Kullanım `DownLoadFile` bir dize veya URI olarak hedef dosyanın konumunu belirtme ve dosya, kullanıcı adı ve parola depolanacağı konumu belirtin dosyayı indirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7d99-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="b7d99-123">Bu örnek dosya yüklemeleri `WineList.txt` gelen `http://www.cohowinery.com/downloads` ve kaydeder `C:\Documents and Settings\All Users\Documents`, kullanıcı adıyla `anonymous` parolayı da boş.</span><span class="sxs-lookup"><span data-stu-id="b7d99-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b7d99-124">Tarafından kullanılan FTP protokolünü `DownLoadFile` yöntemi bilgilerini, parolaları düz metin olarak gönderir ve hassas bilgileri aktarmak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7d99-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d99-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7d99-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="b7d99-126">Nasıl yapılır: Bir dosyayı karşıya yükleyin</span><span class="sxs-lookup"><span data-stu-id="b7d99-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="b7d99-127">Nasıl yapılır: Dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b7d99-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
