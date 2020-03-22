---
title: 'Nasıl Yapılır: Belgelerim Dizinindeki Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334519"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="d2d7d-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="d2d7d-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="d2d7d-103">Nesne, `My.Computer.FileSystem.SpecialDirectories` **MyDocuments** dizini gibi özel dizinlere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d2d7d-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="d2d7d-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="d2d7d-105">Belgelerim dizinine yeni metin dosyaları yazmak için</span><span class="sxs-lookup"><span data-stu-id="d2d7d-105">To write new text files in the My Documents directory</span></span>  
  
1. <span data-ttu-id="d2d7d-106">Yolu `My.Computer.FileSystem.SpecialDirectories.MyDocuments` sağlamak için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="d2d7d-107">Belirtilen `WriteAllText` dosyaya metin yazmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="d2d7d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2d7d-108">Example</span></span>  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2d7d-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d2d7d-109">Compiling the Code</span></span>  

 <span data-ttu-id="d2d7d-110">Yazmak `test.txt` istediğiniz dosyanın adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d2d7d-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d2d7d-111">Robust Programming</span></span>  

 <span data-ttu-id="d2d7d-112">Bu kod, dosyaya metin yazarken oluşabilecek tüm özel durumları yeniden atar.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="d2d7d-113">Kullanıcı seçeneklerini geçerli dosya adlarıyla sınırlayan [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) bileşenleri gibi Windows Forms denetimlerini kullanarak özel durumlar olasılığını azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="d2d7d-114">Ancak, bu denetimleri kullanarak kusursuz değildir.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="d2d7d-115">Dosya sistemi, kullanıcının bir dosyayı seçtiği saat ile kodun yürütüldettiği saat arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="d2d7d-116">Bu nedenle, dosyalarla çalışırken özel durum işleme neredeyse her zaman gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d2d7d-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d2d7d-117">.NET Framework Security</span></span>  

 <span data-ttu-id="d2d7d-118">Kısmi güven bağlamında çalışıyorsanız, kod yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="d2d7d-119">Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="d2d7d-120">Bu örnek yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-120">This example creates a new file.</span></span> <span data-ttu-id="d2d7d-121">Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için oluşturma iznine ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="d2d7d-122">İzinler erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="d2d7d-123">Dosya zaten varsa, uygulamanın yalnızca yazma iznine, daha az bir ayrıcalığa ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="d2d7d-124">Mümkün olduğunda, dosyayı dağıtım sırasında oluşturmak ve bir klasör için ayrıcalık oluştur'a ayrıcalık vermek yerine yalnızca tek bir dosyaya Okuma ayrıcalıkları vermek daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="d2d7d-125">Ayrıca, kullanıcı klasörlerine veri yazmak kök klasöre veya **Program Dosyaları** klasörüne yazmaktan daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="d2d7d-126">Daha fazla bilgi için [ACL Technology Genel Bakış'a](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-126">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d7d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d7d-127">See also</span></span>

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
