---
title: 'Nasıl yapılır: Bir nesneye bağlayın veya Web sayfası Windows Forms LinkLabel denetimi ile'
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
ms.openlocfilehash: fd397f9a6462ad9da06b1cc258a51b3cccf5d21c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628454"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Nasıl yapılır: Bir nesneye bağlayın veya Web sayfası Windows Forms LinkLabel denetimi ile
Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimi formunuzda Web stili bağlantılar oluşturmanızı sağlar. Bağlantıya tıklandığında bağlantı ziyaret belirtmek için rengini değiştirebilirsiniz. Rengi değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms LinkLabel denetiminin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## <a name="linking-to-another-form"></a>Başka bir forma bağlama  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>LinkLabel denetimi ile başka bir form bağlamak için  
  
1.  Ayarlama <xref:System.Windows.Forms.LinkLabel.Text%2A> özelliğini uygun bir açıklamalı alt yazı.  
  
2.  Ayarlama <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> hangi kısmını açıklamalı alt yazı bir bağlantı gösterilir belirlemek için özellik. Nasıl gösterilen bağlantı etiketi, görünüm ilgili özelliklerine bağlıdır. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Değeri tarafından temsil edilen bir <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> iki sayı, başlangıç karakteri konumunu ve karakter sayısını içeren bir nesne. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Özelliği, Özellikler penceresinde veya kodu aşağıdakine benzer bir şekilde ayarlanabilir:  
  
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
  
3.  İçinde <xref:System.Windows.Forms.LinkLabel.LinkClicked> olay işleyicisi çağırma <xref:System.Windows.Forms.Form.Show%2A> projede başka bir formu açın ve ayarlamak için yöntem <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliğini `true`.  
  
    > [!NOTE]
    >  Örneği <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> sınıfı taşıyan bir başvuru <xref:System.Windows.Forms.LinkLabel> cast gerekmez. Bu nedenle, tıklandığını denetimi `sender` nesne.  
  
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
  
## <a name="linking-to-a-web-page"></a>Bir Web sayfasına bağlama  
 <xref:System.Windows.Forms.LinkLabel> Denetim da varsayılan tarayıcı ile bir Web sayfasını görüntülemek için kullanılabilir.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>LinkLabel denetimi ile Internet Explorer ve bir Web sayfasına bağlantı başlatmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.LinkLabel.Text%2A> özelliğini uygun bir açıklamalı alt yazı.  
  
2.  Ayarlama <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> hangi kısmını açıklamalı alt yazı bir bağlantı gösterilir belirlemek için özellik.  
  
3.  İçinde <xref:System.Windows.Forms.LinkLabel.LinkClicked> olay işleyicisi, bir özel durum işleme bloğu ortasında ayarlar ikinci bir yordam çağırma <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliğini `true` ve kullandığı <xref:System.Diagnostics.Process.Start%2A> bir URL ile varsayılan tarayıcı başlatmak için yöntemi. Kullanılacak <xref:System.Diagnostics.Process.Start%2A> bir başvuru eklemeniz gereken yöntemini <xref:System.Diagnostics?displayProperty=nameWithType> ad alanı.  
  
    > [!IMPORTANT]
    >  Aşağıdaki kodu kısmi güven ortamında çalıştırırsanız (gibi paylaşılan bir sürücüde), JIT derleyicisi başarısız olur `VisitLink` yöntemi çağrılır. `System.Diagnostics.Process.Start` Deyimi, başarısız bir bağlantı talebi neden olur. İstisnayı tarafından zaman `VisitLink` yöntemi çağrıldığında, aşağıdaki kod, JIT derleyicisi başarısız olursa hata düzgün bir şekilde işlenmesini sağlar.  
  
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
- [LinkLabel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms LinkLabel denetiminin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel Denetimi](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
