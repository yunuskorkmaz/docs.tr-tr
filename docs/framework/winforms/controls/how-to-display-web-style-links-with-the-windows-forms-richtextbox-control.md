---
title: 'Nasıl yapılır: Windows Forms RichTextBox denetimi ile Web stili bağlantılar görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 64a2c8d9a9f6b8a7271a659b80ca2a63c423b3bc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718534"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox denetimi ile Web stili bağlantılar görüntüleme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, Web bağlantıları görüntüleyebilir, renkli ve altı çizili olarak. Bağlantıya tıklandığında bağlantı metni belirtilen Web sitesi gösteren bir tarayıcı penceresi açılır kod yazabilirsiniz.  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>RichTextBox denetimi ile bir Web sayfasına bağlantı için  
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliğine geçerli bir URL içeren bir dize (örneğin, "http://www.microsoft.com/").  
  
2.  Emin <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> özelliği `true` (varsayılan).  
  
3.  Genel yeni bir örneğini oluşturma <xref:System.Diagnostics.Process> nesne.  
  
4.  Bir olay işleyicisi için yazma <xref:System.Windows.Forms.RichTextBox.LinkClicked> tarayıcı istediğiniz metni gönderen olay.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.RichTextBox.LinkClicked> olay bir örneğini belirtilen URL'ye Internet Explorer açılır <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimi. Bu örnek bir formla varsayar bir <xref:System.Windows.Forms.RichTextBox> denetimi.  
  
    > [!IMPORTANT]
    >  İçinde arama <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> yöntemi karşılaşırsınız bir <xref:System.Security.SecurityException> yetersiz ayrıcalıklar nedeniyle bir kısmi güven bağlamında kod çalıştırıyorsanız, özel durum. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) İşlemi başlatmalısınız `p`, formunuzu oluşturucuda aşağıdaki deyim ekleyerek yapabilirsiniz:  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     Hemen çalışmaya tamamladıktan sonra oluşturduğunuz işlemi durdurmak önemlidir. Yukarıda gösterilen koda başvuran, işlemi durdurmak için kodunuzda şuna benzeyebilir:  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
