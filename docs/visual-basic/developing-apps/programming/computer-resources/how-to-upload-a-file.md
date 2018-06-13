---
title: "Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme"
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 769c04430f8323dfde680fca45cfcd67809bdab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583792"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="ebf64-102">Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme</span><span class="sxs-lookup"><span data-stu-id="ebf64-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="ebf64-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Yöntemi, bir dosyayı karşıya yükleme ve uzak bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ebf64-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="ebf64-104">Varsa `ShowUI` parametrenin ayarlanmış `True`, karşıya yükleme ilerlemesini gösterir ve işlemi iptal etmek kullanıcıların sağlayan bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ebf64-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="ebf64-105">Bir dosyayı karşıya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="ebf64-105">To upload a file</span></span>  
  
-   <span data-ttu-id="ebf64-106">Kullanım `UploadFile` bir dize veya URI'yi (Tekdüzen Kaynak Tanımlayıcısı) olarak kaynak dosya konumu ve hedef dizin konumunu belirten bir dosyayı karşıya yüklemeyi yöntemi. Bu örnek dosya karşıya yükleme `Order.txt` için `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="ebf64-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="ebf64-107">Bir dosyayı karşıya yükleyin ve işlemin ilerlemesini Göster</span><span class="sxs-lookup"><span data-stu-id="ebf64-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="ebf64-108">Kullanım `UploadFile` bir dize veya URI olarak kaynak dosya konumu ve hedef dizin konumunu belirten bir dosyayı karşıya yüklemeyi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ebf64-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="ebf64-109">Bu örnek dosya karşıya yükleme `Order.txt` için `http://www.cohowinery.com/uploads.aspx` bir kullanıcı adı veya parola girmeden karşıya yükleme ilerlemesini gösterir ve bir zaman aşımı aralığı (500 milisaniye olarak) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ebf64-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="ebf64-110">Bir kullanıcı adı ve parola sağlayarak bir dosyayı karşıya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="ebf64-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="ebf64-111">Kullanım `UploadFile` bir dize veya URI olarak kaynak dosya konumu ve hedef dizin konumunu belirtme ve kullanıcı adı ve parola belirterek bir dosyayı karşıya yüklemeyi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ebf64-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="ebf64-112">Bu örnek dosya karşıya yükleme `Order.txt` için `http://www.cohowinery.com/uploads.aspx`, kullanıcı adını sağlayarak `anonymous` ve boş bir parola.</span><span class="sxs-lookup"><span data-stu-id="ebf64-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ebf64-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ebf64-113">Robust Programming</span></span>  
 <span data-ttu-id="ebf64-114">Aşağıdaki koşullar, bir özel durum:</span><span class="sxs-lookup"><span data-stu-id="ebf64-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="ebf64-115">Yerel dosya yolu geçerli değil (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ebf64-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ebf64-116">Kimlik doğrulama başarısız oldu (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ebf64-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="ebf64-117">Bağlantı zaman aşımına uğradı (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="ebf64-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf64-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebf64-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>  
 [<span data-ttu-id="ebf64-119">Nasıl Yapılır: Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="ebf64-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [<span data-ttu-id="ebf64-120">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="ebf64-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
