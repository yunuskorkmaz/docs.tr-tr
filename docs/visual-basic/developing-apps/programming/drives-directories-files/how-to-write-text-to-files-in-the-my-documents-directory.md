---
title: "Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 94532e27f38eb0f8b1ca91d424a97aba1b9f5173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589676"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="334ec-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="334ec-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="334ec-103">`My.Computer.FileSystem.SpecialDirectories` Nesne özel dizinleri gibi erişmenizi sağlar **MyDocuments** dizin.</span><span class="sxs-lookup"><span data-stu-id="334ec-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="334ec-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="334ec-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="334ec-105">Belgelerim dizini yeni metin dosyaları yazma</span><span class="sxs-lookup"><span data-stu-id="334ec-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="334ec-106">Kullanım `My.Computer.FileSystem.SpecialDirectories.MyDocuments` özelliği yolunu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="334ec-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="334ec-107">Kullanım `WriteAllText` metni belirtilen dosyaya yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="334ec-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="334ec-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="334ec-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="334ec-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="334ec-109">Compiling the Code</span></span>  
 <span data-ttu-id="334ec-110">Değiştir `test.txt` yazmak istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="334ec-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="334ec-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="334ec-111">Robust Programming</span></span>  
 <span data-ttu-id="334ec-112">Bu kod metin dosyasına yazma sırasında meydana gelebilecek tüm özel durumları yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="334ec-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="334ec-113">Windows Forms denetimleri gibi kullanarak özel durumlar olasılığını azaltabilir [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) geçerli dosya adları için kullanıcı seçimlerini sınırlamak bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="334ec-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="334ec-114">Bu denetimleri kullanarak ancak kusursuz, değildir.</span><span class="sxs-lookup"><span data-stu-id="334ec-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="334ec-115">Dosya sistemi, kullanıcı bir dosyayı seçtiğinde ve kodu yürütür saat arasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="334ec-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="334ec-116">Özel durum işleme Bu nedenle neredeyse her zaman dosyalarıyla çalışma zaman ile gereklidir.</span><span class="sxs-lookup"><span data-stu-id="334ec-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="334ec-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="334ec-117">.NET Framework Security</span></span>  
 <span data-ttu-id="334ec-118">Kısmi güven bağlamda çalıştırıyorsanız, kodu nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="334ec-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="334ec-119">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="334ec-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="334ec-120">Bu örnekte yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="334ec-120">This example creates a new file.</span></span> <span data-ttu-id="334ec-121">Bir uygulama bir dosya oluşturmak gerekirse, bu uygulama için klasör oluşturma izniniz gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="334ec-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="334ec-122">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="334ec-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="334ec-123">Dosya zaten varsa, uygulamanın yalnızca yazma izni, daha düşük ayrıcalık gerekir.</span><span class="sxs-lookup"><span data-stu-id="334ec-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="334ec-124">Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca tek bir dosya için okuma ayrıcalıkları vermek yerine bir klasör oluşturma ayrıcalığı vermek için daha güvenli olan.</span><span class="sxs-lookup"><span data-stu-id="334ec-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="334ec-125">Ayrıca, verileri kullanıcı klasörleri kök klasörüne yazmak için daha güvenli olan veya **Program Files** klasör.</span><span class="sxs-lookup"><span data-stu-id="334ec-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="334ec-126">Daha fazla bilgi için bkz: [ACL teknoloji genel bakış](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="334ec-126">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334ec-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="334ec-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
