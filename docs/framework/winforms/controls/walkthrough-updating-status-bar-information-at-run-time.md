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
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197106"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri yerini alır ve <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimlerine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur.  
  
 Genellikle, bir program, uygulama durumu veya diğer kullanıcı etkileşimlerine bağlı olarak durum çubuğu panellerinin içeriğini çalışma zamanında dinamik olarak güncelleştirmeniz için çağrı yapılır. Bu, Caps Lock, NUM LOCK veya SCROLL LOCK gibi anahtarların etkinleştirildiğini veya tarih ya da saatin uygun bir başvuru olarak sağlanması için kullanıcılara işaret etmenin yaygın bir yoludur.  
  
 Aşağıdaki örnekte, bir saati barındırmak için <xref:System.Windows.Forms.StatusBarPanel> sınıfının bir örneğini kullanacaksınız.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Durum çubuğunu güncelleştirmeye hazırlanıyor  
  
1. Yeni bir Windows formu oluşturun.  
  
2. Formunuza <xref:System.Windows.Forms.StatusBar> denetimi ekleyin. Ayrıntılar için bkz. [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).  
  
3. <xref:System.Windows.Forms.StatusBar> denetimine bir durum çubuğu paneli ekleyin. Ayrıntılar için bkz. [nasıl yapılır: bir StatusBar Denetimine Panel ekleme](how-to-add-panels-to-a-statusbar-control.md).  
  
4. Formunuza eklediğiniz <xref:System.Windows.Forms.StatusBar> denetimi için <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true`olarak ayarlayın.  
  
5. Forma bir Windows Forms <xref:System.Windows.Forms.Timer> bileşeni ekleyin.  
  
    > [!NOTE]
    > Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> bileşeni bir Windows Forms ortamı için tasarlanmıştır. Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`olarak ayarlayın.  
  
7. <xref:System.Windows.Forms.Timer> <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini 30000 olarak ayarlayın.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.Timer> bileşenin <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, görüntülenen sürede doğru saatin yansıtıldığından emin olmak için 30 saniye (30.000 milisaniye) olarak ayarlanır.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Durum çubuğunu güncelleştirmek üzere zamanlayıcıyı uygulamak için  
  
1. <xref:System.Windows.Forms.StatusBar> denetiminin panelini güncelleştirmek için <xref:System.Windows.Forms.Timer> bileşenin olay işleyicisine aşağıdaki kodu ekleyin.  
  
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
  
     Bu noktada, uygulamayı çalıştırmaya ve durum çubuğu panelinde çalışan saati gözlemlemeye hazırız.  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1. Uygulamada hata ayıklayın ve F5 tuşuna basarak çalıştırın. Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](/visualstudio/debugger/debugger-feature-tour).  
  
    > [!NOTE]
    > Durum çubuğunda saatin görünmesi yaklaşık olarak 30 saniye sürer. Bu, mümkün olan en doğru zamanı almak için kullanılır. Tersine, saatin daha önce görünmesi için, önceki yordamda 7. adımda ayarladığınız <xref:System.Windows.Forms.Timer.Interval%2A> özelliğinin değerini azaltabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme](how-to-add-panels-to-a-statusbar-control.md)
- [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
