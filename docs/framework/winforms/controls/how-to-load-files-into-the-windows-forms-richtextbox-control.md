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
ms.openlocfilehash: 1288d89bc9ffd729b59626b88fd2f3ca61c8669d
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053548"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="7e2eb-102">Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme</span><span class="sxs-lookup"><span data-stu-id="7e2eb-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="7e2eb-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, bir düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyasını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="7e2eb-104">Bunu yapmak için çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="7e2eb-105">Ayrıca <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi bir akıştan verileri yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="7e2eb-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="7e2eb-107">RichTextBox denetimine bir dosya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="7e2eb-107">To load a file into the RichTextBox control</span></span>  
  
1. <span data-ttu-id="7e2eb-108">Kullanılarak açılmasını dosyasının yolunu belirlemek <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="7e2eb-109">Genel bakış için bkz. [OpenFileDialog bileşenine genel bakış](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7e2eb-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="7e2eb-110">Çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> yüklenecek dosyanın ve isteğe bağlı olarak bir dosya türünü belirten denetimi.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="7e2eb-111">Aşağıdaki örnekte, yüklenecek dosyanın sınıfından alınmıştır <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="7e2eb-112">Bir dosya adı yalnızca bağımsız değişken olarak yöntemi çağırın, dosya türü RTF olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="7e2eb-113">Başka bir dosya türü belirtmek için bir değerini yöntemi çağırın <xref:System.Windows.Forms.RichTextBoxStreamType> ikinci bağımsız değişken olarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="7e2eb-114">Aşağıdaki örnekte <xref:System.Windows.Forms.OpenFileDialog> bileşeni, bir düğmeye tıklandığında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="7e2eb-115">Seçilen dosya sonra açıldı ve görüntülenen <xref:System.Windows.Forms.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="7e2eb-116">Bu örnek, bir formda bir düğme bulunur varsayar`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
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
  
     <span data-ttu-id="7e2eb-117">(Visual C#, Visual C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7e2eb-118">Bu işlemi çalıştırmak için derlemenizi ayrıcalık düzeyi verilen tarafından gerekli kılabiliriz <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7e2eb-119">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle özel bir durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="7e2eb-120">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="7e2eb-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2eb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e2eb-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="7e2eb-122">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="7e2eb-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="7e2eb-123">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="7e2eb-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
