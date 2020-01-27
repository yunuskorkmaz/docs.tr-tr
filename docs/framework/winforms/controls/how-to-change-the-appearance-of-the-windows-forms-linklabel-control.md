---
title: LinkLabel denetiminin görünümünü değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746624"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme
<xref:System.Windows.Forms.LinkLabel> denetimi tarafından görüntülenecek metni çeşitli amaçlarla değiştirebilirsiniz. Örneğin, metnin metin ile belirli bir renkte görünmesini sağlayarak metne tıklanabileceği kullanıcıya göstermek yaygın bir uygulamadır. Kullanıcı metne tıkladıktan sonra, renk farklı bir renge dönüşür. Bu davranışı denetlemek için, beş farklı özellik belirleyebilirsiniz: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>ve <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özellikleri.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Bir LinkLabel denetiminin görünüşünü değiştirmek için  
  
1. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> ve <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> özelliklerini istediğiniz renklere ayarlayın.  
  
     Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. <xref:System.Windows.Forms.LinkLabel.Text%2A> özelliğini uygun bir başlık olarak ayarlayın.  
  
     Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Başlığın hangi kısmının bağlantı olarak belirtileyeceğini öğrenmek için <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliğini ayarlayın.  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> değeri iki sayı içeren bir <xref:System.Windows.Forms.LinkArea> ile temsil edilir, başlangıç karakteri konumu ve karakter sayısı. Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> özelliğini <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>veya <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>olarak ayarlayın.  
  
     <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>olarak ayarlanırsa, başlığın <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> tarafından belirlenen bölümü yalnızca işaretçi üzerine getirildiğinde altı çizili olur.  
  
5. <xref:System.Windows.Forms.LinkLabel.LinkClicked> olay işleyicisinde, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliğini `true`olarak ayarlayın.  
  
     Bir bağlantı ziyaret edildiğinde, genellikle renge göre görünümünü bir şekilde değiştirmek yaygın bir uygulamadır. Metin, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> özelliği tarafından belirtilen renge değişecektir.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [LinkLabel Denetimine Genel Bakış](linklabel-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel Denetimi](linklabel-control-windows-forms.md)
