---
title: 'İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: 4b2d968aff157ac83b21823d546c052e140607a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540270"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için ise, ' ı seçin.  
  
 Genellikle, bir program, çalışma zamanında dinamik olarak güncelleştir uygulama durumu veya başka bir kullanıcı etkileşimi değişikliklere göre durum çubuğu panellerinin içeriğini çağırır. Bu anahtarları CAPS LOCK, NUM LOCK veya SCROLL LOCK gibi etkinleştirilir kullanıcılar sinyal veya tarih veya saat kullanışlı bir başvuru olarak sağlamak için genel bir yoludur.  
  
 Aşağıdaki örnekte, bir örneğini kullanacağı <xref:System.Windows.Forms.StatusBarPanel> bir saat barındırmak için sınıf.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Durum çubuğu güncelleştirmek için hazır hale getirmek için  
  
1.  Yeni bir Windows form oluşturun.  
  
2.  Ekleme bir <xref:System.Windows.Forms.StatusBar> Formunuza denetim. Ayrıntılar için bkz [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Durum çubuğu paneline ekleyebilir, <xref:System.Windows.Forms.StatusBar> denetim. Ayrıntılar için bkz [nasıl yapılır: bir StatusBar denetimine paneller ekleme](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  İçin <xref:System.Windows.Forms.StatusBar> formunuza, eklediğiniz denetimini ayarlama <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `true`.  
  
5.  Windows Forms eklemek <xref:System.Windows.Forms.Timer> forma bileşen.  
  
    > [!NOTE]
    >  Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> bileşeni, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun bir süreölçer gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Ayarlama <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğine `true`.  
  
7.  Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> özelliği <xref:System.Windows.Forms.Timer> 30000 için.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği <xref:System.Windows.Forms.Timer> bileşen doğru zaman görüntülenen zaman yansıtılmasını sağlamak için 30 saniye (30.000 milisaniye) olarak ayarlanır.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Durum çubuğu güncelleştirmek için Zamanlayıcı uygulamak için  
  
1.  Olay işleyicisinin aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Timer> panelini güncelleştirmek için bileşen <xref:System.Windows.Forms.StatusBar> denetim.  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     Bu noktada, uygulamayı çalıştırın ve durum çubuğu Masası'nda çalışan saati gözlemlemek hazırsınız.  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Uygulamada hata ayıklama ve çalıştırmak için F5 tuşuna basın. Hata ayıklama hakkında daha fazla bilgi için bkz [Visual Studio'da hata ayıklamayı](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  Yaklaşık olarak 30 durum çubuğunda görünmesini saniye saat sürer. Bu olası en doğru zamanı elde etmektir. Buna karşılık, er görünür saati yapmak için değeri azaltabilir <xref:System.Windows.Forms.Timer.Interval%2A> ayarlanan önceki yordamdaki adım 7'deki özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [StatusBar Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
