---
title: 'Nasıl yapılır: Açılır Yardımı Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: 5751bcdb9fe7a16138680f34a4fcc1760f85a1d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523880"
---
# <a name="how-to-display-pop-up-help"></a>Nasıl yapılır: Açılır Yardımı Görüntüleme
Windows Forms'ta Yardım görüntülemek için bir yol olduğu aracılığıyla **yardımcı** üzerinden erişilebilir başlık çubuğunu sağ tarafında bulunan düğmesini <xref:System.Windows.Forms.Form.HelpButton%2A> özelliği. Bu Yardım görüntüleme iletişim kutuları ile kullanmak için oldukça uygun türüdür. Kalıcı olarak gösterilen iletişim kutuları (ile <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi) kalıcı iletişim kutuları için başka bir pencere odak kaydırabilirsiniz önce kapatılması gerektiğinden dış yardım sistemleri hale getirme konusunda sorun yaşıyor. Ayrıca, kullanarak **yardımcı** düğmesi gerektiren olduğunu hiçbir **simge durumuna küçült** düğmesini veya **Ekranı Kapla** başlık çubuğunda gösterilen düğmesi. Formlar genellikle sahip bir standart iletişim kutusu kuralı ise **simge durumuna küçült** ve **Ekranı Kapla** düğmeler.  
  
 Ayrıca kullanabileceğinizi unutmayın <xref:System.Windows.Forms.HelpProvider> denetimleri açılır Yardım uyguladık olsa bile bir Yardım sisteminde dosyalara bağlamak için bileşen. Daha fazla bilgi için bkz: [bir Windows uygulamasında Yardım sağlama](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-pop-up-help"></a>Açılır Yardım görüntülemek için  
  
1.  Sürükleme bir [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) formunuza araç bileşen.  
  
     Windows Forms Tasarımcısı'nın altındaki tepsisinde sit.  
  
2.  Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.HelpButton%2A> özelliğine `true`. Bu düğme bir soru işaretiyle içinde formun başlık çubuğunu sağ tarafta görüntüler.  
  
3.  Sırayla <xref:System.Windows.Forms.Form.HelpButton%2A> görüntülemek için formun <xref:System.Windows.Forms.Form.MinimizeBox%2A> ve <xref:System.Windows.Forms.Form.MaximizeBox%2A> özellikleri ayarlanmalıdır `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> özelliğini `true`ve <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini aşağıdaki değerlerden birine: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> veya <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Yardım'ı formunuzda göstermek ve Özellikler penceresinde Yardım dizesi ayarlamak istediğiniz denetimi seçin. Benzer şekilde bir penceresinde görüntülenen metin dizesidir bir [araç ipucu](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).  
  
5.  Tuşuna **F5**.  
  
6.  Tuşuna **yardımcı** düğmesini başlık çubuğunda ve Yardım dizesi ayarladığınız denetim'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ToolTips Kullanarak Denetim Yardımı](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Windows Forms'ta Kullanıcı Yardımını Tümleştirme](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
