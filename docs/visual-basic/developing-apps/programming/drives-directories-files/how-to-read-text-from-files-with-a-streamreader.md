---
title: 'Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: cd6f7b70f2ddabfc5a1476c45ca9813b9a4d949f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588661"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="f2fb6-102">Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2fb6-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="f2fb6-103">`My.Computer.FileSystem` Nesne açmak için yöntemler sağlar bir <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="f2fb6-104">Bu yöntemler `OpenTextFileWriter` ve `OpenTextFileReader`, seçtiğiniz sürece IntelliSense içinde görünmez yöntemleri Gelişmiş **tüm** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="f2fb6-105">Bir satır bir metin okuyucu bir dosyasından okunamıyor</span><span class="sxs-lookup"><span data-stu-id="f2fb6-105">To read a line from a file with a text reader</span></span>  
  
-   <span data-ttu-id="f2fb6-106">Kullanım `OpenTextFileReader` açmak için yöntemini <xref:System.IO.TextReader>, dosya belirtme.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="f2fb6-107">Bu örnek adlı dosyayı açar `testfile.txt`, bir satır ondan okur ve satırı bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f2fb6-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f2fb6-108">Robust Programming</span></span>  
 <span data-ttu-id="f2fb6-109">Salt okunur dosya bir metin dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="f2fb6-110">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f2fb6-111">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="f2fb6-112">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="f2fb6-113">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f2fb6-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f2fb6-114">.NET Framework Security</span></span>  
 <span data-ttu-id="f2fb6-115">Bir dosyadan okunan için derlemenizi ayrıcalık düzeyi verilen tarafından gerektirir <xref:System.Security.Permissions.FileIOPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="f2fb6-116">Kısmi güven bağlamda çalıştırıyorsanız, kodu nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="f2fb6-117">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="f2fb6-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="f2fb6-118">Kullanıcının dosyaya erişim de gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-118">The user also needs access to the file.</span></span> <span data-ttu-id="f2fb6-119">Daha fazla bilgi için bkz: [ACL teknoloji genel bakış](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="f2fb6-119">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2fb6-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2fb6-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>  
 [<span data-ttu-id="f2fb6-121">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="f2fb6-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)  
 [<span data-ttu-id="f2fb6-122">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="f2fb6-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
