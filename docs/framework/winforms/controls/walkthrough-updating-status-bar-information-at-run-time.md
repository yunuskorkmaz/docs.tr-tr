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
ms.openlocfilehash: 7beae9bb886c7c79d4d97375887bfecb0c2a40c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792164"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.  
  
 Genellikle, bir program, çalışma zamanında dinamik olarak güncelleştirmek için uygulama durumunu veya başka bir kullanıcı etkileşimi değişikliklere göre durum çubuğu panellerinin içeriğini çağırır. Bu anahtarları CAPS LOCK, NUM LOCK veya SCROLL LOCK gibi etkinleştirildiğini kullanıcılar sinyal ya da tarih veya saat kullanışlı bir başvuru olarak sağlamak için ortak bir yoludur.  
  
 Aşağıdaki örnekte, bir örneğini kullanacağınız <xref:System.Windows.Forms.StatusBarPanel> saat barındırmak için sınıf.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Durum çubuğu güncelleştirmek için hazır hale getirmek için  
  
1. Yeni bir Windows formu oluşturun.  
  
2. Ekleme bir <xref:System.Windows.Forms.StatusBar> form denetimi. Ayrıntılar için bkz [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).  
  
3. Bir durum çubuğu paneline eklemek, <xref:System.Windows.Forms.StatusBar> denetimi. Ayrıntılar için bkz [nasıl yapılır: Bir StatusBar denetimine panel ekleme](how-to-add-panels-to-a-statusbar-control.md).  
  
4. İçin <xref:System.Windows.Forms.StatusBar> formunuza, eklediğiniz denetimi ayarlama <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true`.  
  
5. Bir Windows Forms ekleme <xref:System.Windows.Forms.Timer> forma bileşen.  
  
    > [!NOTE]
    >  Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> bileşeni, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Ayarlama <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true`.  
  
7. Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> özelliği <xref:System.Windows.Forms.Timer> 30000 için.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği <xref:System.Windows.Forms.Timer> bileşeni doğru bir zaman görüntülenen saat yansıtılmasını sağlamak üzere 30 saniye (30.000 milisaniye cinsinden) ayarlanır.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Durum çubuğunu güncellemek için Zamanlayıcıyı uygulamak için  
  
1. Olay işleyicisi aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Timer> panelini güncelleştirmek için bileşen <xref:System.Windows.Forms.StatusBar> denetimi.  
  
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
  
     Bu noktada, uygulamayı çalıştırmak ve durum çubuğu panelinde çalıştıran saat gözlemek hazır olursunuz.  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1. Uygulamada hata ayıklamak ve çalıştırmak için F5 tuşuna basın. Hata ayıklama hakkında daha fazla ayrıntı için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  Yaklaşık olarak 30 durum çubuğunda görüntülenecek saniye saat sürer. Olası en doğru zamanı elde etmek için budur. Buna karşılık, daha kısa süre içinde görünen saati hale getirmek için değerini azaltabilirsiniz <xref:System.Windows.Forms.Timer.Interval%2A> ayarlanan önceki yordamdaki adım 7'deki özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Nasıl yapılır: Bir StatusBar denetimine panel ekleme](how-to-add-panels-to-a-statusbar-control.md)
- [Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar Denetimine Genel Bakış](statusbar-control-overview-windows-forms.md)
