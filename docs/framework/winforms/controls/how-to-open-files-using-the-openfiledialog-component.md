---
title: 'Nasıl açılır: OpenFileDialog bileşeni ile dosyaları açın'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182126"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="2799e-102">Nasıl yapılı: OpenFileDialog ile dosyaları açın</span><span class="sxs-lookup"><span data-stu-id="2799e-102">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="2799e-103">Bileşen, <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> dosyaları tarama ve seçmek için Windows iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="2799e-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="2799e-104">Seçili dosyaları açıp okumak için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> yöntemi kullanabilir veya sınıfın bir <xref:System.IO.StreamReader?displayProperty=nameWithType> örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2799e-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2799e-105">Aşağıdaki örnekler her iki yaklaşımı da göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2799e-105">The following examples show both approaches.</span></span>

<span data-ttu-id="2799e-106">.NET Framework'de, <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği almak veya ayarlamak için <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2799e-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2799e-107">Örnekler bir <xref:System.Security.Permissions.FileIOPermission> izin denetimi çalıştırın ve kısmi güven bağlamında çalıştırılırsa yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="2799e-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="2799e-108">Daha fazla bilgi için [Kod erişim güvenlik temellerine](../../misc/code-access-security-basics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2799e-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="2799e-109">Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamaları olarak oluşturabilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2799e-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="2799e-110">Daha fazla bilgi için [csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [Build komut satırına](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)sahip Command-line binasına bakın.</span><span class="sxs-lookup"><span data-stu-id="2799e-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="2799e-111">.NET Core 3.0 ile başlayarak, .NET Core Windows Forms \* \<klasör adı>.csproj\* proje dosyasına sahip bir klasörden windows .NET Core uygulamaları olarak örnekler oluşturabilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2799e-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="2799e-112">Örnek: Bir dosyayı StreamReader ile akış olarak okuyun</span><span class="sxs-lookup"><span data-stu-id="2799e-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="2799e-113"><xref:System.Windows.Forms.Button> Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.OpenFileDialog> yöntemle açmak için Windows Forms denetiminin olay işleyicisi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="2799e-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="2799e-114">Kullanıcı bir dosya yı seçip **Tamam'ı**seçtikten sonra sınıfın bir örneği dosyayı <xref:System.IO.StreamReader> okur ve içeriğini formun metin kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2799e-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="2799e-115">Dosya akışlarından okuma hakkında daha <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> fazla <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="2799e-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="2799e-116">Örnek: OpenFile ile filtre uygulanmış bir seçimden dosya açma</span><span class="sxs-lookup"><span data-stu-id="2799e-116">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="2799e-117">Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> yalnızca <xref:System.Windows.Forms.Control.Click> metin dosyalarını gösteren <xref:System.Windows.Forms.OpenFileDialog> bir filtreyi açmak için denetimin olay işleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2799e-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="2799e-118">Kullanıcı bir metin dosyası seçtikten ve **Tamam'ı**seçtikten sonra, dosyayı <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Not Defteri'nde açmak için yöntem kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2799e-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="2799e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2799e-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="2799e-120">OpenFileDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="2799e-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
