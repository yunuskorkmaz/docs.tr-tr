---
title: LinkLabel Denetimigörünümünü Değiştirme
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
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142136"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme
<xref:System.Windows.Forms.LinkLabel> Denetim tarafından görüntülenen metni çeşitli amaçlara uyacak şekilde değiştirebilirsiniz. Örneğin, metnin altı çizili belirli bir renkte görünmesi için metin ayarlayarak metnin tıklanabileceğini kullanıcıya belirtmek yaygın bir uygulamadır. Kullanıcı metni tıklattıktan sonra renk farklı bir renge dönüşür. Bu davranışı denetlemek için beş farklı özellik <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>ayarlayabilirsiniz: , , <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, ve <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özellikleri.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Bir LinkLabel denetiminin görünümünü değiştirmek için  
  
1. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> Ve <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> özellikleri istediğiniz renklere ayarlayın.  
  
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
  
2. <xref:System.Windows.Forms.LinkLabel.Text%2A> Özelliği uygun bir alt yazı yla ayarlayın.  
  
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
  
3. Alt <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> yazının hangi bölümünün bağlantı olarak gösterileceğini belirlemek için özelliği ayarlayın.  
  
     Değer, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> iki sayı, <xref:System.Windows.Forms.LinkArea> başlangıç karakter konumu ve karakter sayısı içeren bir ile gösterilir. Bu, **Özellikler** penceresinde programlı olarak veya tasarım zamanında yapılabilir.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> Özelliği <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>veya <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>Ayarlanırsa, alt yazının belirlediği <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bölüm yalnızca işaretçi üzerinde yse altı çizilir.  
  
5. Olay <xref:System.Windows.Forms.LinkLabel.LinkClicked> işleyicisi, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliği `true`' ye ayarla.  
  
     Bir bağlantı ziyaret edildiğinde, görünümünü genellikle renk olarak bir şekilde değiştirmek yaygın bir uygulamadır. <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> Metin, özellik tarafından belirtilen renge değişecektir.  
  
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
