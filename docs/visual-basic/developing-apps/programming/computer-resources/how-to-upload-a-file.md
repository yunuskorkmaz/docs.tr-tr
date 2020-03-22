---
title: 'Nasıl Yapılır: Karşıya Dosya Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345555"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="87a22-102">Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme</span><span class="sxs-lookup"><span data-stu-id="87a22-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="87a22-103">Yöntem, <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> bir dosyayı yüklemek ve uzak bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87a22-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="87a22-104">`ShowUI` Parametre `True`ayarlanmışsa, yüklemenin ilerlemesini gösteren ve kullanıcıların işlemi iptal etmesine izin veren bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="87a22-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="87a22-105">Dosya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="87a22-105">To upload a file</span></span>  
  
- <span data-ttu-id="87a22-106">Kaynak `UploadFile` dosyanın konumunu ve hedef dizin konumunu dize veya URI (Tekdüzen Kaynak Tanımlayıcı) olarak belirterek dosya yüklemek için yöntemi kullanın. Bu örnek, `Order.txt` dosyayı `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="87a22-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="87a22-107">Bir dosya yüklemek ve işlemin ilerlemesini göstermek için</span><span class="sxs-lookup"><span data-stu-id="87a22-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="87a22-108">Kaynak `UploadFile` dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek dosya yüklemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="87a22-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="87a22-109">Bu örnek, bir `Order.txt` `http://www.cohowinery.com/uploads.aspx` kullanıcı adı veya parola sağlamadan dosyayı yükler, yüklemenin ilerlemesini gösterir ve 500 milisaniyelik bir zaman aralığına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87a22-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="87a22-110">Bir dosya yüklemek için, kullanıcı adı ve parola sağlama</span><span class="sxs-lookup"><span data-stu-id="87a22-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="87a22-111">Bir `UploadFile` dosyayı yüklemek, kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek ve kullanıcı adını ve parolayı belirtmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="87a22-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="87a22-112">Bu örnek, `Order.txt` dosyayı `http://www.cohowinery.com/uploads.aspx`kullanıcı adı `anonymous` ve boş bir parola sağlayan dosyaya yükler.</span><span class="sxs-lookup"><span data-stu-id="87a22-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="87a22-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="87a22-113">Robust Programming</span></span>  

 <span data-ttu-id="87a22-114">Aşağıdaki koşullar bir özel durum atabilir:</span><span class="sxs-lookup"><span data-stu-id="87a22-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="87a22-115">Yerel dosya yolu geçerli<xref:System.ArgumentException>değil ( ).</span><span class="sxs-lookup"><span data-stu-id="87a22-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="87a22-116">Kimlik doğrulama<xref:System.Security.SecurityException>başarısız oldu ( ).</span><span class="sxs-lookup"><span data-stu-id="87a22-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="87a22-117">Bağlantı zamanlanmış (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="87a22-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a22-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87a22-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="87a22-119">Nasıl Yapılır: Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="87a22-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="87a22-120">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="87a22-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
