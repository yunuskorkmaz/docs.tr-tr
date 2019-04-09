---
title: 'Nasıl yapılır: OpenFileDialog bileşeni ile açık dosyalar'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 7f4e96f1714a182647665f12e29d38f2b8037478
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159113"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="1f833-102">Nasıl yapılır: OpenFileDialog ile açık dosyalar</span><span class="sxs-lookup"><span data-stu-id="1f833-102">How to: Open files with the OpenFileDialog</span></span> 

<span data-ttu-id="1f833-103"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> Bileşeni göz atma ve dosyalar seçmek için Windows iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="1f833-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="1f833-104">Seçili dosyaları açmak ve okumak için kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> yöntemi veya bir örneğini oluşturmak <xref:System.IO.StreamReader?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f833-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1f833-105">Aşağıdaki örnekler, iki yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f833-105">The following examples show both approaches.</span></span> 

<span data-ttu-id="1f833-106">.NET Framework'teki almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği gerektiren bir ayrıcalık düzeyi verilmiş tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f833-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1f833-107">Örnekleri çalıştırmak bir <xref:System.Security.Permissions.FileIOPermission> izni denetleyin ve bir özel durum yetersiz ayrıcalıklar nedeniyle bir kısmi güven bağlamında çalıştırırsanız atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f833-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="1f833-108">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="1f833-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="1f833-109">Derleme ve bu örnekler, .NET Framework uygulamaları Çalıştır C# veya Visual Basic komut satırı.</span><span class="sxs-lookup"><span data-stu-id="1f833-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="1f833-110">Daha fazla bilgi için [csc.exe ile komut satırı derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="1f833-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="1f833-111">.NET Core 3.0 ile başlayarak, ayrıca yapı ve örnekler Windows .NET Core uygulamaları .NET Core Windows Forms bir klasörden Çalıştır  *\<klasör adı > .csproj* proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="1f833-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="1f833-112">Örnek: StreamReader olan bir akış olarak bir dosyayı okuma</span><span class="sxs-lookup"><span data-stu-id="1f833-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="1f833-113">Aşağıdaki örnek Windows Forms kullanan <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> açmak için olay işleyicisi <xref:System.Windows.Forms.OpenFileDialog> ile <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f833-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="1f833-114">Kullanıcı bir dosya seçer ve seçer sonra **Tamam**, örneği <xref:System.IO.StreamReader> sınıf dosyasını okur ve form denetiminin metin kutusuna içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f833-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="1f833-115">Dosya akışları okuma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f833-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="1f833-116">Örnek: Openfıle ile filtre uygulanmış bir seçimin bir dosyayı açma</span><span class="sxs-lookup"><span data-stu-id="1f833-116">Example: Open a file from a filtered selection with OpenFile</span></span> 

<span data-ttu-id="1f833-117">Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> açmak için olay işleyicisi <xref:System.Windows.Forms.OpenFileDialog> bir filtreyle yalnızca metin dosyaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f833-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="1f833-118">Kullanıcı bir metin dosyası seçer ve seçer sonra **Tamam**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyasını Not Defteri'nde açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f833-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="1f833-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f833-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="1f833-120">OpenFileDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="1f833-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
