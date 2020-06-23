---
title: 'Nasıl yapılır: OpenFileDialog bileşeniyle dosya açma'
ms.date: 02/11/2019
description: Dosya tarama ve seçme için Windows iletişim kutusunu açmak üzere OpenFileDialog bileşenini nasıl kullanacağınızı öğrenin.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904435"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="49823-103">Nasıl yapılır: OpenFileDialog ile dosyaları açma</span><span class="sxs-lookup"><span data-stu-id="49823-103">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="49823-104"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>Bileşen, dosyalara gözatmak ve seçmek Için Windows iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="49823-104">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="49823-105">Seçili dosyaları açmak ve okumak için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> yöntemini kullanabilir veya sınıfının bir örneğini oluşturabilirsiniz <xref:System.IO.StreamReader?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="49823-105">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="49823-106">Aşağıdaki örneklerde her iki yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49823-106">The following examples show both approaches.</span></span>

<span data-ttu-id="49823-107">.NET Framework, özelliği almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> sınıfı tarafından verilen ayrıcalık düzeyi gereklidir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="49823-107">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="49823-108">Örnekler bir <xref:System.Security.Permissions.FileIOPermission> izin denetimi çalıştırır ve kısmi güven bağlamında çalıştırıldıysanız ayrıcalıkların yetersiz olması nedeniyle bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="49823-108">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="49823-109">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="49823-109">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="49823-110">Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamalar olarak oluşturabilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49823-110">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="49823-111">Daha fazla bilgi için, komut satırından csc.exeveya [derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) [ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="49823-111">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="49823-112">.NET Core 3,0 ile başlayarak, örnekleri .NET Core Windows Forms \* \<folder name> . csproj\* proje dosyası olan bir klasörden Windows .NET Core uygulamaları olarak oluşturup çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49823-112">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="49823-113">Örnek: StreamReader ile bir dosyayı akış olarak okuma</span><span class="sxs-lookup"><span data-stu-id="49823-113">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="49823-114">Aşağıdaki örnek, <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> yöntemi ile açmak için Windows Forms denetimin olay işleyicisini kullanır <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> .</span><span class="sxs-lookup"><span data-stu-id="49823-114">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="49823-115">Kullanıcı bir dosya seçtikten ve **Tamam**seçeneğini belirledikten sonra, sınıfın bir örneği <xref:System.IO.StreamReader> dosyayı okur ve formun metin kutusunda içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="49823-115">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="49823-116">Dosya akışlarından okuma hakkında daha fazla bilgi için bkz <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> . ve <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="49823-116">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="49823-117">Örnek: bir filtrelenmiş seçimden bir dosyayı OpenFile ile açma</span><span class="sxs-lookup"><span data-stu-id="49823-117">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="49823-118">Aşağıdaki örnek <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.OpenFileDialog> yalnızca metin dosyalarını gösteren bir filtre ile açmak için denetimin olay işleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="49823-118">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="49823-119">Kullanıcı bir metin dosyası seçtikten ve **Tamam**' ı seçerse, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dosyayı Not defteri 'nde açmak için yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49823-119">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="49823-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49823-120">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="49823-121">OpenFileDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="49823-121">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
