---
title: Windows Forms Uygulamalarında İki Yönlü Destek
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
ms.openlocfilehash: 3bf90636bf1fc4b20b23c61fdd90033b3da35ddd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141191"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Windows Forms Uygulamalarında İki Yönlü Destek
Visual Studio 'Yu, Arapça ve Ibranice gibi çift yönlü (sağdan sola) dilleri destekleyen Windows tabanlı uygulamalar oluşturmak için kullanabilirsiniz. Bu, standart formları, iletişim kutularını, MDI formlarını ve bu formlarda (<xref:System.Windows.Forms.Control> ad alanındaki tüm nesneler) birlikte çalışarak kullanabileceğiniz tüm denetimleri içerir.

## <a name="culture-support"></a>Kültür desteği
 Kültür ve UI kültürü ayarları bir uygulamanın tarihler, saatler, para birimi ve diğer bilgilerle nasıl çalıştığını belirleme. Kültür ve UI kültürü desteği, diğer dillerin yanı sıra iki yönlü diller için de aynıdır. Daha fazla bilgi için bkz. [Genel Windows formları ve Web formları Için kültüre özgü sınıflar](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).

## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft ve RightToLeftLayout özellikleri
 Form türettikleri temel <xref:System.Windows.Forms.Control> sınıfı, bir formun ve denetimlerin okuma düzenini değiştirmek için ayarlayabileceğiniz bir <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği içerir. Formun <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğini ayarlarsanız, formdaki varsayılan denetimler bu ayarı devralınır. Ancak, <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğini birçok denetim üzerinde ayrı ayrı de ayarlayabilirsiniz. Ayrıca bkz. [nasıl yapılır: Genelleştirme için Windows Forms Içinde sağdan sola metin görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).

 <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğinin etkisi bir denetimden diğerine farklılık gösterebilir. Bazı denetimlerde özelliği, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> ve <xref:System.Windows.Forms.ToolTip> denetimlerinde olduğu gibi yalnızca okuma sırasını ayarlar. Diğer denetimlerde <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği hem okuma düzenini hem de düzeni değiştirir. Buna <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.CheckBox> denetimleri dahildir. Diğer denetimler, düzeni sağdan sola yansıtmak için <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliğinin uygulanmasını gerektirir. Aşağıdaki tabloda <xref:System.Windows.Forms.Control.RightToLeft%2A> ve <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliklerinin tek Windows Forms denetimleri nasıl etkilediği hakkında ayrıntılı bilgi verilmektedir.

