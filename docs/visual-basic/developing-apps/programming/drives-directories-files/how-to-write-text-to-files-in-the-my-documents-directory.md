---
title: 'Nasıl yapılır: Belgelerim Dizinindeki Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bb3a9bdc44f86fbcdb3c56ee088740efdfebe95d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546464"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="76ecd-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="76ecd-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="76ecd-103">`My.Computer.FileSystem.SpecialDirectories`Nesnesi, **MyDocuments** dizini gibi özel dizinlere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="76ecd-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="76ecd-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="76ecd-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="76ecd-105">Yeni metin dosyalarını Belgelerim dizinine yazmak için</span><span class="sxs-lookup"><span data-stu-id="76ecd-105">To write new text files in the My Documents directory</span></span>  
  
1. <span data-ttu-id="76ecd-106">`My.Computer.FileSystem.SpecialDirectories.MyDocuments`Yolunu sağlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76ecd-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="76ecd-107">`WriteAllText`Belirtilen dosyaya metin yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="76ecd-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="76ecd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="76ecd-108">Example</span></span>  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76ecd-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="76ecd-109">Compiling the Code</span></span>  

 <span data-ttu-id="76ecd-110">`test.txt`Yazmak istediğiniz dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="76ecd-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="76ecd-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="76ecd-111">Robust Programming</span></span>  

 <span data-ttu-id="76ecd-112">Bu kod, dosyaya metin yazarken ortaya çıkabilecek tüm özel durumları yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76ecd-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="76ecd-113">Kullanıcı seçimlerini geçerli dosya adlarıyla sınırlayan [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) ve [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) bileşenleri gibi Windows Forms denetimleri kullanarak özel durumların olasılığını azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76ecd-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) and the [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="76ecd-114">Ancak, bu denetimlerin kullanılması, örnek değildir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="76ecd-115">Dosya sistemi, kullanıcının bir dosyayı seçtiği zaman ve kodun yürütüldüğü saat arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="76ecd-116">Bu nedenle, dosyalarla çalışırken neredeyse her zaman özel durum işleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="76ecd-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="76ecd-117">.NET Framework Security</span></span>  

 <span data-ttu-id="76ecd-118">Kısmi güven bağlamında çalıştırıyorsanız, yetersiz ayrıcalıklar nedeniyle kod bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="76ecd-119">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="76ecd-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="76ecd-120">Bu örnek yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76ecd-120">This example creates a new file.</span></span> <span data-ttu-id="76ecd-121">Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için oluşturma izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="76ecd-122">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="76ecd-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="76ecd-123">Dosya zaten mevcutsa, uygulamanın daha az bir ayrıcalık olmak üzere yalnızca yazma izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="76ecd-124">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve bir klasör için oluşturma ayrıcalıkları vermek yerine yalnızca tek bir dosyaya okuma ayrıcalıkları verin.</span><span class="sxs-lookup"><span data-stu-id="76ecd-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="76ecd-125">Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya **Program Files** klasöründen daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="76ecd-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="76ecd-126">Daha fazla bilgi için bkz. [ACL teknolojisine genel bakış](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="76ecd-126">For more information, see [ACL Technology Overview](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ecd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76ecd-127">See also</span></span>

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
