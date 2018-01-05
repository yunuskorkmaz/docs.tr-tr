---
title: "Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81eba9a71d90c79f72ccadfa65431754dfb0164e
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="f424c-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="f424c-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="f424c-103">`My.Computer.FileSystem.SpecialDirectories` Nesne özel dizinleri gibi erişmenizi sağlar **MyDocuments** dizin.</span><span class="sxs-lookup"><span data-stu-id="f424c-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="f424c-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="f424c-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="f424c-105">Belgelerim dizini yeni metin dosyaları yazma</span><span class="sxs-lookup"><span data-stu-id="f424c-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="f424c-106">Kullanım `My.Computer.FileSystem.SpecialDirectories.MyDocuments` özelliği yolunu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f424c-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="f424c-107">Kullanım `WriteAllText` metni belirtilen dosyaya yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="f424c-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="f424c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f424c-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f424c-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f424c-109">Compiling the Code</span></span>  
 <span data-ttu-id="f424c-110">Değiştir `test.txt` yazmak istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="f424c-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f424c-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f424c-111">Robust Programming</span></span>  
 <span data-ttu-id="f424c-112">Bu kod metin dosyasına yazma sırasında meydana gelebilecek tüm özel durumları yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f424c-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="f424c-113">Windows Forms denetimleri gibi kullanarak özel durumlar olasılığını azaltabilir [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) geçerli dosya adları için kullanıcı seçimlerini sınırlamak bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="f424c-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="f424c-114">Bu denetimleri kullanarak ancak kusursuz, değildir.</span><span class="sxs-lookup"><span data-stu-id="f424c-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="f424c-115">Dosya sistemi, kullanıcı bir dosyayı seçtiğinde ve kodu yürütür saat arasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f424c-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="f424c-116">Özel durum işleme Bu nedenle neredeyse her zaman dosyalarıyla çalışma zaman ile gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f424c-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f424c-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f424c-117">.NET Framework Security</span></span>  
 <span data-ttu-id="f424c-118">Kısmi güven bağlamda çalıştırıyorsanız, kodu nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="f424c-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="f424c-119">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="f424c-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="f424c-120">Bu örnekte yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f424c-120">This example creates a new file.</span></span> <span data-ttu-id="f424c-121">Bir uygulama bir dosya oluşturmak gerekirse, bu uygulama için klasör oluşturma izniniz gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f424c-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="f424c-122">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f424c-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="f424c-123">Dosya zaten varsa, uygulamanın yalnızca yazma izni, daha düşük ayrıcalık gerekir.</span><span class="sxs-lookup"><span data-stu-id="f424c-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="f424c-124">Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca tek bir dosya için okuma ayrıcalıkları vermek yerine bir klasör oluşturma ayrıcalığı vermek için daha güvenli olan.</span><span class="sxs-lookup"><span data-stu-id="f424c-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="f424c-125">Ayrıca, verileri kullanıcı klasörleri kök klasörüne yazmak için daha güvenli olan veya **Program Files** klasör.</span><span class="sxs-lookup"><span data-stu-id="f424c-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="f424c-126">Daha fazla bilgi için bkz: [ACL teknoloji genel bakış](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="f424c-126">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f424c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f424c-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