|Denetim/bileşen|RightToLeft özelliğinin etkisi|RightToLeftLayout özelliğinin etkisi|Yansıtma gerekiyor mu?|
|------------------------|------------------------------------|------------------------------------------|-------------------------|
|<xref:System.Windows.Forms.Button>|RTL okuma sırasını ayarlar. <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>ve <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A> tersine çevirir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.CheckBox>|Onay kutusu, metnin sağ tarafında görüntülenir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.CheckedListBox>|Tüm onay kutuları, metnin sağ tarafında görüntülenir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ColorDialog>|Etkilenmemiştir; işletim sisteminin diline bağlıdır|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ComboBox>|Birleşik giriş kutusu denetimindeki öğeler sağa hizalı|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ContextMenu>|Sağdan sola okuma düzeni ile sağa hizalı görüntülenir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.DataGrid>|Sağdan sola okuma düzeni ile sağa hizalı görüntülenir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.DataGridView>|Hem RTL okuma sırası hem de denetim düzenini etkiler|Efekt yok|Hayır|
|<xref:System.Windows.Forms.DateTimePicker>|Etkilenmemiştir; işletim sisteminin diline bağlıdır|Denetimi yansıtır|Evet|
|<xref:System.Windows.Forms.DomainUpDown>|Yukarı ve aşağı düğmeleri sola hizalar|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ErrorProvider>|Desteklenmez|Efekt yok|Hayır|
|<xref:System.Windows.Forms.FontDialog>|İşletim sisteminin diline bağlıdır|Efekt yok|Hayır|
|<xref:System.Windows.Forms.Form>|RTL okuma düzenini ayarlar ve kaydırma çubuklarını ters çevirir|Formu yansıtır|Evet|
|<xref:System.Windows.Forms.GroupBox>|Başlık sağa hizalı görüntülenir. Alt denetimler bu özelliği devralınabilir.|Sağdan sola yansıtma desteği için denetim içindeki bir <xref:System.Windows.Forms.TableLayoutPanel> kullanın|Hayır|
|<xref:System.Windows.Forms.HScrollBar>|Kaydırma kutusuyla başlar (Thumb) sağa hizalı|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ImageList>|Gerekli değil|Efekt yok|Hayır|
|<xref:System.Windows.Forms.Label>|Sağa hizalı olarak görüntülendi. <xref:System.Windows.Forms.Label.TextAlign%2A> ve <xref:System.Windows.Forms.Label.ImageAlign%2A> ters çevirir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.LinkLabel>|Sağa hizalı olarak görüntülendi. <xref:System.Windows.Forms.Label.TextAlign%2A> ve <xref:System.Windows.Forms.Label.ImageAlign%2A> ters çevirir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ListBox>|Öğeler sağa hizalı|Efekt yok|Hayır|
|<xref:System.Windows.Forms.ListView>|Okuma sırasını RTL olarak ayarlar; öğeler sola hizalı kalır|Denetimi yansıtır|Evet|
|<xref:System.Windows.Forms.MainMenu>|Çalışma zamanında (tasarım zamanında değil) RTL okuma sırasıyla sağa hizalı olarak görüntülendi|Efekt yok|Hayır|
|<xref:System.Windows.Forms.MaskedTextBox>|Sağdan sola metin görüntüler.|Efekt yok|Hayır|
|<xref:System.Windows.Forms.MonthCalendar>|Etkilenmemiştir; işletim sisteminin diline bağlıdır|Denetimi yansıtır|Evet|
|<xref:System.Windows.Forms.NotifyIcon>|Desteklenmez|Desteklenmez|Hayır|
|<xref:System.Windows.Forms.NumericUpDown>|Yukarı ve aşağı düğmeleri sola hizalı|Efekt yok|Hayır|
|<xref:System.Windows.Forms.OpenFileDialog>|Sağdan sola işletim sistemlerinde, içeren formun <xref:System.Windows.Forms.Control.RightToLeft> özelliğini, iletişim kutusunu <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> yerelleştirir olarak ayarlama |Efekt yok|Hayır|
|<xref:System.Windows.Forms.PageSetupDialog>|Etkilenmemiştir; işletim sisteminin diline bağlıdır|Efekt yok|Hayır|
|<xref:System.Windows.Forms.Panel>|Alt denetimler bu özelliği kalýtýmla alabilir|Sağdan sola destek için denetim içinde <xref:System.Windows.Forms.TableLayoutPanel> kullanın|Evet|
|<xref:System.Windows.Forms.PictureBox>|Desteklenmez|Efekt yok|Hayır|
|<xref:System.Windows.Forms.PrintDialog>|Etkilenmemiştir; işletim sisteminin diline bağlıdır|Efekt yok|Hayır|
|<xref:System.Drawing.Printing.PrintDocument>|Dikey kaydırma çubuğu sola hizalı hale gelir ve yatay kaydırma çubuğu soldan başlar|Efekt yok|Hayır|
|<xref:System.Windows.Forms.PrintPreviewDialog>|Desteklenmez|Desteklenmez|Hayır|
|<xref:System.Windows.Forms.ProgressBar>|Bu özellik tarafından etkilenmiyor|Denetimi yansıtır|Evet|
|<xref:System.Windows.Forms.RadioButton>|Radyo düğmesi metnin sağ tarafında görüntülenir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.RichTextBox>|Metin içeren denetim öğeleri sağdan sola, RTL okuma sırasıyla görüntülenir|Efekt yok|Hayır|
|<xref:System.Windows.Forms.SaveFileDialog>|Etkilenmemiştir; işletim sisteminin diline bağlıdır|Efekt yok|Hayır|
|<xref:System.Windows.Forms.SplitContainer>|Panel düzeni tersine çevrilir; dikey kaydırma çubuğu solda görünür; yatay kaydırma çubuğu sağdan başlar|Alt denetimlerin sırasını yansıtmak için <xref:System.Windows.Forms.TableLayoutPanel> kullanma|Hayır|
|<xref:System.Windows.Forms.Splitter>|Desteklenmez|Efekt yok|Hayır|
|<xref:System.Windows.Forms.StatusBar>|Desteklenmiyor; Bunun yerine <xref:System.Windows.Forms.StatusStrip> kullanın|Efekt yok; Bunun yerine <xref:System.Windows.Forms.StatusStrip> kullanın|Hayır|
|<xref:System.Windows.Forms.TabControl>|Bu özellikten etkilenmiyor|Denetimi yansıtır|Evet|
|<xref:System.Windows.Forms.TextBox>|Sağdan sola, RTL okuma düzeninde metin görüntüler|Efekt yok|Hayır|
|<xref:System.Windows.Forms.Timer>|Gerekli değil|Gerekli değil|Hayır|
|<xref:System.Windows.Forms.ToolBar>|Bu özellikten etkilenmemektedir; Bunun yerine <xref:System.Windows.Forms.ToolStrip> kullanın|Efekt yok; Bunun yerine <xref:System.Windows.Forms.ToolStrip> kullanın|Evet|
|<xref:System.Windows.Forms.ToolTip>|RTL okuma sırasını ayarlar|Efekt yok|Hayır|
|<xref:System.Windows.Forms.TrackBar>|Kaydırma veya izleme sağdan başlar; <xref:System.Windows.Forms.TrackBar.Orientation%2A> dikey olduğunda, sağ taraftaki zaman işaretleri oluşur|Efekt yok|Hayır|
|<xref:System.Windows.Forms.TreeView>|Yalnızca RTL okuma düzenini ayarlar|Denetimi yansıtır|Evet|
|<xref:System.Windows.Forms.UserControl>|Dikey kaydırma çubuğu solda görünür; yatay kaydırma çubuğunun sağ tarafta parmak izi vardır|Doğrudan destek yoktur; <xref:System.Windows.Forms.TableLayoutPanel> kullanma|Hayır|
|<xref:System.Windows.Forms.VScrollBar>|Kaydırılabilir denetimlerin sağ tarafı yerine sol tarafta gösterilir|Efekt yok|Hayır|

