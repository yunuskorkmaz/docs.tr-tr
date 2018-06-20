---
title: Windows Forms Uygulamalarında İki Yönlü Destek
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbe14e6c05fd6ef155b564e499157e00c5d809e5
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208475"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Windows Forms Uygulamalarında İki Yönlü Destek
Arapça ve İbranice gibi çift yönlü (sağdan sola) dilleri destekleyen Windows tabanlı uygulamalar oluşturmak için Visual Studio'yu kullanabilirsiniz. Bu standart formlar, iletişim kutuları, MDI formları ve birlikte çalışabilir tüm denetimler bu formlarda içerir — diğer bir deyişle, tüm nesneleri <xref:System.Windows.Forms.Control> ad alanı.  
  
## <a name="culture-support"></a>Kültür desteği  
 Kültür ve UI kültürü ayarlar tarih, saat, para birimi ve diğer bilgileri ile bir uygulamanın nasıl çalıştığını belirler. Diğer diller için olduğu gibi kültür ve UI kültürü desteği çift yönlü diller için aynıdır.   Ayrıca bkz. [genel Windows Formları ve Web formları için kültüre özgü sınıflar](http://msdn.microsoft.com/library/94ye9x8c\(v=vs.110\)) veya [genel Windows Formları ve Web formları için kültüre özgü sınıflar](http://msdn.microsoft.com/library/94ye9x8c\(v=vs.120\))  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft ve RightToLeftLayout özellikleri  
 Temel <xref:System.Windows.Forms.Control> içinden forms türetilmiş sınıf içeren bir <xref:System.Windows.Forms.Control.RightToLeft%2A> form ve denetimlerinin okuma sırasını değiştirmek için ayarlayabileceğiniz özelliği. Formun ayarlarsanız <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği, varsayılan denetimleri form üzerinde tarafından devral bu ayarı. Ancak, aynı zamanda ayarlayabileceğiniz <xref:System.Windows.Forms.Control.RightToLeft%2A> ayrı ayrı çoğu denetimlerinde özellik. Ayrıca bkz. [nasıl yapılır: Windows Forms Genelleştirme için görüntü sağdan sola metinde](http://msdn.microsoft.com/library/7d3337xw\(v=vs.110\)).  
  
 Etkisini <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği bir denetimden farklı diğerine. Bazı denetimler özelliği yalnızca okuma sırası olarak ayarlar <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ToolTip> kontrol eder. Diğer denetimlerinde <xref:System.Windows.Forms.Control.RightToLeft%2A> okuma düzeni ve Düzen özelliğini değiştirir. Bu içerir <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.CheckBox> kontrol eder. Diğer denetimleri gerektiren <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliği sağdan sola düzenini yansıtmak üzere uygulanabilir. Aşağıdaki tabloda Ayrıntılar üzerinde nasıl sağlar <xref:System.Windows.Forms.Control.RightToLeft%2A> ve <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özellikleri ayrı ayrı Windows Forms denetimleri etkiler.  
  
|Denetim/bileşeni|RightToLeft özelliği etkisi|RightToLeftLayout özelliğinin etkisi|Yansıtması gerekir?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Okuma sırası RTL ayarlar. Tersine çevirir <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, ve <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.CheckBox>|Onay kutusu metni sağ tarafında görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.CheckedListBox>|Tüm onay kutularını metnin sağ tarafında görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ColorDialog>|Etkilenen değil; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ComboBox>|Birleşik giriş kutusu denetimi öğelerde sağa hizalı|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ContextMenu>|Sağa hizalı okuma sırası RTL ile görünür|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.DataGrid>|Sağa hizalı okuma sırası RTL ile görünür|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.DataGridView>|Okuma sırası ve denetim düzeni hem RTL etkiler|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.DateTimePicker>|Etkilenen değil; işletim sisteminin diline bağlıdır|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.DomainUpDown>|Sola hizalar yukarı ve aşağı düğmeleri|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ErrorProvider>|Desteklenmez|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.FontDialog>|İşletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Form>|Okuma sırası RTL ayarlar ve scrollbars tersine çevirir|Formun yansıtır|Evet|  
|<xref:System.Windows.Forms.GroupBox>|Resim yazısı sağa hizalı görüntülenir. Alt denetimler, bu özellik devralır.|Kullanım bir <xref:System.Windows.Forms.TableLayoutPanel> sağdan sola yansıtması için Denetim içindeki desteği|Hayır|  
|<xref:System.Windows.Forms.HScrollBar>|Sağa hizalı kaydırma kutusunun (Flash) ile başlar|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ImageList>|Gerekli değil|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Label>|Sağa hizalı görüntülenir. Tersine çevirir <xref:System.Windows.Forms.Label.TextAlign%2A> ve <xref:System.Windows.Forms.Label.ImageAlign%2A>|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.LinkLabel>|Sağa hizalı görüntülenir. Tersine çevirir <xref:System.Windows.Forms.Label.TextAlign%2A> ve <xref:System.Windows.Forms.Label.ImageAlign%2A>|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ListBox>|Sağa hizalı öğeleri|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ListView>|Okuma sırasını RTL ayarlar; sola hizalı öğeleri kalır|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.MainMenu>|Sağa hizalı (değil tasarım zamanında) çalışma zamanında okuma sırası RTL görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.MaskedTextBox>|Sağdan sola metinden görüntüler.|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.MonthCalendar>|Etkilenen değil; işletim sisteminin diline bağlıdır|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.NotifyIcon>|Desteklenmez|Desteklenmez|Hayır|  
|<xref:System.Windows.Forms.NumericUpDown>|Yukarı ve aşağı düğmeleri sola hizalı|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.OpenFileDialog>|Sağdan sola işletim sistemlerinde içeren formun ayarı <xref:System.Windows.Forms.Control.RightToLeft> özelliğine <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> iletişim yerelletirilmesi |Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.PageSetupDialog>|Etkilenen değil; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Panel>|Alt denetimler bu özellik devral|Kullanım <xref:System.Windows.Forms.TableLayoutPanel> sağdan sola desteği için denetim içinde|Evet|  
|<xref:System.Windows.Forms.PictureBox>|Desteklenmez|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.PrintDialog>|Etkilenen değil; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Drawing.Printing.PrintDocument>|Sola hizalı hale dikey kaydırma çubuğu ve yatay kaydırma çubuğu soldan başlatır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Desteklenmez|Desteklenmez|Hayır|  
|<xref:System.Windows.Forms.ProgressBar>|Bu özellik tarafından etkilememek|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.RadioButton>|Radyo düğmesi metni sağ tarafında görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.RichTextBox>|Metin içeren denetim öğelerini sağdan sola okuma sırası RTL ile görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.SaveFileDialog>|Etkilenen değil; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.SplitContainer>|Paneli düzeni ters; Sol taraftaki dikey kaydırma çubuğu görüntülenir; Yatay kaydırma çubuğu sağdan başlatır|Kullanım bir <xref:System.Windows.Forms.TableLayoutPanel> yansıtma sipariş alt denetimler|Hayır|  
|<xref:System.Windows.Forms.Splitter>|Desteklenmez|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.StatusBar>|Desteklenmeyen; kullanmak <xref:System.Windows.Forms.StatusStrip> yerine|Herhangi bir etkisi; kullanmak <xref:System.Windows.Forms.StatusStrip> yerine|Hayır|  
|<xref:System.Windows.Forms.TabControl>|Bu özellik tarafından etkilenen değil|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.TextBox>|Sağdan sola metin okuma sırası RTL ile görüntüler|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Timer>|Gerekli değil|Gerekli değil|Hayır|  
|<xref:System.Windows.Forms.ToolBar>|Bu özellik tarafından etkilenen değil; kullanmak <xref:System.Windows.Forms.ToolStrip> yerine|Herhangi bir etkisi; kullanmak <xref:System.Windows.Forms.ToolStrip> yerine|Evet|  
|<xref:System.Windows.Forms.ToolTip>|Okuma sırası RTL ayarlar|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.TrackBar>|Sağa kaydırma veya iz başlatır; zaman <xref:System.Windows.Forms.TrackBar.Orientation%2A> çizgilerine sağdan ortaya, dikeydir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.TreeView>|Okuma düzenini yalnızca RTL ayarlar|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.UserControl>|Sol taraftaki dikey kaydırma çubuğu görüntülenir; Yatay kaydırma çubuğu Flash sağ tarafta sahiptir.|Doğrudan destek yok; kullanan bir <xref:System.Windows.Forms.TableLayoutPanel>|Hayır|  
|<xref:System.Windows.Forms.VScrollBar>|Kaydırılabilir denetimleri sağ tarafındaki yerine sol tarafında görüntülenir|Herhangi bir etkisi|Hayır|  
  
## <a name="encoding"></a>Kodlama  
 Windows Forms Unicode desteğini, çift yönlü uygulamalarınızı oluşturduğunuzda herhangi bir karakter içerebilir. Ancak, tüm Windows Forms denetimleri tüm platformlarda Unicode'u destekler. Daha fazla bilgi için bkz: [kodlama ve Windows Forms Genelleştirme](../../../../docs/framework/winforms/advanced/encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağdan sola okuma sırası metinle çizmek için. <xref:System.Drawing.Graphics.DrawString%2A> Metin çizmek için kullanılan yöntem destekleyen bir `StringFormat` ayarlamak için parametre <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> üyesi <xref:System.Drawing.StringFormatFlags> metin için başlangıç noktasını tersine çevirmek için numaralandırması.  
  
## <a name="common-dialog-boxes"></a>Ortak iletişim kutuları  
 Dosya Aç iletişim kutusu gibi sistem araçları Windows denetiminde olan. Bunlar, işletim sistemi dil öğeleri devralır. Doğru dil ayarlarını bir Windows sürümü kullanıyorsanız, bu iletişim kutularından çift yönlü dillerde düzgün çalışır.  
  
 Benzer şekilde, ileti kutuları işletim sistemi üzerinden gidin ve çift yönlü metin destekler. İleti kutusu düğmeleri başlıkları geçerli dil ayarı temel alır. Varsayılan olarak, ileti kutuları sağdan sola okuma sırası kullanmayın, ancak ileti kutuları görüntülendiğinde okuma sırasını değiştirmek için bir parametre belirtebilirsiniz.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, kaydırma çubukları ve ScrollableControl  
 Şu anda Windows Forms'ta türetilen tüm sınıflar engelleyen bir sınırlama yoktur <xref:System.Windows.Forms.ScrollableControl> düzgün şekilde davranan gelen olduğunda her ikisi de <xref:System.Windows.Forms.Control.RightToLeft%2A> etkinleştirilir ve <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ayarlanır <xref:System.Windows.Forms.RightToLeft.Yes>. Örneğin, bir denetim gibi yerleştirin diyelim ki <xref:System.Windows.Forms.Panel>— veya bir kapsayıcı sınıfını türetilmiş <xref:System.Windows.Forms.Panel> (gibi <xref:System.Windows.Forms.FlowLayoutPanel> veya <xref:System.Windows.Forms.TableLayoutPanel>) — formunuzda. Ayarlarsanız <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> kapsayıcıya üzerinde <xref:System.Windows.Forms.RightToLeft.Yes> ve ardından <xref:System.Windows.Forms.Control.Anchor%2A> özelliği bir veya daha çok kapsayıcıya içinde denetimleri <xref:System.Windows.Forms.AnchorStyles.Right>, herhangi bir zamanda hiçbir kaydırma çubuğu görüntülenir. Sınıfın türetildiği <xref:System.Windows.Forms.ScrollableControl> davranır gibi <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ayarlanan <xref:System.Windows.Forms.RightToLeft.No>.  
  
 Şu anda yerleştirmek için yalnızca geçici bir çözüm değildir <xref:System.Windows.Forms.ScrollableControl> iç <xref:System.Windows.Forms.ScrollableControl>. Örneğin, gerekirse <xref:System.Windows.Forms.TableLayoutPanel> bu durumda çalışmaya, içine yerleştirebilirsiniz bir <xref:System.Windows.Forms.Panel> denetleyin ve ayarlayın <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> üzerinde <xref:System.Windows.Forms.Panel> için <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Yansıtma  
 *Yansıtma* bunlar arasında sağdan sola akması kullanıcı Arabirimi öğeleri düzeni ters çevirme için başvuruyor. Yansıtılmış bir Windows formunda, örneğin, simge durumuna küçült, Ekranı Kapla ve Kapat düğmeleri görünür değil en sağdaki başlık çubuğunda en solundaki.  
  
 Bir form veya denetimin <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğine `true` çevirmelerinin okuma formu, ancak bu ayar öğelerin değil ters sırada sağdan sola olmasını düzeni — diğer bir deyişle, yansıtma neden olmaz. Örneğin, bu özelliği ayarlamak taşınmaz **simge durumuna küçült**, **Ekranı Kapla**, ve **Kapat** formun başlık çubuğuna formun sol tarafındaki düğmeleri. Benzer şekilde, bazı denetimleri gibi <xref:System.Windows.Forms.TreeView> denetlemek, Arapça veya İbranice için uygun olacak şekilde kendi görüntüsünü değiştirmek için yansıtma gerektirir. Bu denetimler ayarları tarafından yansıtabilirsiniz <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliği.  
  
 Aşağıdaki denetimleri yansıtılmış sürümlerini oluşturabilirsiniz:  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Bazı denetimler korumalıdır. Bu nedenle, bunları yeni bir denetim türetilemez. Bunlar <xref:System.Windows.Forms.ImageList> ve <xref:System.Windows.Forms.ProgressBar> kontrol eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

[ASP.NET Web uygulamaları için çift yönlü destek](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
[Windows Forms uygulamaları Genelleştirme](globalizing-windows-forms.md)
