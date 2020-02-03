---
title: RichTextBox denetimine dosya yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736291"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="01d0a-102">Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme</span><span class="sxs-lookup"><span data-stu-id="01d0a-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="01d0a-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyası görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="01d0a-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="01d0a-104">Bunu yapmak için <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="01d0a-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="01d0a-105">Bir akıştan veri yüklemek için <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d0a-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="01d0a-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="01d0a-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="01d0a-107">RichTextBox denetimine bir dosya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="01d0a-107">To load a file into the RichTextBox control</span></span>

1. <span data-ttu-id="01d0a-108"><xref:System.Windows.Forms.OpenFileDialog> bileşeni kullanılarak açılacak dosyanın yolunu saptayın.</span><span class="sxs-lookup"><span data-stu-id="01d0a-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="01d0a-109">Genel bakış için bkz. [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="01d0a-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="01d0a-110">Yüklenecek dosyayı ve isteğe bağlı olarak bir dosya türünü belirterek <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="01d0a-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="01d0a-111">Aşağıdaki örnekte, yüklenecek dosya <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliğinden alınır.</span><span class="sxs-lookup"><span data-stu-id="01d0a-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="01d0a-112">Yöntemini tek bağımsız değişkeni olarak bir dosya adı ile çağırırsanız, dosya türünün RTF olacağı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="01d0a-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="01d0a-113">Başka bir dosya türü belirtmek için, ikinci bağımsız değişkeni olarak <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması değeri ile yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="01d0a-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="01d0a-114">Aşağıdaki örnekte, bir düğmeye tıklandığında <xref:System.Windows.Forms.OpenFileDialog> bileşeni gösterilir.</span><span class="sxs-lookup"><span data-stu-id="01d0a-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="01d0a-115">Seçili dosya daha sonra açılır ve <xref:System.Windows.Forms.RichTextBox> denetiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="01d0a-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="01d0a-116">Bu örnekte, bir formun bir düğme olduğunu varsayar`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="01d0a-116">This example assumes a form has a button,`btnOpenFile`.</span></span>

    ```vb
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _
       ByVal e As System.EventArgs) Handles btnOpenFile.Click
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _
              RichTextBoxStreamType.RichText)
          End If
    End Sub
    ```

    ```csharp
    private void btnOpenFile_Click(object sender, System.EventArgs e)
    {
       if(openFileDialog1.ShowDialog() == DialogResult.OK)
       {
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);
       }
    }
    ```

    ```cpp
    private:
       void btnOpenFile_Click(System::Object ^  sender,
          System::EventArgs ^  e)
       {
          if(openFileDialog1->ShowDialog() == DialogResult::OK)
          {
             richTextBox1->LoadFile(openFileDialog1->FileName,
                RichTextBoxStreamType::RichText);
          }
       }
    ```

    <span data-ttu-id="01d0a-117">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="01d0a-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="01d0a-118">Bu işlemi çalıştırmak için, derlemeniz <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı tarafından verilen bir ayrıcalık düzeyi gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="01d0a-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="01d0a-119">Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="01d0a-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="01d0a-120">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="01d0a-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01d0a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01d0a-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="01d0a-122">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="01d0a-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="01d0a-123">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="01d0a-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
