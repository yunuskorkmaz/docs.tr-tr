---
title: "Nasıl yapılır: Visual Basic'te dosya karşıya yükleme"
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 486351bc140a2bbf18bb8f85f761fc491f028bba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840360"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="bbf3d-102">Nasıl yapılır: Visual Basic'te dosya karşıya yükleme</span><span class="sxs-lookup"><span data-stu-id="bbf3d-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="bbf3d-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Yöntemi, bir dosyayı karşıya yüklemek ve uzak bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="bbf3d-104">Varsa `ShowUI` parametrenin ayarlanmış `True`, karşıya yükleme ilerlemesini gösterir ve işlemi iptal etmesine izin veren bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="bbf3d-105">Bir dosyayı karşıya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bbf3d-105">To upload a file</span></span>  
  
-   <span data-ttu-id="bbf3d-106">Kullanım `UploadFile` kaynak dosya konumu ve hedef dizin konumunu bir dize veya URI'si (Tekdüzen Kaynak Tanımlayıcısı) olarak belirterek, bir dosyayı karşıya yüklemek için yöntemi. Bu örnek dosyayı yükler `Order.txt` için `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="bbf3d-107">Bir dosyayı karşıya yüklemek ve işlemin ilerlemesini Göster</span><span class="sxs-lookup"><span data-stu-id="bbf3d-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="bbf3d-108">Kullanım `UploadFile` kaynak dosya konumu ve hedef dizin konumunu bir dize veya URI olarak belirterek, bir dosyayı karşıya yüklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="bbf3d-109">Bu örnek dosyayı yükler `Order.txt` için `http://www.cohowinery.com/uploads.aspx` bir kullanıcı adı ve parola sağlamadan karşıya yükleme ilerlemesini gösterir ve bir zaman aşımı aralığı aralığını 500 milisaniyenin vardır.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="bbf3d-110">Bir kullanıcı adı ve parola sağlayan, bir dosyayı karşıya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bbf3d-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="bbf3d-111">Kullanım `UploadFile` bir dize veya URI olarak kaynak dosya konumu ve hedef dizin konumunu belirtme ve kullanıcı adı ve parola belirterek bir dosyayı karşıya yüklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="bbf3d-112">Bu örnek dosyayı yükler `Order.txt` için `http://www.cohowinery.com/uploads.aspx`, kullanıcı adını sağlayarak `anonymous` parolayı da boş.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bbf3d-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="bbf3d-113">Robust Programming</span></span>  
 <span data-ttu-id="bbf3d-114">Aşağıdaki koşullar, bir özel durum oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="bbf3d-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="bbf3d-115">Yerel dosya yolu geçerli değil (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bbf3d-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="bbf3d-116">Kimlik doğrulaması başarısız oldu (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="bbf3d-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="bbf3d-117">Bağlantı zaman aşımına uğradı (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="bbf3d-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf3d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf3d-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="bbf3d-119">Nasıl yapılır: Dosya indirme</span><span class="sxs-lookup"><span data-stu-id="bbf3d-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="bbf3d-120">Nasıl yapılır: Dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="bbf3d-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
