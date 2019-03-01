---
title: "Nasıl yapılır: Dosyalara metin yazma Visual Basic'te Belgelerim dizini"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 147dad822a8bc8b8e9692b88f6b498f841bac1fa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966755"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="194b1-102">Nasıl yapılır: Dosyalara metin yazma Visual Basic'te Belgelerim dizini</span><span class="sxs-lookup"><span data-stu-id="194b1-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="194b1-103">`My.Computer.FileSystem.SpecialDirectories` Nesnesinin özel dizinleri gibi erişmenizi sağlar **MyDocuments** dizin.</span><span class="sxs-lookup"><span data-stu-id="194b1-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="194b1-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="194b1-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="194b1-105">Belgelerim dizini içinde yeni metin dosyaları yazma</span><span class="sxs-lookup"><span data-stu-id="194b1-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="194b1-106">Kullanım `My.Computer.FileSystem.SpecialDirectories.MyDocuments` yolunu sağlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="194b1-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2.  <span data-ttu-id="194b1-107">Kullanım `WriteAllText` metni belirtilen dosyaya yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="194b1-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="194b1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="194b1-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="194b1-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="194b1-109">Compiling the Code</span></span>  
 <span data-ttu-id="194b1-110">Değiştirin `test.txt` yazmak istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="194b1-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="194b1-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="194b1-111">Robust Programming</span></span>  
 <span data-ttu-id="194b1-112">Bu kod, metin dosyasına yazma sırasında oluşabilecek tüm özel durumları yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="194b1-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="194b1-113">Windows Forms denetimlerini kullanarak özel durumları olasılığını azaltabilirsiniz [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) geçerli dosya adları için kullanıcı seçenekler sınırlandıran bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="194b1-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="194b1-114">Bu denetimleri kullanarak ancak kusursuz, değildir.</span><span class="sxs-lookup"><span data-stu-id="194b1-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="194b1-115">Dosya sistemi, bir dosya kullanıcının seçtiği zaman ve kodu yürüten saat arasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="194b1-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="194b1-116">Özel durum işleme Bu nedenle neredeyse her zaman dosyalarıyla çalışma ile gereklidir.</span><span class="sxs-lookup"><span data-stu-id="194b1-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="194b1-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="194b1-117">.NET Framework Security</span></span>  
 <span data-ttu-id="194b1-118">Kısmi güven bağlamda çalıştırıyorsanız, kod bir özel durum yetersiz ayrıcalıklar nedeniyle fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="194b1-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="194b1-119">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="194b1-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="194b1-120">Bu örnek, yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="194b1-120">This example creates a new file.</span></span> <span data-ttu-id="194b1-121">Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulama için klasör oluşturma izniniz gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="194b1-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="194b1-122">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="194b1-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="194b1-123">Dosya zaten varsa, uygulamanın yalnızca yazma izni, daha az ayrıcalıkla gerekir.</span><span class="sxs-lookup"><span data-stu-id="194b1-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="194b1-124">Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca tek bir dosyayı okuma ayrıcalıkları vermek yerine bir klasör oluşturma ayrıcalıkları vermek için daha güvenli olması.</span><span class="sxs-lookup"><span data-stu-id="194b1-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="194b1-125">Ayrıca, verileri kullanıcı klasörleri kök klasörüne yazmak için daha güvenli olması veya **Program dosyaları** klasör.</span><span class="sxs-lookup"><span data-stu-id="194b1-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="194b1-126">Daha fazla bilgi için [ACL teknolojisine genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="194b1-126">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194b1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="194b1-127">See also</span></span>
- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
