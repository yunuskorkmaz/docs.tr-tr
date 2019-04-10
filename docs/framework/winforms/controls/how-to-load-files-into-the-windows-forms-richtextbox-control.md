---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme'
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
ms.openlocfilehash: ffbce7401f068b3d0a7fee4fd8ba04c10cb6f6b7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340860"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="43b35-102">Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme</span><span class="sxs-lookup"><span data-stu-id="43b35-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="43b35-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, bir düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyasını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43b35-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="43b35-104">Bunu yapmak için çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="43b35-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="43b35-105">Ayrıca <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi bir akıştan verileri yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="43b35-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="43b35-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="43b35-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="43b35-107">RichTextBox denetimine bir dosya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="43b35-107">To load a file into the RichTextBox control</span></span>  
  
1. <span data-ttu-id="43b35-108">Kullanılarak açılmasını dosyasının yolunu belirlemek <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="43b35-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="43b35-109">Genel bakış için bkz. [OpenFileDialog bileşenine genel bakış](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="43b35-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="43b35-110">Çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> yüklenecek dosyanın ve isteğe bağlı olarak bir dosya türünü belirten denetimi.</span><span class="sxs-lookup"><span data-stu-id="43b35-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="43b35-111">Aşağıdaki örnekte, yüklenecek dosyanın sınıfından alınmıştır <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="43b35-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="43b35-112">Bir dosya adı yalnızca bağımsız değişken olarak yöntemi çağırın, dosya türü RTF olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="43b35-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="43b35-113">Başka bir dosya türü belirtmek için bir değerini yöntemi çağırın <xref:System.Windows.Forms.RichTextBoxStreamType> ikinci bağımsız değişken olarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="43b35-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="43b35-114">Aşağıdaki örnekte <xref:System.Windows.Forms.OpenFileDialog> bileşeni, bir düğmeye tıklandığında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="43b35-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="43b35-115">Seçilen dosya sonra açıldı ve görüntülenen <xref:System.Windows.Forms.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="43b35-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="43b35-116">Bu örnek, bir formda bir düğme bulunur varsayar`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="43b35-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
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
  
     <span data-ttu-id="43b35-117">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="43b35-117">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="43b35-118">Bu işlemi çalıştırmak için derlemenizi ayrıcalık düzeyi verilen tarafından gerekli kılabiliriz <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="43b35-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="43b35-119">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle özel bir durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="43b35-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="43b35-120">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="43b35-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b35-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43b35-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="43b35-122">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="43b35-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="43b35-123">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="43b35-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
