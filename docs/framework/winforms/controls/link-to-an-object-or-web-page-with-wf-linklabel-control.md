---
title: 'Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: cd9c53527429dfc3e7156c4023b52509452b96cd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046246"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama

Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimi, formunuzda Web stili bağlantılar oluşturmanıza olanak sağlar. Bağlantıya tıklandığında, bağlantının ziyaret edildiğini göstermek için rengini değiştirebilirsiniz. Rengi değiştirme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms LinkLabel denetiminin](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)görünümünü değiştirin.

## <a name="linking-to-another-form"></a>Başka bir forma bağlama

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>LinkLabel denetimiyle başka bir forma bağlamak için

1. <xref:System.Windows.Forms.LinkLabel.Text%2A> Özelliği uygun bir başlık olarak ayarlayın.

2. Başlığın hangi kısmının bağlantı olarak belirtileyeceğini belirleyen özelliğiayarlayın.<xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Nasıl belirtildiği, bağlantı etiketinin görünümle ilgili özelliklerine bağlıdır. Değer iki sayı içeren bir <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> nesne tarafından temsil edilir, başlangıç karakterinin konumunu ve karakter sayısını. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Özelliği Özellikler penceresi veya kod içinde aşağıdakine benzer bir şekilde ayarlanabilir:

    ```vb
    ' In this code example, the link area has been set to begin
    ' at the first character and extend for eight characters.
    ' You may need to modify this based on the text entered in Step 1.
    LinkLabel1.LinkArea = New LinkArea(0, 8)
    ```

    ```csharp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1.LinkArea = new LinkArea(0,8);
    ```

    ```cpp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1->LinkArea = LinkArea(0,8);
    ```

3. Olay işleyicisinde, <xref:System.Windows.Forms.Form.Show%2A> `true` projedebaşkabirformaçmakiçinyönteminiçağırınveözelliğiniolarakayarlayın.<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> <xref:System.Windows.Forms.LinkLabel.LinkClicked>

    > [!NOTE]
    > <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> Sınıfının bir örneği tıklanan <xref:System.Windows.Forms.LinkLabel> denetime bir başvuru taşır, bu nedenle `sender` nesneyi atama gerekmez.

    ```vb
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       ' Show another form.
       Dim f2 As New Form()
       f2.Show
       LinkLabel1.LinkVisited = True
    End Sub
    ```

    ```csharp
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       // Show another form.
       Form f2 = new Form();
       f2.Show();
       linkLabel1.LinkVisited = true;
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          // Show another form.
          Form ^ f2 = new Form();
          f2->Show();
          linkLabel1->LinkVisited = true;
       }
    ```

## <a name="linking-to-a-web-page"></a>Bir Web sayfasına bağlanma

<xref:System.Windows.Forms.LinkLabel> Denetim, varsayılan tarayıcıyla bir Web sayfası göstermek için de kullanılabilir.

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Internet Explorer 'ı başlatmak ve LinkLabel denetimiyle bir Web sayfasına bağlantı sağlamak için

1. <xref:System.Windows.Forms.LinkLabel.Text%2A> Özelliği uygun bir başlık olarak ayarlayın.

2. Başlığın hangi kısmının bağlantı olarak belirtileyeceğini belirleyen özelliğiayarlayın.<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>

3. Olay işleyicisinde, bir özel durum işleme bloğunun ortasında <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> , <xref:System.Diagnostics.Process.Start%2A> özelliğini olarak `true` ayarlayan ikinci bir yordam çağırın ve varsayılan tarayıcıyı bir URL ile başlatmak için yöntemini kullanır. <xref:System.Windows.Forms.LinkLabel.LinkClicked> <xref:System.Diagnostics.Process.Start%2A> Yöntemi kullanmak için, <xref:System.Diagnostics?displayProperty=nameWithType> ad alanına bir başvuru eklemeniz gerekir.

    > [!IMPORTANT]
    > Aşağıdaki kod, kısmi güven ortamında (örneğin, paylaşılan bir sürücüde) çalışıyorsa, `VisitLink` yöntemi çağrıldığında JIT derleyicisi başarısız olur. İfade `System.Diagnostics.Process.Start` , başarısız olan bir bağlantı talebine neden olur. `VisitLink` Yöntemi çağrıldığında özel durum yakalanarak, aşağıdaki kod JIT derleyicisi başarısız olursa hatanın düzgün şekilde işleneceğini sağlar.

    ```vb
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       Try
          VisitLink()
       Catch ex As Exception
          ' The error message
          MessageBox.Show("Unable to open link that was clicked.")
       End Try
    End Sub

    Sub VisitLink()
       ' Change the color of the link text by setting LinkVisited
       ' to True.
       LinkLabel1.LinkVisited = True
       ' Call the Process.Start method to open the default browser
       ' with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com")
    End Sub
    ```

    ```csharp
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       try
       {
          VisitLink();
       }
       catch (Exception ex )
       {
          MessageBox.Show("Unable to open link that was clicked.");
       }
    }

    private void VisitLink()
    {
       // Change the color of the link text by setting LinkVisited
       // to true.
       linkLabel1.LinkVisited = true;
       //Call the Process.Start method to open the default browser
       //with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com");
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          try
          {
             VisitLink();
          }
          catch (Exception ^ ex)
          {
             MessageBox::Show("Unable to open link that was clicked.");
          }
       }
    private:
       void VisitLink()
       {
          // Change the color of the link text by setting LinkVisited
          // to true.
          linkLabel1->LinkVisited = true;
          // Call the Process.Start method to open the default browser
          // with a URL:
          System::Diagnostics::Process::Start("http://www.microsoft.com");
       }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [LinkLabel Denetimine Genel Bakış](linklabel-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms LinkLabel denetiminin görünümünü değiştirme](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel Denetimi](linklabel-control-windows-forms.md)
