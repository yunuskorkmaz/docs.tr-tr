---
title: "İşlevlere Göre Windows Forms Denetimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a48e1e728e3ded58b0045554a81588933027074c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-controls-by-function"></a>İşlevlere Göre Windows Forms Denetimleri
Windows Forms denetimleri ve işlevleri gerçekleştirmek bileşenleri sunar. Aşağıdaki tabloda Windows Forms denetimleri ve bileşenleri genel işlevi göre listelenmektedir. Ayrıca, aynı işleve hizmet eden birden çok denetim mevcut olduğunda, önerilen denetim yenisiyle denetim ilgili not ile listelenir. Ayrı bir sonraki tabloda değiştirilen denetimleri ile önerilen kendi değişikliklerini listelenir.  
  
> [!NOTE]
>  Aşağıdaki tablolarda her denetimi veya bileşeni Windows Forms'ta kullanabilirsiniz listelemez; daha kapsamlı bir listesi için bkz: [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Önerilen denetimleri ve bileşenleri tarafından işlevi  
  
|İşlev|Denetim|Açıklama|  
|--------------|-------------|-----------------|  
|Verileri görüntüleme|<xref:System.Windows.Forms.DataGridView>denetimi|<xref:System.Windows.Forms.DataGridView> Denetim verileri görüntülemek için özelleştirilebilir bir tablo sağlar. <xref:System.Windows.Forms.DataGridView> Sınıfı hücreler, satırlar, sütunlar ve Kenarlıklar özelleştirmesini sağlar. **Not:** <xref:System.Windows.Forms.DataGridView> denetimi sağlar eksik çok sayıda temel ve Gelişmiş Özellikler <xref:System.Windows.Forms.DataGrid> denetim. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Veri bağlama ve gezinme|<xref:System.Windows.Forms.BindingSource>Bileşen|Veri için bir form üzerinde denetimleri bağlama para birimi yönetimi, değişikliği bildirimi ve diğer hizmetleri sağlayarak basitleştirir.|  
||<xref:System.Windows.Forms.BindingNavigator>denetimi|Gidin ve bir form üzerinde verileri işlemek için bir araç çubuğu türü arabirimi sağlar.|  
|Metin düzenleme|<xref:System.Windows.Forms.TextBox>denetimi|Çalışma zamanında kullanıcı tarafından düzenlenmiş veya program aracılığıyla değiştirilen tasarım zamanında girilen metin görüntüler.|  
||<xref:System.Windows.Forms.RichTextBox>denetimi|Düz metin veya zengin metin biçimi (RTF) biçimlendirme ile görüntülenecek metni sağlar.|  
||<xref:System.Windows.Forms.MaskedTextBox>denetimi|Kullanıcı girişi biçimi kısıtlar|  
|Bilgi görüntüleme (salt okunur)|<xref:System.Windows.Forms.Label>denetimi|Kullanıcıların doğrudan düzenleyemezsiniz metin görüntüler.|  
||<xref:System.Windows.Forms.LinkLabel>denetimi|Metin Web stili bağlantı olarak görüntüler ve özel metin kullanıcı, bir olay tetikler. Genellikle başka bir pencere veya bir Web sitesi bağlantı metindir.|  
||<xref:System.Windows.Forms.StatusStrip>denetimi|Çerçeveli alanı genellikle üst form alt kısmındaki kullanarak uygulamanın geçerli durumuyla ilgili bilgileri görüntüler.|  
||<xref:System.Windows.Forms.ProgressBar>denetimi|Kullanıcı için geçerli bir işlemin ilerlemesini görüntüler.|  
|Web sayfası görüntüleme|<xref:System.Windows.Forms.WebBrowser>denetimi|Form içinde Web sayfalarında gezinmek kullanıcının sağlar.|  
|Listesinden seçim|<xref:System.Windows.Forms.CheckedListBox>denetimi|Öğe, bir onay kutusu her eşlik kaydırılabilir bir listesini görüntüler.|  
||<xref:System.Windows.Forms.ComboBox>denetimi|Öğeleri açılan listesini görüntüler.|  
||<xref:System.Windows.Forms.DomainUpDown>denetimi|Kullanıcılar ile yukarı ve aşağı düğmeleri kaydırmak metin öğeleri listesini görüntüler.|  
||<xref:System.Windows.Forms.ListBox>denetimi|Metin ve grafik öğeleri (simgeler) listesini görüntüler.|  
||<xref:System.Windows.Forms.ListView>denetimi|Öğeleri dört farklı görünümleri görüntüler. Görünümleri yalnızca metin, küçük simgelerle metni, metin büyük simgelerle ve Ayrıntılar görünümü içerir.|  
||<xref:System.Windows.Forms.NumericUpDown>denetimi|Kullanıcılar ile yukarı ve aşağı düğmeleri kaydırmak rakamları listesini görüntüler.|  
||<xref:System.Windows.Forms.TreeView>denetimi|İsteğe bağlı onay kutularını veya simgeleri metinle oluşabilir düğüm nesneleri hiyerarşik koleksiyonunu görüntüler.|  
|Grafik görüntüleme|<xref:System.Windows.Forms.PictureBox>denetimi|Bit eşlemler ve simgeler gibi grafik dosyaları bir çerçevede görüntüler.|  
|Grafik depolama|<xref:System.Windows.Forms.ImageList>denetimi|Görüntüleri için depo görevi görür. <xref:System.Windows.Forms.ImageList>denetimleri ve içerdikleri görüntüleri bir uygulamadan diğerine yeniden kullanılabilir.|  
|Değer ayarı|<xref:System.Windows.Forms.CheckBox>denetimi|Bir onay kutusu ve metin etiketini görüntüler. Genellikle seçeneklerini ayarlamak için kullanılır.|  
||<xref:System.Windows.Forms.CheckedListBox>denetimi|Öğe, bir onay kutusu her eşlik kaydırılabilir bir listesini görüntüler.|  
||<xref:System.Windows.Forms.RadioButton>denetimi|Üzerinde veya açık bir düğme görüntülenir.|  
||<xref:System.Windows.Forms.TrackBar>denetimi|Bir ölçek boyunca bir "tutacağı" taşıyarak bir ölçekte değerlerini ayarlamak kullanıcıların sağlar.|  
|Tarih ayarı|<xref:System.Windows.Forms.DateTimePicker>denetimi|Bir tarih veya saat seçin yapmalarına izin vermek için bir grafik takvim görüntülenir.|  
||<xref:System.Windows.Forms.MonthCalendar>denetimi|Bir tarih aralığı seçin yapmalarına izin vermek için bir grafik takvim görüntülenir.|  
|İletişim kutuları|<xref:System.Windows.Forms.ColorDialog>denetimi|Kullanıcılara bir arabirim öğesinin rengini ayarlamak Renk Seçici iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.FontDialog>denetimi|Kullanıcıların ve bir yazı tipi özniteliklerini ayarlama olanak sağlayan bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.OpenFileDialog>denetimi|Gidin ve bir dosya seçin olanak tanıyan bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintDialog>denetimi|Bir yazıcı seçin ve özniteliklerini ayarlayın olanak tanıyan bir iletişim kutusu görüntüler.|  
||<xref:System.Windows.Forms.PrintPreviewDialog>denetimi|Bir denetim nasıl görüntüleyen bir iletişim kutusu görüntüler <xref:System.Drawing.Printing.PrintDocument> bileşen yazdırıldığında görünür.|  
||<xref:System.Windows.Forms.FolderBrowserDialog>denetimi|Gözat, oluşturmak ve sonunda bir klasör seçmek kullanıcılara bir iletişim kutusu görüntüler|  
||<xref:System.Windows.Forms.SaveFileDialog>denetimi|Bir dosyayı kaydetmek kullanıcılara bir iletişim kutusu görüntüler.|  
|Menü denetimleri|<xref:System.Windows.Forms.MenuStrip>denetimi|Özel menüleri oluşturur. **Not:** <xref:System.Windows.Forms.MenuStrip> değiştirmek için tasarlanmış <xref:System.Windows.Forms.MainMenu> denetim.|  
||<xref:System.Windows.Forms.ContextMenuStrip>denetimi|Özel bağlam menülerini oluşturur. **Not:** <xref:System.Windows.Forms.ContextMenuStrip> değiştirmek için tasarlanmış <xref:System.Windows.Forms.ContextMenu> denetim.|  
|Komutlar|<xref:System.Windows.Forms.Button>denetimi|Başlatır, durdurur veya bir işlem keser.|  
||<xref:System.Windows.Forms.LinkLabel>denetimi|Metin Web stili bağlantı olarak görüntüler ve özel metin kullanıcı, bir olay tetikler. Genellikle başka bir pencere veya bir Web sitesi bağlantı metindir.|  
||<xref:System.Windows.Forms.NotifyIcon>denetimi|Arka planda çalışan bir uygulama temsil eden görev çubuğunun durum bildirim alanında bir simge görüntülenir.|  
||<xref:System.Windows.Forms.ToolStrip>denetimi|Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer veya özel görünüm, ile veya olmadan temalar ve taşma ve çalışma zamanı öğesi yeniden sıralama için destek sağlayabilirsiniz araç çubukları oluşturur. **Not:** <xref:System.Windows.Forms.ToolStrip> denetim değiştirmek için tasarlanmıştır <xref:System.Windows.Forms.ToolBar> denetim.|  
|Kullanıcı Yardımı|<xref:System.Windows.Forms.HelpProvider>Bileşen|Açılır veya çevrimiçi Yardım denetimleri sağlar.|  
||<xref:System.Windows.Forms.ToolTip>Bileşen|Kullanıcı denetimi işaretçisi getirildiğinde, bir denetimin amacı kısa bir açıklamasını görüntüleyen bir açılır pencere sağlar.|  
|Diğer denetimleri gruplandırma|<xref:System.Windows.Forms.Panel>denetimi|Etiketlenmemiş, kaydırılabilir çerçevesinde denetimleri kümesini gruplandırır.|  
||<xref:System.Windows.Forms.GroupBox>denetimi|Etiketli, nonscrollable çerçevesinde (örneğin, radyo düğmeleri) denetimleri kümesini gruplandırır.|  
||<xref:System.Windows.Forms.TabControl>denetimi|Düzenleme ve erişme sekmeli sayfa nesneleri verimli bir şekilde gruplandırılmış sağlar.|  
||<xref:System.Windows.Forms.SplitContainer>denetimi|Taşınabilir bir çubukla ayrılan iki bölme sağlar. **Not:** <xref:System.Windows.Forms.SplitContainer> denetim değiştirmek için tasarlanmıştır <xref:System.Windows.Forms.Splitter> denetim.|  
||<xref:System.Windows.Forms.TableLayoutPanel>denetimi|Dinamik olarak içeriğini satırları ve sütunları oluşan bir kılavuz olarak mı yerleştireceğini bir panel temsil eder.|  
||<xref:System.Windows.Forms.FlowLayoutPanel>denetimi|Dinamik olarak, içeriğini yatay veya dikey olarak mı yerleştireceğini bir panel temsil eder.|  
|Ses|<xref:System.Media.SoundPlayer>denetimi|Ses dosyalarını .wav biçiminde çalar. Ses yüklü veya zaman uyumsuz olarak yürütülebilir.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Denetimleri ve bileşenleri işlevi tarafından değiştirilen  
  
|İşlev|Değiştirilen denetimi|Önerilen değiştirme|  
|--------------|------------------------|-----------------------------|  
|Verileri görüntüleme|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Bilgi görüntüleme (salt okunur denetimler)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Menü denetimleri|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Komutlar|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Form düzeni|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
