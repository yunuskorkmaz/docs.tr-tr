---
title: ToolStrip Teknoloiji Özeti
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: c4f7b13590457623bbdfd6e4c07317f3a0285fd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541917"
---
# <a name="toolstrip-technology-summary"></a>ToolStrip Teknoloiji Özeti
Bu konu hakkında bilgileri özetler `ToolStrip` denetimi ve kullanımını destekleyen sınıflar.  
  
 `ToolStrip` Denetim ve onun ilişkili sınıfları sağlar eksiksiz bir çözüm araç çubukları, durum çubukları ve menüleri oluşturmak için.  
  
## <a name="namespaces"></a>Ad Alanları  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Arka Plan  
 İle `ToolStrip` denetim ve onun ilişkili sınıfları, tutarlı ve profesyonel bir görünüm ve davranış olan Gelişmiş araç işlevselliği oluşturabilirsiniz. `ToolStrip` Denetim ve sınıfları önceki denetimleri aşağıdaki geliştirmeleri sunar:  
  
-   Daha tutarlı bir olay modeli.  
  
-   Görev listeleri ve madde koleksiyon düzenleyiciler içeren daha tutarlı bir tasarım zamanı davranışı.  
  
-   Özel işleme ile `ToolStripManager` ve `ToolStripRenderer`.  
  
-   Yerleşik radye ile (yerleştirildiğinde aracı alanda yatay veya dikey alanı paylaşımı) `ToolStripContainer` ve `ToolStripPanel`.  
  
-   Tasarım zamanı ve çalışma zamanı ile öğelerinin yeniden sıralanmasını <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliği.  
  
-   Taşma menüsüyle öğelerin yeniden konumlandırma <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği.  
  
-   Tamamen yapılandırılabilir denetim konumla `ToolStripContainer`, `ToolStripPanel`, ve `ToolStripContentPanel`.  
  
-   Barındırma `ToolStrip`, geleneksel ya da özel denetimler kullanarak `ToolStripControlHost`.  
  
