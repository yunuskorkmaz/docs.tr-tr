---
title: 'Nasıl yapılır: (Visual Basic) StreamReader olan dosyalardaki metni okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 0ce3bffc151f149773c5279e1da08f74319b00f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968706"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="83779-102">Nasıl yapılır: (Visual Basic) StreamReader olan dosyalardaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="83779-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="83779-103">`My.Computer.FileSystem` Nesne açmak için yöntemler sağlar bir <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="83779-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="83779-104">Bu yöntemler `OpenTextFileWriter` ve `OpenTextFileReader`, seçtiğiniz sürece Intellisense'te görünmez yöntemleri Gelişmiş **tüm** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="83779-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="83779-105">Bir dosyadan metin okuyucu ile bir satır okunamadı</span><span class="sxs-lookup"><span data-stu-id="83779-105">To read a line from a file with a text reader</span></span>  
  
-   <span data-ttu-id="83779-106">Kullanım `OpenTextFileReader` açmak için yöntemi <xref:System.IO.TextReader>, dosya belirtme.</span><span class="sxs-lookup"><span data-stu-id="83779-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="83779-107">Bu örnek adlı bir dosya açar `testfile.txt`bir satır okur ve satırı bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="83779-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="83779-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="83779-108">Robust Programming</span></span>  
 <span data-ttu-id="83779-109">Okunan Dosya bir metin dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83779-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="83779-110">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="83779-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="83779-111">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="83779-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="83779-112">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="83779-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="83779-113">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="83779-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="83779-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="83779-114">.NET Framework Security</span></span>  
 <span data-ttu-id="83779-115">Bir dosyadan okunan, derlemenizin ayrıcalık düzeyi verilen tarafından gerektirir <xref:System.Security.Permissions.FileIOPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="83779-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="83779-116">Kısmi güven bağlamda çalıştırıyorsanız, kod bir özel durum yetersiz ayrıcalıklar nedeniyle fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="83779-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="83779-117">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="83779-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="83779-118">Kullanıcının dosyaya erişimi de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83779-118">The user also needs access to the file.</span></span> <span data-ttu-id="83779-119">Daha fazla bilgi için [ACL teknolojisine genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="83779-119">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83779-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83779-120">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="83779-121">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="83779-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [<span data-ttu-id="83779-122">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="83779-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
