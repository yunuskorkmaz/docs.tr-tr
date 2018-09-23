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
ms.openlocfilehash: b4c572e518c84dfb230ff26049369011d8d7aa70
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577815"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Windows Forms Uygulamalarında İki Yönlü Destek
Visual Studio, Arapça ve İbranice gibi çift yönlü (sağdan sola) dilleri destekleyen Windows tabanlı uygulamalar oluşturmak için kullanabilirsiniz. Bu formlarda bu standart formlar, iletişim kutuları, MDI formları ve birlikte çalışabilen tüm denetimler içerir — diğer bir deyişle, tüm nesneleri <xref:System.Windows.Forms.Control> ad alanı.  
  
## <a name="culture-support"></a>Kültür desteği  
 Tarih, saat, para birimi ve diğer bilgileri ile bir uygulamanın nasıl çalıştığını, kültür ve UI kültür ayarları belirleyin. Diğer diller için olduğu gibi kültür ve kullanıcı Arabirimi kültürünü desteği çift yönlü diller için aynıdır.   Ayrıca bkz: [genel Windows Formları ve Web formları için kültüre özgü sınıflar](https://msdn.microsoft.com/library/94ye9x8c\(v=vs.110\)) veya [genel Windows Formları ve Web formları için kültüre özgü sınıflar](https://msdn.microsoft.com/library/94ye9x8c\(v=vs.120\))  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft ve RightToLeftLayout özellikleri  
 Temel <xref:System.Windows.Forms.Control> forms türettiğiniz, sınıfı içeren bir <xref:System.Windows.Forms.Control.RightToLeft%2A> form denetimlerini ve okuma düzenini değiştirmek için ayarlayabileceğiniz özelliği. Formun ayarlarsanız <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği, varsayılan form üzerinde denetimleri tarafından devralınan bu ayarı. Ancak, aynı zamanda ayarlayabileceğiniz <xref:System.Windows.Forms.Control.RightToLeft%2A> çoğu denetimlerinde Tek tek özellik. Ayrıca bkz: [nasıl yapılır: Windows Forms Genelleştirme için görünen sağdan sola metin](https://msdn.microsoft.com/library/7d3337xw\(v=vs.110\)).  
  
 Etkisini <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği bir denetimden diğerine gösterebileceğini. Bazı denetimler özelliği yalnızca okuma düzeni olarak ayarlar <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ToolTip> kontrol eder. Diğer denetimlerde <xref:System.Windows.Forms.Control.RightToLeft%2A> okuma düzeni hem Düzen özelliğini değiştirir. Bu içerir <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.CheckBox> kontrol eder. Diğer denetimleri gerektiren <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliği, sağdan sola düzenini yansıtmak için uygulanabilir. Aşağıdaki tabloda Ayrıntılar üzerinde nasıl sağlar <xref:System.Windows.Forms.Control.RightToLeft%2A> ve <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özellikleri ayrı ayrı Windows Forms denetimlerini etkiler.  
  
|Denetim/bileşeni|RightToLeft özelliği etkisi|RightToLeftLayout özelliğin etkisi|Yansıtması gerekir?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Sağdan sola okuma düzeni ayarlar. Tersine <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, ve <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.CheckBox>|Onay kutusu metni sağ tarafta görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.CheckedListBox>|Tüm onay kutularının metnin sağ tarafında görüntülenir.|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ColorDialog>|Etkilenmeyen; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ComboBox>|Birleşik giriş kutusu denetimi öğeleri sağa hizalı|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ContextMenu>|Sağa hizalı sağdan sola okuma düzeni ile görünür.|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.DataGrid>|Sağa hizalı sağdan sola okuma düzeni ile görünür.|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.DataGridView>|Her iki sağdan sola okuma sırası ve denetim düzeni etkiler|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.DateTimePicker>|Etkilenmeyen; işletim sisteminin diline bağlıdır|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.DomainUpDown>|Sola hizalar yukarı ve aşağı düğmeleri|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ErrorProvider>|Desteklenmez|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.FontDialog>|İşletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Form>|Sağdan sola okuma düzeni ayarlar ve kaydırma çubukları tersine çevirir.|Form yansıtır|Evet|  
|<xref:System.Windows.Forms.GroupBox>|Sağa hizalı başlık görüntülenir. Alt denetimler, bu özellik devralabilir.|Kullanım bir <xref:System.Windows.Forms.TableLayoutPanel> denetiminde sağdan sola yansıtma için destek|Hayır|  
|<xref:System.Windows.Forms.HScrollBar>|Sağa hizalı kaydırma kutusunun (Flash) ile başlar|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ImageList>|Gerekli değil|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Label>|Sağa hizalı görüntülenir. Tersine <xref:System.Windows.Forms.Label.TextAlign%2A> ve <xref:System.Windows.Forms.Label.ImageAlign%2A>|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.LinkLabel>|Sağa hizalı görüntülenir. Tersine <xref:System.Windows.Forms.Label.TextAlign%2A> ve <xref:System.Windows.Forms.Label.ImageAlign%2A>|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ListBox>|Öğeleri sağa hizalı|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.ListView>|İçin sağdan sola okuma düzeni ayarlar; öğeleri sola hizalanmış haberdar olun.|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.MainMenu>|Sağa hizalı sağdan sola okuma düzeni (değil tasarım zamanında) çalışma zamanında görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.MaskedTextBox>|Sağdan sola metin görüntüler.|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.MonthCalendar>|Etkilenmeyen; işletim sisteminin diline bağlıdır|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.NotifyIcon>|Desteklenmez|Desteklenmez|Hayır|  
|<xref:System.Windows.Forms.NumericUpDown>|Yukarı ve aşağı düğmeleri sola hizalanmış|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.OpenFileDialog>|Sağdan sola işletim sistemlerinde içeren formun ayarlama <xref:System.Windows.Forms.Control.RightToLeft> özelliğini <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> yerelletirilmesi iletişim kutusu |Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.PageSetupDialog>|Etkilenmeyen; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Panel>|Bu özellik alt denetimler devralabilir|Kullanım <xref:System.Windows.Forms.TableLayoutPanel> denetiminde sağdan sola destek için|Evet|  
|<xref:System.Windows.Forms.PictureBox>|Desteklenmez|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.PrintDialog>|Etkilenmeyen; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Drawing.Printing.PrintDocument>|Dikey kaydırma çubuğunun sola hizalanmış haline gelir ve yatay kaydırma çubuğunun soldan başlatır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Desteklenmez|Desteklenmez|Hayır|  
|<xref:System.Windows.Forms.ProgressBar>|Bu özellik tarafından etkilemez.|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.RadioButton>|Radyo düğmesi metnin sağ tarafında görüntülenir.|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.RichTextBox>|Metin içeren denetim öğelerini sağdan sola okuma düzeni ile sağdan sola görüntülenir|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.SaveFileDialog>|Etkilenmeyen; işletim sisteminin diline bağlıdır|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.SplitContainer>|Panel düzenini ters; Sol taraftaki dikey kaydırma çubuğu görünür; Yatay kaydırma çubuğunun sağ taraftan başlatır|Kullanım bir <xref:System.Windows.Forms.TableLayoutPanel> için yansıtma düzenini alt denetimler|Hayır|  
|<xref:System.Windows.Forms.Splitter>|Desteklenmez|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.StatusBar>|Desteklenmeyen; kullanma <xref:System.Windows.Forms.StatusStrip> yerine|Etkisi yok; kullanma <xref:System.Windows.Forms.StatusStrip> yerine|Hayır|  
|<xref:System.Windows.Forms.TabControl>|Bu özellikten etkilenen değil|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.TextBox>|Sağdan sola okuma düzeni ile sağdan sola metin görüntüler|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.Timer>|Gerekli değil|Gerekli değil|Hayır|  
|<xref:System.Windows.Forms.ToolBar>|Bu özellikten etkilenen değil; kullanma <xref:System.Windows.Forms.ToolStrip> yerine|Etkisi yok; kullanma <xref:System.Windows.Forms.ToolStrip> yerine|Evet|  
|<xref:System.Windows.Forms.ToolTip>|Sağdan sola okuma düzenini ayarlar|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.TrackBar>|Sağa kaydırma veya izleme başlatır; zaman <xref:System.Windows.Forms.TrackBar.Orientation%2A> ticks sağ taraftan ortaya dikey olduğu|Herhangi bir etkisi|Hayır|  
|<xref:System.Windows.Forms.TreeView>|Sağdan sola okuma düzenini yalnızca ayarlar|Denetim yansıtır|Evet|  
|<xref:System.Windows.Forms.UserControl>|Sol taraftaki dikey kaydırma çubuğu görünür; Yatay kaydırma çubuğu sağ tarafta thumb sahiptir.|Doğrudan destek yok; kullanan bir <xref:System.Windows.Forms.TableLayoutPanel>|Hayır|  
|<xref:System.Windows.Forms.VScrollBar>|Sol tarafta kaydırılabilir denetimleri sağ tarafında yerine görüntülenir|Herhangi bir etkisi|Hayır|  
  
## <a name="encoding"></a>Kodlama  
 Windows Forms Unicode desteğini, çift yönlü uygulamalarınızı oluşturduğunuzda herhangi bir karakter içerebilir. Ancak, tüm Windows Forms denetimleri, tüm platformlarda Unicode'u destekler. Daha fazla bilgi için [kodlama ve Windows Forms Genelleştirme](../../../../docs/framework/winforms/advanced/encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağdan sola okuma düzeni ile metin çizin. <xref:System.Drawing.Graphics.DrawString%2A> Metin çizmek için kullanılan yöntemi destekleyen bir `StringFormat` ayarlamak için parametre <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> üyesi <xref:System.Drawing.StringFormatFlags> metin için başlangıç noktasını tersine çevirmek için sabit listesi.  
  
## <a name="common-dialog-boxes"></a>Ortak iletişim kutuları  
 Dosya Aç iletişim kutusu gibi sistem araçları Windows denetimi altında olan. Bunlar, işletim sistemi dil öğelerini devralır. Doğru dil ayarlarını bir Windows sürümü kullanıyorsanız, bu iletişim kutularından çift yönlü dillerde düzgün çalışacaktır.  
  
 Benzer şekilde, ileti kutuları, işletim sistemi üzerinden gidin ve çift yönlü metin desteği. İleti kutusu düğmeleri resim yazıları, geçerli dil ayarını temel alır. Varsayılan olarak, ileti kutularını sağdan sola okuma düzeni kullanmayın, ancak ileti kutusu görüntülendiğinde okuma düzenini değiştirmek için bir parametresini belirtebilir.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, kaydırma çubukları ve ScrollableControl  
 Şu anda Windows Forms'ta türetilmiş tüm sınıfları engelleyen bir sınırlama yoktur <xref:System.Windows.Forms.ScrollableControl> düzgün bir şekilde davranan gelen, her ikisi de <xref:System.Windows.Forms.Control.RightToLeft%2A> etkinleştirilir ve <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ayarlanır <xref:System.Windows.Forms.RightToLeft.Yes>. Örneğin, bir denetimi gibi yerleştirmek varsayalım <xref:System.Windows.Forms.Panel>— veya bir kapsayıcı sınıfını türetilen <xref:System.Windows.Forms.Panel> (gibi <xref:System.Windows.Forms.FlowLayoutPanel> veya <xref:System.Windows.Forms.TableLayoutPanel>) — formunuzdaki. Ayarlarsanız <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> kapsayıcıya üzerinde <xref:System.Windows.Forms.RightToLeft.Yes> ve ardından <xref:System.Windows.Forms.Control.Anchor%2A> özelliği bir veya daha fazla denetim için kapsayıcı içinde <xref:System.Windows.Forms.AnchorStyles.Right>, hiç olmadığı kadar hiçbir kaydırma çubuğu belirir. Türetilen sınıfın <xref:System.Windows.Forms.ScrollableControl> çalışır gibi <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ayarlanmasına <xref:System.Windows.Forms.RightToLeft.No>.  
  
 Tek geçici çözüm şu anda, iç içe olmaktır <xref:System.Windows.Forms.ScrollableControl> iç <xref:System.Windows.Forms.ScrollableControl>. Örneğin, gerekirse <xref:System.Windows.Forms.TableLayoutPanel> bu durumda çalışmaya, içine yerleştirebilirsiniz bir <xref:System.Windows.Forms.Panel> denetleyin ve ayarlayın <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> üzerinde <xref:System.Windows.Forms.Panel> için <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Yansıtma  
 *Yansıtma* böylece bunlar sağdan sola flow kullanıcı Arabirimi öğeleri düzenini ters ifade eder. Yansıtılmış bir Windows formunda, örnekte, simge durumuna küçült, Ekranı Kapla ve Kapat düğmeleri görünür değil en sağdaki başlık çubuğunda en soldaki.  
  
 Bir form veya denetim ayarı <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğini `true` çevirmelerinin okuma formu, ancak bu ayar öğelerin değil ters sırada sağdan sola düzen — diğer bir deyişle, yansıtma neden olmaz. Örneğin, bu özelliğin ayarlanması taşınmaz **simge durumuna küçült**, **Ekranı Kapla**, ve **Kapat** formun başlık çubuğu formun sol tarafındaki düğmeleri. Benzer şekilde, bazı denetimleri gibi <xref:System.Windows.Forms.TreeView> denetlemek, Arapça veya İbranice için uygun olacak şekilde kendi görünümünü değiştirmek için yansıtma gerektirir. Bu denetimler ayarları tarafından yansıtabilirsiniz <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliği.  
  
 Yansıtılmış sürümleri aşağıdaki denetimleri oluşturabilirsiniz:  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Bazı denetimler korumalıdır. Bu nedenle, yeni bir denetim bunlardan türetilemez. Bunlar <xref:System.Windows.Forms.ImageList> ve <xref:System.Windows.Forms.ProgressBar> kontrol eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

[ASP.NET Web uygulamaları için çift yönlü destek](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
[Windows Forms uygulamaları Genelleştirme](globalizing-windows-forms.md)
