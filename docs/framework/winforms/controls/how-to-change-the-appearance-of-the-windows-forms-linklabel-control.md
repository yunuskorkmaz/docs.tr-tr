---
title: 'Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme'
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
ms.openlocfilehash: e1bb0ecba6fd8ddf66c6debb90ef4dd94641a97e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531492"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme
Tarafından görüntülenen metni değiştirebilirsiniz <xref:System.Windows.Forms.LinkLabel> çeşitli amaçlarla uyacak şekilde denetim. Örneğin, kullanıcıya metin altı çizili olan belirli bir renk görünmesi metin ayarlayarak tıklanabilecek belirtmek yaygın bir uygulamadır. Metin kullanıcı sonra farklı bir renk rengi değişir. Bu davranışı denetlemek için beş farklı özellikleri ayarlayabilirsiniz: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, ve <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özellikleri.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>LinkLabel denetiminin görünümünü değiştirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> ve <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> istediğiniz renkleri özellikleri.  
  
     Bu ya da program aracılığıyla veya tasarım zamanında de yapılabilir **özellikleri** penceresi.  
  
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
  
2.  Ayarlama <xref:System.Windows.Forms.LinkLabel.Text%2A> uygun bir resim yazısı özelliğini.  
  
     Bu ya da program aracılığıyla veya tasarım zamanında de yapılabilir **özellikleri** penceresi.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Ayarlama <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> resim yazısını hangi parçası bir bağlantı gösterilir belirlemek için özellik.  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Değeri ile temsil edilir bir <xref:System.Windows.Forms.LinkArea> iki sayı, başlangıç karakteri konumunu ve karakter sayısını içeren. Bu ya da program aracılığıyla veya tasarım zamanında de yapılabilir **özellikleri** penceresi.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Ayarlama <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> özelliğine <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, veya <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Bu ayarlanırsa <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, tarafından belirlenen resim yazısı parçası <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> işaretçi üzerine getirildiğinde yalnızca altı çizili olacaktır.  
  
5.  İçinde <xref:System.Windows.Forms.LinkLabel.LinkClicked> olay işleyici ayarlamayı <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliğine `true`.  
  
     Bir bağlantıyı ziyaret edildiğinde görünümünü bazı şekilde genellikle renge göre değiştirmek yaygın bir uygulamadır. Metin tarafından belirtilen rengi değişir <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> özelliği.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [LinkLabel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [LinkLabel Denetimi](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
