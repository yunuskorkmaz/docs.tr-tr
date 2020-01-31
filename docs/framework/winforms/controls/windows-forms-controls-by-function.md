---
title: Işleve göre denetimler
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: f2341d49513b418c244ee7ab93c0858899502487
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741582"
---
# <a name="windows-forms-controls-by-function"></a>İşlevlere Göre Windows Forms Denetimleri
Windows Forms, çok sayıda işlev gerçekleştiren denetimler ve bileşenler sunmaktadır. Aşağıdaki tabloda, genel işleve göre Windows Forms denetimleri ve bileşenleri listelenmektedir. Ayrıca, aynı işlevi sunan birden çok denetim varsa, önerilen denetim, yerini aldığı denetimle ilgili bir notlarla listelenir. Ayrı bir sonraki tabloda, yenisiyle değiştirilen denetimler önerilen değişiklikler ile listelenir.  
  
> [!NOTE]
> Aşağıdaki tablolar Windows Forms ' de kullanabileceğiniz her denetim veya bileşeni listeetmez; daha kapsamlı bir liste için bkz. [Windows Forms Için kullanılacak denetimler](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Işleve göre önerilen denetimler ve bileşenler  
  
|İşlev|Denetim|Açıklama|  
|--------------|-------------|-----------------|  
|Veri görüntüleme|<xref:System.Windows.Forms.DataGridView> denetimi|<xref:System.Windows.Forms.DataGridView> denetim, verileri görüntülemek için özelleştirilebilir bir tablo sağlar. <xref:System.Windows.Forms.DataGridView> sınıfı hücreler, satırlar, sütunlar ve kenarlıkların özelleştirilmesine izin vermez. **Note:**  <xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Windows.Forms.DataGrid> denetiminde bulunmayan çok sayıda temel ve gelişmiş özellik sağlar. Daha fazla bilgi için bkz [. Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Veri bağlama ve gezinme|<xref:System.Windows.Forms.BindingSource> bileşeni|Para birimi yönetimi, değişiklik bildirimi ve diğer hizmetleri sağlayarak bir formdaki verileri bir biçimde bağlamayı basitleştirir.|  
||<xref:System.Windows.Forms.BindingNavigator> denetimi|Bir formdaki verileri gezinmek ve işlemek için bir araç çubuğu türü arabirim sağlar.|  
|Metin düzenlemesi|<xref:System.Windows.Forms.TextBox> denetimi|Çalışma zamanında kullanıcılar tarafından düzenlenebilen veya program aracılığıyla değiştirilebilen tasarım zamanında girilen metni görüntüler.|  
||<xref:System.Windows.Forms.RichTextBox> denetimi|Metnin düz metin veya zengin metin biçimindeki (RTF) biçimlendirmeyle görüntülenmesini sağlar.|  
||<xref:System.Windows.Forms.MaskedTextBox> denetimi|Kullanıcı girişinin biçimini kısıtlar|  
|Bilgi görüntüleme (salt okuma)|<xref:System.Windows.Forms.Label> denetimi|Kullanıcıların doğrudan düzenleyebileceği metni görüntüler.|  
||<xref:System.Windows.Forms.LinkLabel> denetimi|Metni bir Web stili bağlantısı olarak görüntüler ve Kullanıcı özel metne tıkladığında bir olayı tetikler. Genellikle metin, başka bir pencerenin veya Web sitesinin bir bağlantıdır.|  
||<xref:System.Windows.Forms.StatusStrip> denetimi|Bir çerçeveli alanı kullanarak uygulamanın geçerli durumuyla ilgili bilgileri, genellikle üst formun altında görüntüler.|  
||<xref:System.Windows.Forms.ProgressBar> denetimi|Kullanıcıya bir işlemin geçerli ilerlemesini görüntüler.|  
|Web sayfası görüntüleme|<xref:System.Windows.Forms.WebBrowser> denetimi|Kullanıcının formunuzun içindeki Web sayfalarında gezinmesine olanak sağlar.|  
|Listeden seçim|<xref:System.Windows.Forms.CheckedListBox> denetimi|Her biri bir onay kutusuyla birlikte olan öğelerin kaydırılabilir listesini görüntüler.|  
||<xref:System.Windows.Forms.ComboBox> denetimi|Öğelerin açılan listesini görüntüler.|  
||<xref:System.Windows.Forms.DomainUpDown> denetimi|Kullanıcıların yukarı ve aşağı düğmeleriyle kaydırabileceği metin öğelerinin bir listesini görüntüler.|  
||<xref:System.Windows.Forms.ListBox> denetimi|Metin ve grafik öğelerinin bir listesini görüntüler (simgeler).|  
||<xref:System.Windows.Forms.ListView> denetimi|Öğeleri dört farklı görünümden birinde görüntüler. Görünümler yalnızca metin, küçük simgelerle metin, büyük simgelerle metin ve Ayrıntılar görünümü içerir.|  
||<xref:System.Windows.Forms.NumericUpDown> denetimi|Kullanıcıların yukarı ve aşağı düğmelerini kullanarak kaydırabileceği sayıların bir listesini görüntüler.|  
||<xref:System.Windows.Forms.TreeView> denetimi|İsteğe bağlı onay kutuları veya simgeleri olan metinden oluşabilen düğüm nesnelerinin hiyerarşik koleksiyonunu görüntüler.|  
|Grafik görüntüsü|<xref:System.Windows.Forms.PictureBox> denetimi|Bir çerçevede bit eşlemler ve simgeler gibi grafik dosyalarını görüntüler.|  
|Grafik depolama|<xref:System.Windows.Forms.ImageList> denetimi|Görüntüler için bir depo işlevi görür. <xref:System.Windows.Forms.ImageList> denetimleri ve içerdikleri görüntüler, bir uygulamadan sonrakine yeniden kullanılabilir.|  
|Değer ayarı|<xref:System.Windows.Forms.CheckBox> denetimi|Metin için bir onay kutusu ve etiket görüntüler. Genellikle seçenekleri ayarlamak için kullanılır.|  
||<xref:System.Windows.Forms.CheckedListBox> denetimi|Her biri bir onay kutusuyla birlikte olan öğelerin kaydırılabilir listesini görüntüler.|  
||<xref:System.Windows.Forms.RadioButton> denetimi|Açık veya kapalı olabilecek bir düğmeyi görüntüler.|  
||<xref:System.Windows.Forms.TrackBar> denetimi|Kullanıcıların bir ölçekte "thumb" taşıyarak ölçek üzerinde değer ayarlamasına olanak tanır.|  
|Tarih ayarı|<xref:System.Windows.Forms.DateTimePicker> denetimi|Kullanıcıların bir tarih veya saat seçmesine izin vermek için grafik bir takvim görüntüler.|  
||<xref:System.Windows.Forms.MonthCalendar> denetimi|Kullanıcıların bir tarih aralığı seçmesine izin vermek için grafik bir takvim görüntüler.|  
|İletişim kutuları|<xref:System.Windows.Forms.ColorDialog> denetimi|Kullanıcıların bir arabirim öğesi rengini ayarlamasına izin veren Renk Seçici iletişim kutusunu görüntüler.|  
||<xref:System.Windows.Forms.FontDialog> denetimi|Kullanıcıların bir yazı tipi ve özniteliklerini ayarlamasına izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.OpenFileDialog> denetimi|Kullanıcıların bir dosya üzerinde gezindiğini ve seçmesine izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintDialog> denetimi|Kullanıcıların bir yazıcı seçmesini ve özniteliklerini ayarlamanızı sağlayan bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintPreviewDialog> denetimi|Bir denetim <xref:System.Drawing.Printing.PrintDocument> bileşeninin yazdırıldığında nasıl görüneceğini görüntüleyen bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.FolderBrowserDialog> denetimi|Kullanıcıların bir klasöre gözatmasına, oluşturmalarına ve en sonunda seçim yapmasına olanak tanıyan bir iletişim kutusu görüntüler|  
||<xref:System.Windows.Forms.SaveFileDialog> denetimi|Kullanıcıların bir dosyayı kaydetmesine izin veren bir iletişim kutusu görüntüler.|  
|Menü denetimleri|<xref:System.Windows.Forms.MenuStrip> denetimi|Özel menüler oluşturur. **Note:**  <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.MainMenu> denetiminin yerini alacak şekilde tasarlanmıştır.|  
||<xref:System.Windows.Forms.ContextMenuStrip> denetimi|Özel bağlam menüleri oluşturur. **Note:**  <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ContextMenu> denetiminin yerini alacak şekilde tasarlanmıştır.|  
|Komutlar|<xref:System.Windows.Forms.Button> denetimi|Bir işlemi başlatır, durduruyor veya keser.|  
||<xref:System.Windows.Forms.LinkLabel> denetimi|Metni bir Web stili bağlantısı olarak görüntüler ve Kullanıcı özel metne tıkladığında bir olayı tetikler. Genellikle metin, başka bir pencerenin veya Web sitesinin bir bağlantıdır.|  
||<xref:System.Windows.Forms.NotifyIcon> denetimi|Arka planda çalışan bir uygulamayı temsil eden görev çubuğunun durum bildirim alanında bir simge görüntüler.|  
||<xref:System.Windows.Forms.ToolStrip> denetimi|Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer veya özel görünüm içeren, temalar içeren veya içermeyen ve taşma ve çalışma zamanı öğesi yeniden sıralama desteğiyle bir araç çubuğu oluşturur. **Note:**  <xref:System.Windows.Forms.ToolStrip> denetimi, <xref:System.Windows.Forms.ToolBar> denetiminin yerini alacak şekilde tasarlanmıştır.|  
|Kullanıcı Yardımı|<xref:System.Windows.Forms.HelpProvider> bileşeni|Denetimler için açılır veya çevrimiçi yardım sağlar.|  
||<xref:System.Windows.Forms.ToolTip> bileşeni|Kullanıcı işaretçiyi denetimin üzerine getirdiğinde denetimin amacının kısa bir açıklamasını görüntüleyen bir açılır pencere sağlar.|  
|Diğer denetimleri gruplandırma|<xref:System.Windows.Forms.Panel> denetimi|Etiketsiz, kaydırılabilir çerçevede bir denetim kümesini gruplandırır.|  
||<xref:System.Windows.Forms.GroupBox> denetimi|Etiketli, kaydırılamayan çerçevede bir denetim kümesini (radyo düğmeleri gibi) gruplandırır.|  
||<xref:System.Windows.Forms.TabControl> denetimi|Gruplanmış nesneleri düzenlemek ve bunlara erişmek için sekmeli bir sayfa sağlar.|  
||<xref:System.Windows.Forms.SplitContainer> denetimi|Taşınabilir çubukla ayrılmış iki panel sağlar. **Note:**  <xref:System.Windows.Forms.SplitContainer> denetimi, <xref:System.Windows.Forms.Splitter> denetiminin yerini alacak şekilde tasarlanmıştır.|  
||<xref:System.Windows.Forms.TableLayoutPanel> denetimi|Kendi içeriğini satırlardan ve sütunlardan oluşan bir kılavuzda dinamik olarak yerleştirmeyen bir paneli temsil eder.|  
||<xref:System.Windows.Forms.FlowLayoutPanel> denetimi|İçeriğini yatay veya dikey olarak dinamik bir şekilde yerleştirmeyen bir paneli temsil eder.|  
|Ses|<xref:System.Media.SoundPlayer> denetimi|Ses dosyalarını. wav biçiminde çalar. Sesler, zaman uyumsuz olarak yüklenebilir veya çalıştırılabilir.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Işleve göre yenisiyle değiştirilen denetimler ve bileşenler  
  
|İşlev|Yenisiyle değiştirilen denetim|Önerilen değiştirme|  
|--------------|------------------------|-----------------------------|  
|Veri görüntüleme|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Bilgi görüntüleme (salt okuma denetimleri)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Menü denetimleri|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Komutlar|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Form düzeni|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