## <a name="encoding"></a>Şifreleme
 Windows Forms Unicode desteği sayesinde, çift yönlü uygulamalarınızı oluştururken herhangi bir karakter kümesini dahil edebilirsiniz. Ancak, tüm Windows Forms denetimleri tüm platformlarda Unicode 'U desteklemez.

## <a name="gdi"></a>GDI+
 Sağdan sola okuma düzeninde metin çizmek için GDI+ kullanabilirsiniz. Metin çizmek için kullanılan <xref:System.Drawing.Graphics.DrawString%2A> yöntemi, metnin kaynak noktasını ters çevirmek için <xref:System.Drawing.StringFormatFlags> numaralandırmanın <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> üyesine ayarlayabileceğiniz bir `StringFormat` parametresini destekler.

## <a name="common-dialog-boxes"></a>Ortak Iletişim kutuları
 Dosya Aç iletişim kutusu gibi sistem araçları, Windows denetimi altındadır. Dil öğelerini işletim sisteminden alırlar. Doğru dil ayarlarına sahip bir Windows sürümü kullanıyorsanız, bu iletişim kutuları çift yönlü dillerle doğru çalışacaktır.

 Benzer şekilde, ileti kutuları işletim sisteminden geçer ve çift yönlü metni destekler. İleti kutusu düğmelerindeki açıklamalı alt yazılar geçerli dil ayarını temel alır. Varsayılan olarak, ileti kutuları sağdan sola okuma düzeni kullanmaz, ancak ileti kutuları görüntülenirken okuma sırasını değiştirmek için bir parametre belirtebilirsiniz.

## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, ScrollBars ve ScrollableControl
 Windows Forms ' de, her iki <xref:System.Windows.Forms.Control.RightToLeft%2A> etkin olduğunda ve <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> <xref:System.Windows.Forms.RightToLeft.Yes>olarak ayarlandığında <xref:System.Windows.Forms.ScrollableControl> türetilmiş tüm sınıfların düzgün şekilde hareket etmesini önleyen bir sınırlama vardır. Örneğin, <xref:System.Windows.Forms.Panel>gibi bir denetim veya <xref:System.Windows.Forms.Panel> (<xref:System.Windows.Forms.FlowLayoutPanel> ya da <xref:System.Windows.Forms.TableLayoutPanel>gibi) türetilmiş bir kapsayıcı sınıfı, formunuz üzerinde yerleştirtiğinizi varsayalım. Kapsayıcıda <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> <xref:System.Windows.Forms.RightToLeft.Yes> ve sonra kapsayıcının içindeki denetimlerin bir veya daha fazlası üzerinde <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right>olarak ayarlarsanız, hiç kaydırma çubuğu görünmez. <xref:System.Windows.Forms.ScrollableControl> türetilen sınıf <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> <xref:System.Windows.Forms.RightToLeft.No>olarak ayarlanmış gibi davranır.

 Şu anda tek geçici çözüm <xref:System.Windows.Forms.ScrollableControl> başka bir <xref:System.Windows.Forms.ScrollableControl>içine yuvalanmamaktadır. Örneğin, bu durumda çalışmak için <xref:System.Windows.Forms.TableLayoutPanel> gerekiyorsa, <xref:System.Windows.Forms.Panel> bir denetimin içine yerleştirebilir ve <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> <xref:System.Windows.Forms.RightToLeft.Yes>olarak ayarlayabilirsiniz.

## <a name="mirroring"></a>Yansıma
 *Yansıtma* , Kullanıcı arabirimi öğelerinin yerleşimini sağdan sola akacak şekilde tersine çevirme anlamına gelir. Yansıtılmış bir Windows formunda, örneğin, en düşük düzeyde değil, başlık çubuğunda en aza Indirmeler, Ekranı Kapla ve Kapat düğmeleri görüntülenir.

 Form veya denetimin <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğini `true` olarak ayarlamak, bir form üzerindeki öğelerin okuma sırasını tersine çevirir, ancak bu ayar düzeni sağdan sola doğru değil — diğer bir deyişle, yansıtmaya neden olmaz. Örneğin, bu özelliğin ayarlanması formun başlık çubuğundaki **simge durumuna küçült**, **Ekranı Kapla**ve **Kapat** düğmelerini formun sol tarafına taşımaz. Benzer şekilde, <xref:System.Windows.Forms.TreeView> denetimi gibi bazı denetimler, ekran Arapça veya Ibranice için uygun olacak şekilde değiştirilmesini gerektirir. <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> özelliğini ayarlar ile bu denetimleri yansıtabilirsiniz.

 Aşağıdaki denetimlerin yansıtılmış sürümlerini oluşturabilirsiniz:

- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TabPage>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.TreeView>

 Bazı denetimler mühürlü. Bu nedenle, bundan yeni bir denetim türemezsiniz. Bunlar <xref:System.Windows.Forms.ImageList> ve <xref:System.Windows.Forms.ProgressBar> denetimlerini içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Web uygulamaları için çift yönlü destek](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
