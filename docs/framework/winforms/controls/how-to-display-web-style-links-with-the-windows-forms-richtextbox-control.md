---
title: RichTextBox denetimiyle Web stili bağlantıları görüntüleme
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
ms.openlocfilehash: 06ed304e566bb437a2353dd330d7de5328f2a729
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144831"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme

Windows Forms <xref:System.Windows.Forms.RichTextBox> Denetim, web bağlantılarını renkli ve altı çizili olarak gösterebilir. Bağlantı tıklandığında bağlantı metninde belirtilen Web sitesini gösteren tarayıcı penceresi açan bir kod yazabilirsiniz.

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>RichTextBox denetimiyle bir Web sayfasına bağlantı sağlamak için

1. <xref:System.Windows.Forms.RichTextBox.Text%2A>Özelliğini geçerli BIR URL (örneğin, "") içeren bir dizeye ayarlayın https://www.microsoft.com/ .

2. <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>Özelliğin (varsayılan) olarak ayarlandığından emin olun `true` .

3. Nesnenin yeni bir genel örneğini oluşturun <xref:System.Diagnostics.Process> .

4. <xref:System.Windows.Forms.RichTextBox.LinkClicked>Tarayıcıya istenen metni gönderen olay için bir olay işleyicisi yazın.

    Aşağıdaki örnekte, <xref:System.Windows.Forms.RichTextBox.LinkClicked> olay, bir Internet Explorer örneğini denetimin özelliğinde BELIRTILEN URL 'ye açar <xref:System.Windows.Forms.RichTextBox.Text%2A> <xref:System.Windows.Forms.RichTextBox> . Bu örnekte, bir denetimi olan bir form varsayılır <xref:System.Windows.Forms.RichTextBox> .

    > [!IMPORTANT]
    > <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>Yöntemi çağırırken, <xref:System.Security.SecurityException> yetersiz ayrıcalıklar nedeniyle kodu kısmi güven bağlamında çalıştırıyorsanız bir özel durumla karşılaşacaksınız. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

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

    (Visual C++) `p`Aşağıdaki deyiminizi formunuzun yapıcısına ekleyerek yapabileceğiniz işlemi başlatmalısınız:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (Visual C#, Visual C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.

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

    Üzerinde çalışmayı bitirdikten sonra oluşturduğunuz işlemi hemen durdurmak önemlidir. Yukarıda sunulan koda başvurarak, işlemi durdurmak için kodunuz şuna benzeyebilir:

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
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