-   Birleştirme `ToolStrip` denetimlerini kullanma `ToolStripPanel`.  
  
 `ToolStrip` Genişletilebilir temel sınıfı olan `MenuStrip`, `ContextMenuStrip`, ve `StatusStrip`. Bu denetimler <xref:System.Windows.Forms.ToolStripItem> ortak davranışı ve olay işleme devralır kapsayıcıları genişlettiğini her uygulama için uygun davranışı ile ilgilidir. Öğesinden türetilen denetimler <xref:System.Windows.Forms.ToolStripItem> aşağıdaki tabloda listelenmiştir. Temel `ToolStrip` sınıfı boyama, kullanıcı girişi ve bu denetimleri için sürükle ve bırak olayları işler.  
  
 `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, Ve `StatusStrip` denetimleri, önceki araç, menü, kısayol menüsünde ve durum çubuğu denetimleri, bu denetimleri geriye dönük uyumluluk için korunur rağmen değiştirin.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Bir bakışta ToolStrip sınıfları  
 Aşağıdaki tabloda teknoloji alanına göre gruplandırılmış ToolStrip sınıflarını gösterir.  
  
|Teknoloji alanı|örneği|  
|---------------------|-----------|  
|Araç, durum ve menü kapsayıcıları|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|ToolStrip öğeleri|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Konum|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Sunu ve işleme|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>ToolStrip tasarım-zamanı özellikleri  
 <xref:System.Windows.Forms.ToolStrip> Denetimlerin ailesi, düzenleme ve hızla çalışan bir uygulama oluşturabilmesi için kullanıcı arabiriminin foundation tanımlama yerinde için zengin bir araç ve şablonları sağlar.  
  
### <a name="task-dialog-boxes"></a>Görev iletişim kutuları  
 Visual Studio'da bir denetim Tasarımcısı'nda akıllı etiket tıklatarak kolay erişim için bir görev listesi çok sık kullanılan komutlar için görüntüler.  
  
-   [MenuStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [ToolStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [ContextMenuStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [StatusStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [ToolStripContainer görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Öğeleri koleksiyon düzenleyiciler  
 Visual Studio'da tıkladığınızda, **öğe düzenleme** görev listesi veya seçin ve denetim sağ **öğe düzenleme** denetimi için koleksiyon Düzenleyicisi'ni kısayol menüsünde görüntülenir. Koleksiyon düzenleyiciler, eklemek, kaldırmak ve denetimi içeren öğeleri yeniden sıralamak olanak tanır. Ayrıca, görüntüleyin ve denetim ve denetimin öğeleri özelliklerini değiştirin.  
  
-   [MenuStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [StatusStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [ContextMenuStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [ToolStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Denetimleri barındırma  
 <xref:System.Windows.Forms.ToolStripControlHost> SAX için yerleşik sarmalayıcıları <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder. Başka var veya COM denetimi de barındırabilir bir <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Denetimi barındırma örneği için bkz: [nasıl yapılır: ToolStripControlHost ile Windows Forms denetimini kaydırma](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>İşleme  
 <xref:System.Windows.Forms.ToolStrip> sınıfları diğer Windows Forms denetimlerini önemli ölçüde farklı bir işleme uygulamaz. Bu düzeniyle stilleri ve Temalar kolayca uygulayabilirsiniz.  
  
 Stil uygulamak için bir <xref:System.Windows.Forms.ToolStrip> ve tüm <xref:System.Windows.Forms.ToolStripItem> içerdiği nesneleri sahip olmadığınız işlemek <xref:System.Windows.Forms.ToolStripItem.Paint> her öğe için bir olay. Bunun yerine, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini birine <xref:System.Windows.Forms.ToolStripRenderMode> dışındaki değerleri <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Alternatif olarak, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStrip.Renderer%2A> doğrudan öğesinden devralınan bir sınıf için <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu özelliği otomatik olarak ayarlar ayarı <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Birden çok aynı stili uygulayabilirsiniz <xref:System.Windows.Forms.ToolStrip> ayarlayarak aynı uygulamada nesneler <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> için <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> ve ayarı <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğine <xref:System.Windows.Forms.ToolStripManagerRenderMode> istediğiniz veya <xref:System.Windows.Forms.ToolStripRenderer> değeri sırasıyla.  
  
 İşleme örnekleri için bkz: [nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu oluşturup](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Stilleri ve Temalar  
 <xref:System.Windows.Forms.ToolStrip> ve ilişkili sınıfları sağlar görsel stilleri ve geçersiz kılma gerektirmeyen özel görünüm desteklemek için kolay bir yol <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> her öğe için yöntemleri. Kullanım <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> ve <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özellikleri.  
  
## <a name="rafting-and-docking"></a>Radye ve yerleştirme  
 Raft, yerleştirme veya için mutlak konumlandırılması <xref:System.Windows.Forms.ToolStrip> kontrol eder. <xref:System.Windows.Forms.ToolStrip> öğeleri düzenlenir <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kapsayıcısının.  
  
 *Radye* yatay veya dikey boşluk paylaşmak için araç çubukları özelliğidir. Bir Windows formunda olabilir bir <xref:System.Windows.Forms.ToolStripContainer> formun sol, sağ, üst ve alt kenarı konumlandırma ve radye panoları sırayla sahip <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder. Birden çok <xref:System.Windows.Forms.ToolStrip> denetimleri yığın dikey bunları sola veya sağa moduna geçirirseniz <xref:System.Windows.Forms.ToolStripContainer>. Bunları üstüne veya altına yerleştirin varsa bunlar yatay yığın <xref:System.Windows.Forms.ToolStripContainer>. Orta kullanabilirsiniz <xref:System.Windows.Forms.ToolStripContentPanel> , <xref:System.Windows.Forms.ToolStripContainer> geleneksel denetimleri form üzerinde konumlandırmak için.  
  
 Tüm <xref:System.Windows.Forms.ToolStripContainer> denetimleri tasarım zamanında doğrudan seçilebilir ve silinebilir. A <xref:System.Windows.Forms.ToolStripContainer> genişletilebilir ve daraltılabilir ve içerdiği denetimleriyle göre yeniden boyutlandırır.  
  
 *Yerleştirme* formun sol, sağ, üst veya alt kenar basit konumunda bir denetimin belirtilmesi.  
  
 Yerleştirme üzerinden radye avantajı olan <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> denetimleri başka denetimlerle birlikte yatay veya dikey boşluk paylaşabilir.  
  
 Çoğu <xref:System.Windows.Forms.ToolStrip> denetimleri yerleşik radye kullanmak yerine diğer denetimleri gibi forma. Ayrıca belirtebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> denetim serbestçe konumlandırılmış formda grubundan kaldırarak kendi <xref:System.Windows.Forms.ToolStripContainer> ve ayarı kendi `Dock` özelliğine `None`, veya ilgili ayarlayarak mutlak konumunu belirtebilirsiniz <xref:System.Windows.Forms.Control.Location%2A> özellik. Bkz: [nasıl yapılır: forma ToolStripContainer ToolStrip dışı taşıma](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Bir veya daha fazla <xref:System.Windows.Forms.ToolStripPanel> özellikle birden çok belge arabirimi (MDI) uygulamaları için daha fazla esneklik için denetimleri veya ihtiyacınız yoksa bir <xref:System.Windows.Forms.ToolStripContainer>. A <xref:System.Windows.Forms.ToolStripPanel> dockable alanı bulma ve radye sağlar <xref:System.Windows.Forms.ToolStrip> denetimleri ancak değil geleneksel kontrol eder. Varsayılan olarak, <xref:System.Windows.Forms.ToolStripPanel> Tasarımcısı'nda görünmez **araç**, ancak bunu var. sağ tıklayarak put **araç**ve ardından **öğeleri Seç**. Program aracılığıyla da erişebilirsiniz <xref:System.Windows.Forms.ToolStripPanel> ister başka bir sınıf.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, Ve <xref:System.Windows.Forms.StatusStrip> öğeleri taşma olanak tanır. Bu, Microsoft Office araç çubuklarında bu öğeler davranır şekilde benzer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip Denetim, Mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
