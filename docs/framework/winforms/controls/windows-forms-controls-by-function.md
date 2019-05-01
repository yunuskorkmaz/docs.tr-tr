---
title: İşlevlere Göre Windows Forms Denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 3a82642c985b7ec1cee885cdda7b054adbe3dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969474"
---
# <a name="windows-forms-controls-by-function"></a>İşlevlere Göre Windows Forms Denetimleri
Windows Forms denetimleri ve İşlevler bir dizi yerine bileşenleri sunar. Aşağıdaki tabloda, Windows Forms denetimleri ve bileşenleri genel işlev göre listelenmektedir. Ayrıca, birden çok denetim aynı işleve hizmet eden mevcut olduğunda, önerilen denetimi yenisiyle denetimi ile ilgili bir not listelenir. Ayrı bir sonraki tabloda, yerine geçilen denetimleri ile kendi önerilen yedekler listelenir.  
  
> [!NOTE]
>  Aşağıdaki tablolarda her kontrol ya da Windows Forms'ta kullanabileceğiniz bileşen listesinde değil; daha kapsamlı bir listesi için bkz [Windows Forms'da kullanılacak denetimler](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Önerilen denetimleri ve bileşenleri tarafından işlevi  
  
|İşlev|Denetim|Açıklama|  
|--------------|-------------|-----------------|  
|Verileri görüntüleme|<xref:System.Windows.Forms.DataGridView> Denetimi|<xref:System.Windows.Forms.DataGridView> Denetim verileri görüntülemek için özelleştirilebilir bir tablo sağlar. <xref:System.Windows.Forms.DataGridView> Sınıfı hücreler, satırlar, sütunlar ve Kenarlıklar özelleştirmesini sağlar. **Not:**  <xref:System.Windows.Forms.DataGridView> Denetim eksik olan çok sayıda temel ve gelişmiş özellikler sağlar <xref:System.Windows.Forms.DataGrid> denetimi. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Veri bağlama ve gezinti|<xref:System.Windows.Forms.BindingSource> bileşeni|Bir forma veri bağlama denetimleri, para birimi yönetimi, değişiklik bildirimi ve diğer hizmetleri sunarak basitleştirir.|  
||<xref:System.Windows.Forms.BindingNavigator> Denetimi|Gidin ve bir form üzerinde verileri işlemek için bir araç çubuğu türü arabirimi sağlar.|  
|Metin düzenleme|<xref:System.Windows.Forms.TextBox> Denetimi|Tasarım zamanında çalışma zamanında kullanıcı tarafından düzenlenebilir veya program aracılığıyla değiştirdiğiniz girilen metni görüntüler.|  
||<xref:System.Windows.Forms.RichTextBox> Denetimi|İle düz metin veya zengin metin biçimi (RTF) biçimlendirme görüntülenecek metni sağlar.|  
||<xref:System.Windows.Forms.MaskedTextBox> Denetimi|Kullanıcı girişi biçimi kısıtlar|  
|Bilgi görüntüle (salt okunur)|<xref:System.Windows.Forms.Label> Denetimi|Kullanıcıların doğrudan düzenleyemeyeceği metin görüntüler.|  
||<xref:System.Windows.Forms.LinkLabel> Denetimi|Metin stili Web bağlantı olarak görüntüler ve kullanıcının özel metin tıkladığında bir olay tetikler. Genellikle başka bir pencere veya bir Web sitesi bağlantı metindir.|  
||<xref:System.Windows.Forms.StatusStrip> Denetimi|Çerçeveli bir alanı kullanmak genellikle en üst form altında uygulamanın geçerli durumu hakkında bilgileri görüntüler.|  
||<xref:System.Windows.Forms.ProgressBar> Denetimi|Kullanıcı için geçerli bir işlemin ilerlemesini görüntüler.|  
|Web sayfası görüntüleme|<xref:System.Windows.Forms.WebBrowser> Denetimi|Kullanıcının formunuzun içinden Web sayfalarında gezinmek sağlar.|  
|Bir listeden seçim|<xref:System.Windows.Forms.CheckedListBox> Denetimi|Öğeleri, bir onay kutusu her eşlik kaydırılabilir bir listesini görüntüler.|  
||<xref:System.Windows.Forms.ComboBox> Denetimi|Öğeleri açılan listesini görüntüler.|  
||<xref:System.Windows.Forms.DomainUpDown> Denetimi|Kullanıcılar ile yukarı ve aşağı düğmeleri kaydırma yapmasına metin öğelerinin bir listesini görüntüler.|  
||<xref:System.Windows.Forms.ListBox> Denetimi|Metin ve grafik öğeleri (simge) bir listesini görüntüler.|  
||<xref:System.Windows.Forms.ListView> Denetimi|Öğeleri dört farklı görünümleri görüntüler. Görünüm yalnızca metin, metin küçük simgelerle, büyük simgeler metinle ve Ayrıntılar görünümü içerir.|  
||<xref:System.Windows.Forms.NumericUpDown> Denetimi|Kullanıcılar ile yukarı ve aşağı düğmeleri kaydırma yapmasına sayı listesini görüntüler.|  
||<xref:System.Windows.Forms.TreeView> Denetimi|İsteğe bağlı onay kutularını markaları ve simgelerini metinle oluşabilir düğüm nesneleri hiyerarşik koleksiyonu görüntüler.|  
|Grafik görüntüleme|<xref:System.Windows.Forms.PictureBox> Denetimi|Grafik dosyaları, bit eşlemler ve simgeleri gibi bir çerçeve içinde görüntüler.|  
|Grafik depolama|<xref:System.Windows.Forms.ImageList> Denetimi|Görüntüler için bir depo olarak görev yapar. <xref:System.Windows.Forms.ImageList> denetimleri ve içerdikleri görüntüleri bir uygulamadan diğerine yeniden kullanılabilir.|  
|Değer ayarı|<xref:System.Windows.Forms.CheckBox> Denetimi|Bir kutuyu ve metin etiketini görüntüler. Genellikle seçeneklerini ayarlamak için kullanılır.|  
||<xref:System.Windows.Forms.CheckedListBox> Denetimi|Öğeleri, bir onay kutusu her eşlik kaydırılabilir bir listesini görüntüler.|  
||<xref:System.Windows.Forms.RadioButton> Denetimi|Açılıp kapatılabilir bir düğme görüntülenir.|  
||<xref:System.Windows.Forms.TrackBar> Denetimi|Bir ölçek boyunca bir "tutacağı" taşıyarak bir ölçekte değerlerini ayarlamak kullanıcıların sağlar.|  
|Tarih ayarı|<xref:System.Windows.Forms.DateTimePicker> Denetimi|Kullanıcıların bir tarih veya saat seçmesine izin vermek için bir grafik Takvim görüntüler.|  
||<xref:System.Windows.Forms.MonthCalendar> Denetimi|Tarih aralığı seçmek kullanıcılara izin vermek için bir grafik Takvim görüntüler.|  
|İletişim kutuları|<xref:System.Windows.Forms.ColorDialog> Denetimi|Kullanıcılara arabirimi öğenin rengini ayarlamak Renk Seçici iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.FontDialog> Denetimi|Kullanıcıların ve bir yazı tipi özniteliklerini ayarlama izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.OpenFileDialog> Denetimi|Kullanıcıların gidin ve bir dosya seçin izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintDialog> Denetimi|Kullanıcıların bir yazıcı seçin ve özniteliklerini ayarlayın izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintPreviewDialog> Denetimi|Bir denetimi nasıl görüntüleyen bir iletişim kutusu görüntüler <xref:System.Drawing.Printing.PrintDocument> bileşen yazdırıldığında görünür.|  
||<xref:System.Windows.Forms.FolderBrowserDialog> Denetimi|Kullanıcıların göz atın, oluşturun ve sonunda bir klasör seçin izin veren bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.SaveFileDialog> Denetimi|Bir dosyaya kaydedin açmasına izin veren bir iletişim kutusu görüntüler.|  
|Menü denetimleri|<xref:System.Windows.Forms.MenuStrip> Denetimi|Özel menü oluşturur. **Not:**  <xref:System.Windows.Forms.MenuStrip> Değiştirmek için tasarlanmış <xref:System.Windows.Forms.MainMenu> denetimi.|  
||<xref:System.Windows.Forms.ContextMenuStrip> Denetimi|Özel bağlam menüleri oluşturur. **Not:**  <xref:System.Windows.Forms.ContextMenuStrip> Değiştirmek için tasarlanmış <xref:System.Windows.Forms.ContextMenu> denetimi.|  
|Komutlar|<xref:System.Windows.Forms.Button> Denetimi|Başlatır, durdurur veya bir işlemi kesintiye uğratır.|  
||<xref:System.Windows.Forms.LinkLabel> Denetimi|Metin stili Web bağlantı olarak görüntüler ve kullanıcının özel metin tıkladığında bir olay tetikler. Genellikle başka bir pencere veya bir Web sitesi bağlantı metindir.|  
||<xref:System.Windows.Forms.NotifyIcon> Denetimi|Arka planda çalışan bir uygulamayı temsil eden bir görev durumu bildirim alanındaki simge görüntüler.|  
||<xref:System.Windows.Forms.ToolStrip> Denetimi|Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer veya özel görünüm, ile veya olmadan temalar ve taşma ve çalışma zamanı öğesi yeniden sıralama desteği olabilir araç çubukları oluşturur. **Not:**  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirmek üzere tasarlanan <xref:System.Windows.Forms.ToolBar> denetimi.|  
|Kullanıcı Yardımı|<xref:System.Windows.Forms.HelpProvider> bileşeni|Açılan veya çevrimiçi Yardım denetimleri sağlar.|  
||<xref:System.Windows.Forms.ToolTip> bileşeni|Kullanıcı işaretçiyi denetimin üzerine getirildiğinde, bir denetimin amacını kısa bir açıklamasını görüntüleyen bir pencere sağlar.|  
|Diğer denetimleri gruplandırma|<xref:System.Windows.Forms.Panel> Denetimi|Etiketlenmemiş, kaydırılabilir bir çerçeve denetimleri kümesini gruplar.|  
||<xref:System.Windows.Forms.GroupBox> Denetimi|Bir etiketlenmiş, nonscrollable karesinde denetimler (örneğin, radyo düğmeleri) kümesini gruplar.|  
||<xref:System.Windows.Forms.TabControl> Denetimi|Düzenleme ve bunlara erişmek için bir sekmeli sayfada gruplanmış nesneleri verimli bir şekilde sağlar.|  
||<xref:System.Windows.Forms.SplitContainer> Denetimi|Taşınabilir bir çubukla ayırarak iki bölme sağlar. **Not:**  <xref:System.Windows.Forms.SplitContainer> Denetimi değiştirmek üzere tasarlanan <xref:System.Windows.Forms.Splitter> denetimi.|  
||<xref:System.Windows.Forms.TableLayoutPanel> Denetimi|Satırları ve sütunları oluşan bir kılavuzda içeriği dışarı dinamik olarak yerleştirir bir panel temsil eder.|  
||<xref:System.Windows.Forms.FlowLayoutPanel> Denetimi|Dinamik olarak, içeriğini yatay veya dikey olarak yerleştirir bir panel temsil eder.|  
|Ses|<xref:System.Media.SoundPlayer> Denetimi|Ses dosyalarını .wav biçimde çalar. Sesler yüklenmedi veya zaman uyumsuz olarak yürütülen.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Denetimleri ve bileşenleri işlevi tarafından değiştirilen  
  
|İşlev|Değiştirilen denetimi|Önerilen değiştirme|  
|--------------|------------------------|-----------------------------|  
|Verileri görüntüleme|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Bilgi görüntüle (salt okunur denetimleri)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Menü denetimleri|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Komutlar|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Form düzeni|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
