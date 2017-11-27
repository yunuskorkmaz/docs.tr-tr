---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0e2aec42fa3656b64140134efa27fe8e940e1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="62527-102">Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme</span><span class="sxs-lookup"><span data-stu-id="62527-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="62527-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetim düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyasını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62527-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="62527-104">Bunu yapmak için arama <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="62527-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="62527-105">Aynı zamanda <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> bir akışından veri yükleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="62527-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="62527-106">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="62527-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="62527-107">RichTextBox denetimine bir dosya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="62527-107">To load a file into the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="62527-108">Kullanılarak açılması için dosyanın yolunu belirlemek <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="62527-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="62527-109">Genel bir bakış için bkz: [OpenFileDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="62527-109">For an overview, see [OpenFileDialog Component Overview](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="62527-110">Çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> denetim, yüklemek için dosya ve isteğe bağlı olarak bir dosya türünü belirtme.</span><span class="sxs-lookup"><span data-stu-id="62527-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="62527-111">Aşağıdaki örnekte, yük dosyaya alınırlar <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="62527-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="62527-112">Yalnızca bağımsız değişkeni olarak bir dosya adıyla yöntemini çağırırsanız, dosya türü RTF olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="62527-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="62527-113">Başka bir dosya türü belirtmek için değerini yöntemi çağırma <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması ikinci bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="62527-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="62527-114">Aşağıdaki örnekte <xref:System.Windows.Forms.OpenFileDialog> bileşen bir düğme tıklatıldığında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="62527-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="62527-115">Seçilen dosya sonra açılır ve görüntülenen <xref:System.Windows.Forms.RichTextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="62527-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="62527-116">Bu örnek bir biçime sahip bir düğme varsayar`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="62527-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
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
  
     <span data-ttu-id="62527-117">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="62527-117">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="62527-118">Bu işlem çalıştırmayı derlemenizi ayrıcalık düzeyi verilen tarafından gerektirebilir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62527-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="62527-119">Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="62527-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="62527-120">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="62527-120">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62527-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62527-121">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="62527-122">RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="62527-122">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="62527-123">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="62527-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
