---
title: İşlevlere Göre Windows Forms Denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 366b7412a61cac9d3706500adaee34fa8659fba2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922713"
---
# <a name="windows-forms-controls-by-function"></a>İşlevlere Göre Windows Forms Denetimleri
Windows Forms, çok sayıda işlev gerçekleştiren denetimler ve bileşenler sunmaktadır. Aşağıdaki tabloda, genel işleve göre Windows Forms denetimleri ve bileşenleri listelenmektedir. Ayrıca, aynı işlevi sunan birden çok denetim varsa, önerilen denetim, yerini aldığı denetimle ilgili bir notlarla listelenir. Ayrı bir sonraki tabloda, yenisiyle değiştirilen denetimler önerilen değişiklikler ile listelenir.  
  
> [!NOTE]
> Aşağıdaki tablolar Windows Forms ' de kullanabileceğiniz her denetim veya bileşeni listeetmez; daha kapsamlı bir liste için bkz. [Windows Forms Için kullanılacak denetimler](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Işleve göre önerilen denetimler ve bileşenler  
  
|İşlev|Denetim|Açıklama|  
|--------------|-------------|-----------------|  
|Veri görüntüleme|<xref:System.Windows.Forms.DataGridView>denetimle|Denetim <xref:System.Windows.Forms.DataGridView> , verileri görüntülemek için özelleştirilebilir bir tablo sağlar. <xref:System.Windows.Forms.DataGridView> Sınıfı hücrelerin, satırların, sütunların ve kenarlıkların özelleştirilmesine izin vermez. **Not:**  <xref:System.Windows.Forms.DataGridView> Denetim ,<xref:System.Windows.Forms.DataGrid> denetimde bulunmayan çok sayıda temel ve gelişmiş özellik sağlar. Daha fazla bilgi için bkz [. Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Veri bağlama ve gezinme|<xref:System.Windows.Forms.BindingSource> bileşeni|Para birimi yönetimi, değişiklik bildirimi ve diğer hizmetleri sağlayarak bir formdaki verileri bir biçimde bağlamayı basitleştirir.|  
||<xref:System.Windows.Forms.BindingNavigator>denetimle|Bir formdaki verileri gezinmek ve işlemek için bir araç çubuğu türü arabirim sağlar.|  
|Metin düzenlemesi|<xref:System.Windows.Forms.TextBox>denetimle|Çalışma zamanında kullanıcılar tarafından düzenlenebilen veya program aracılığıyla değiştirilebilen tasarım zamanında girilen metni görüntüler.|  
||<xref:System.Windows.Forms.RichTextBox>denetimle|Metnin düz metin veya zengin metin biçimindeki (RTF) biçimlendirmeyle görüntülenmesini sağlar.|  
||<xref:System.Windows.Forms.MaskedTextBox>denetimle|Kullanıcı girişinin biçimini kısıtlar|  
|Bilgi görüntüleme (salt okuma)|<xref:System.Windows.Forms.Label>denetimle|Kullanıcıların doğrudan düzenleyebileceği metni görüntüler.|  
||<xref:System.Windows.Forms.LinkLabel>denetimle|Metni bir Web stili bağlantısı olarak görüntüler ve Kullanıcı özel metne tıkladığında bir olayı tetikler. Genellikle metin, başka bir pencerenin veya Web sitesinin bir bağlantıdır.|  
||<xref:System.Windows.Forms.StatusStrip>denetimle|Bir çerçeveli alanı kullanarak uygulamanın geçerli durumuyla ilgili bilgileri, genellikle üst formun altında görüntüler.|  
||<xref:System.Windows.Forms.ProgressBar>denetimle|Kullanıcıya bir işlemin geçerli ilerlemesini görüntüler.|  
|Web sayfası görüntüleme|<xref:System.Windows.Forms.WebBrowser>denetimle|Kullanıcının formunuzun içindeki Web sayfalarında gezinmesine olanak sağlar.|  
|Listeden seçim|<xref:System.Windows.Forms.CheckedListBox>denetimle|Her biri bir onay kutusuyla birlikte olan öğelerin kaydırılabilir listesini görüntüler.|  
||<xref:System.Windows.Forms.ComboBox>denetimle|Öğelerin açılan listesini görüntüler.|  
||<xref:System.Windows.Forms.DomainUpDown>denetimle|Kullanıcıların yukarı ve aşağı düğmeleriyle kaydırabileceği metin öğelerinin bir listesini görüntüler.|  
||<xref:System.Windows.Forms.ListBox>denetimle|Metin ve grafik öğelerinin bir listesini görüntüler (simgeler).|  
||<xref:System.Windows.Forms.ListView>denetimle|Öğeleri dört farklı görünümden birinde görüntüler. Görünümler yalnızca metin, küçük simgelerle metin, büyük simgelerle metin ve Ayrıntılar görünümü içerir.|  
||<xref:System.Windows.Forms.NumericUpDown>denetimle|Kullanıcıların yukarı ve aşağı düğmelerini kullanarak kaydırabileceği sayıların bir listesini görüntüler.|  
||<xref:System.Windows.Forms.TreeView>denetimle|İsteğe bağlı onay kutuları veya simgeleri olan metinden oluşabilen düğüm nesnelerinin hiyerarşik koleksiyonunu görüntüler.|  
|Grafik görüntüsü|<xref:System.Windows.Forms.PictureBox>denetimle|Bir çerçevede bit eşlemler ve simgeler gibi grafik dosyalarını görüntüler.|  
|Grafik depolama|<xref:System.Windows.Forms.ImageList>denetimle|Görüntüler için bir depo işlevi görür. <xref:System.Windows.Forms.ImageList>denetimler ve içerdikleri görüntüler, bir uygulamadan sonrakine yeniden kullanılabilir.|  
|Değer ayarı|<xref:System.Windows.Forms.CheckBox>denetimle|Metin için bir onay kutusu ve etiket görüntüler. Genellikle seçenekleri ayarlamak için kullanılır.|  
||<xref:System.Windows.Forms.CheckedListBox>denetimle|Her biri bir onay kutusuyla birlikte olan öğelerin kaydırılabilir listesini görüntüler.|  
||<xref:System.Windows.Forms.RadioButton>denetimle|Açık veya kapalı olabilecek bir düğmeyi görüntüler.|  
||<xref:System.Windows.Forms.TrackBar>denetimle|Kullanıcıların bir ölçekte "thumb" taşıyarak ölçek üzerinde değer ayarlamasına olanak tanır.|  
|Tarih ayarı|<xref:System.Windows.Forms.DateTimePicker>denetimle|Kullanıcıların bir tarih veya saat seçmesine izin vermek için grafik bir takvim görüntüler.|  
||<xref:System.Windows.Forms.MonthCalendar>denetimle|Kullanıcıların bir tarih aralığı seçmesine izin vermek için grafik bir takvim görüntüler.|  
|İletişim kutuları|<xref:System.Windows.Forms.ColorDialog>denetimle|Kullanıcıların bir arabirim öğesi rengini ayarlamasına izin veren Renk Seçici iletişim kutusunu görüntüler.|  
||<xref:System.Windows.Forms.FontDialog>denetimle|Kullanıcıların bir yazı tipi ve özniteliklerini ayarlamasına izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.OpenFileDialog>denetimle|Kullanıcıların bir dosya üzerinde gezindiğini ve seçmesine izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintDialog>denetimle|Kullanıcıların bir yazıcı seçmesini ve özniteliklerini ayarlamanızı sağlayan bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintPreviewDialog>denetimle|Bir denetim <xref:System.Drawing.Printing.PrintDocument> bileşeninin yazdırıldığında nasıl görüneceğini görüntüleyen bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.FolderBrowserDialog>denetimle|Kullanıcıların bir klasöre gözatmasına, oluşturmalarına ve en sonunda seçim yapmasına olanak tanıyan bir iletişim kutusu görüntüler|  
||<xref:System.Windows.Forms.SaveFileDialog>denetimle|Kullanıcıların bir dosyayı kaydetmesine izin veren bir iletişim kutusu görüntüler.|  
|Menü denetimleri|<xref:System.Windows.Forms.MenuStrip>denetimle|Özel menüler oluşturur. **Not:**  , <xref:System.Windows.Forms.MenuStrip> Denetimin<xref:System.Windows.Forms.MainMenu> yerini alacak şekilde tasarlanmıştır.|  
||<xref:System.Windows.Forms.ContextMenuStrip>denetimle|Özel bağlam menüleri oluşturur. **Not:**  , <xref:System.Windows.Forms.ContextMenuStrip> Denetimin<xref:System.Windows.Forms.ContextMenu> yerini alacak şekilde tasarlanmıştır.|  
|Komutlar|<xref:System.Windows.Forms.Button>denetimle|Bir işlemi başlatır, durduruyor veya keser.|  
||<xref:System.Windows.Forms.LinkLabel>denetimle|Metni bir Web stili bağlantısı olarak görüntüler ve Kullanıcı özel metne tıkladığında bir olayı tetikler. Genellikle metin, başka bir pencerenin veya Web sitesinin bir bağlantıdır.|  
||<xref:System.Windows.Forms.NotifyIcon>denetimle|Arka planda çalışan bir uygulamayı temsil eden görev çubuğunun durum bildirim alanında bir simge görüntüler.|  
||<xref:System.Windows.Forms.ToolStrip>denetimle|Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer veya özel görünüm içeren, temalar içeren veya içermeyen ve taşma ve çalışma zamanı öğesi yeniden sıralama desteğiyle bir araç çubuğu oluşturur. **Not:**  Denetim, <xref:System.Windows.Forms.ToolBar> denetimin yerini alacak şekilde tasarlanmıştır. <xref:System.Windows.Forms.ToolStrip>|  
|Kullanıcı Yardımı|<xref:System.Windows.Forms.HelpProvider> bileşeni|Denetimler için açılır veya çevrimiçi yardım sağlar.|  
||<xref:System.Windows.Forms.ToolTip> bileşeni|Kullanıcı işaretçiyi denetimin üzerine getirdiğinde denetimin amacının kısa bir açıklamasını görüntüleyen bir açılır pencere sağlar.|  
|Diğer denetimleri gruplandırma|<xref:System.Windows.Forms.Panel>denetimle|Etiketsiz, kaydırılabilir çerçevede bir denetim kümesini gruplandırır.|  
||<xref:System.Windows.Forms.GroupBox>denetimle|Etiketli, kaydırılamayan çerçevede bir denetim kümesini (radyo düğmeleri gibi) gruplandırır.|  
||<xref:System.Windows.Forms.TabControl>denetimle|Gruplanmış nesneleri düzenlemek ve bunlara erişmek için sekmeli bir sayfa sağlar.|  
||<xref:System.Windows.Forms.SplitContainer>denetimle|Taşınabilir çubukla ayrılmış iki panel sağlar. **Not:**  Denetim, <xref:System.Windows.Forms.Splitter> denetimin yerini alacak şekilde tasarlanmıştır. <xref:System.Windows.Forms.SplitContainer>|  
||<xref:System.Windows.Forms.TableLayoutPanel>denetimle|Kendi içeriğini satırlardan ve sütunlardan oluşan bir kılavuzda dinamik olarak yerleştirmeyen bir paneli temsil eder.|  
||<xref:System.Windows.Forms.FlowLayoutPanel>denetimle|İçeriğini yatay veya dikey olarak dinamik bir şekilde yerleştirmeyen bir paneli temsil eder.|  
|Ses|<xref:System.Media.SoundPlayer>denetimle|Ses dosyalarını. wav biçiminde çalar. Sesler, zaman uyumsuz olarak yüklenebilir veya çalıştırılabilir.|  
  
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
