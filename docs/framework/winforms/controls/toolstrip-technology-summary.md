---
title: ToolStrip Teknoloiji Özeti
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: 26317fad5796989a58a48e4f26549805b279228a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264889"
---
# <a name="toolstrip-technology-summary"></a>ToolStrip Teknoloiji Özeti
Bu konu hakkında bilgiler için özetlenmiştir `ToolStrip` denetimi ve kullanımını destekleyen sınıflar.  
  
 `ToolStrip` Denetimi ve ilişkili sınıflarının sağlayan eksiksiz bir çözüm araç çubukları, durum çubukları ve menüler oluşturmak için.  
  
## <a name="namespaces"></a>Ad Alanları  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Arka Plan  
 İle `ToolStrip` denetimi ve ilişkili sınıflarının, tutarlı ve profesyonel görünümünü ve davranışını olan Gelişmiş araç işlevselliğini oluşturabilirsiniz. `ToolStrip` Denetimi ve sınıfları önceki denetimlerin üzerine aşağıdaki geliştirmeleri sunar:  
  
-   Daha tutarlı bir olay modeli.  
  
-   Görev listeleri ve koleksiyon düzenleyicileri öğesi içeren daha tutarlı bir tasarım zamanı davranışını.  
  
-   Özel işleme ile `ToolStripManager` ve `ToolStripRenderer`.  
  
-   Yerleşik radye ile (Yuvalandığında araç alanı içinde yatay veya dikey boşluk paylaşımını) `ToolStripContainer` ve `ToolStripPanel`.  
  
-   Tasarım zamanı ve çalışma zamanı ile öğelerinin yeniden sıralanmasını <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliği.  
  
-   Bir taşma menüsü öğeleri yeniden konumlandırma <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği.  
  
-   Tamamen yapılandırılabilir denetim konumuyla `ToolStripContainer`, `ToolStripPanel`, ve `ToolStripContentPanel`.  
  
-   Barındırılmasını `ToolStrip`, geleneksel ya da özel denetimler kullanarak `ToolStripControlHost`.  
  
-   Birleştirme `ToolStrip` denetimlerini kullanma `ToolStripPanel`.  
  
 `ToolStrip` Genişletilebilir temel sınıfı olan `MenuStrip`, `ContextMenuStrip`, ve `StatusStrip`. Bu denetimler <xref:System.Windows.Forms.ToolStripItem> ortak davranışını ve olay işlemede, devralınan kapsayıcıları genişlettiğini her uygulama için uygun davranışı ile ilgilidir. Öğesinden türetilen denetimler <xref:System.Windows.Forms.ToolStripItem> aşağıdaki tabloda listelenmiştir. Temel `ToolStrip` sınıfı boyama, kullanıcı girişini ve bu denetimleri için sürükle ve bırak olayları işler.  
  
 `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, Ve `StatusStrip` denetimleri, önceki araç, menü, kısayol menüsünü ve durum çubuğu denetimleri, geriye dönük uyumluluk için bu denetimleri korunur ancak değiştirin.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Bir bakışta ToolStrip sınıfları  
 Teknoloji alanı tarafından gruplandırılmış ToolStrip sınıfları aşağıdaki tabloda gösterilmektedir.  
  
|Teknoloji alanı|örneği|  
|---------------------|-----------|  
|Araç, durum ve menü kapsayıcıları|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|ToolStrip öğeler|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Konum|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Sunu ve işleme|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>ToolStrip tasarım-zamanı özellikleri  
 <xref:System.Windows.Forms.ToolStrip> Denetimlerin ailesi, düzenleme ve hızlı bir şekilde çalışan bir uygulama oluşturabilmeniz kullanıcı arabiriminin temel tanımlama yerinde için zengin bir araç ve şablonları sağlar.  
  
### <a name="task-dialog-boxes"></a>Görev iletişim kutuları  
 Visual Studio'da bir denetim Tasarımcısı'nda akıllı etiketine tıkladığınızda kolay erişim için bir görev listesi çok sık kullanılan komutlar için görüntüler.  
  
-   [MenuStrip görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [ToolStrip görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [ContextMenuStrip görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [StatusStrip görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [ToolStripContainer görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Öğeler Koleksiyonu Düzenleyicisi  
 Visual Studio'da tıkladığınızda, **öğe düzenleme** görev listesinde veya seçin ve denetim sağ tıklayın **öğe düzenleme** Koleksiyonu Düzenleyicisi denetimi için kısayol menüsünde görüntülenir. Koleksiyon düzenleyiciler, ekleme, kaldırma ve denetimi içeren öğeleri yeniden sıralamak olanak tanır. Ayrıca, görüntüleyebilir ve denetimi ve denetimin öğeleri özelliklerini değiştirin.  
  
-   [MenuStrip öğeler Koleksiyonu Düzenleyicisi](https://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [StatusStrip öğeler Koleksiyonu Düzenleyicisi](https://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [ContextMenuStrip öğeler Koleksiyonu Düzenleyicisi](https://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [ToolStrip öğeler Koleksiyonu Düzenleyicisi](https://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Denetimleri barındırma  
 <xref:System.Windows.Forms.ToolStripControlHost> Sınıfı için yerleşik sarmalayıcıları sağlar <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder. Başka var veya COM denetiminde de barındırabilir bir <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Denetim barındırma örneği için bkz: [nasıl yapılır: ToolStripControlHost ile bir Windows Forms denetimini kaydırma](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>işleme  
 <xref:System.Windows.Forms.ToolStrip> sınıflar, diğer Windows Forms denetimlerini önemli ölçüde farklı bir işleme düzeni uygular. Bu düzen ile stilleri ve Temalar kolayca uygulayabilirsiniz.  
  
 Bir stil uygulamak için bir <xref:System.Windows.Forms.ToolStrip> ve tüm <xref:System.Windows.Forms.ToolStripItem> içerdiği nesneler yok işlemek <xref:System.Windows.Forms.ToolStripItem.Paint> her öğe için olay. Bunun yerine, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini birine <xref:System.Windows.Forms.ToolStripRenderMode> dışındaki değerler <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Alternatif olarak, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStrip.Renderer%2A> doğrudan öğesinden devralınan bir sınıf için <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu özellik otomatik olarak ayarlar ayarı <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Birden çok aynı stil uygulayabilirsiniz <xref:System.Windows.Forms.ToolStrip> ayarlayarak aynı uygulamada nesneler <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> için <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> ve ayarı <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğini <xref:System.Windows.Forms.ToolStripManagerRenderMode> istediğiniz veya <xref:System.Windows.Forms.ToolStripRenderer> değeri sırasıyla.  
  
 İşleme örnekleri için bkz: [nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu Oluşturma ve](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Stiller ve Temalar  
 <xref:System.Windows.Forms.ToolStrip> ve ilişkili sınıflarının görsel stilleri ve geçersiz kılma gerektirmeyen özel görünüşünü desteklemek için kolay bir yol sağlamak <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> her öğe için yöntemleri. Kullanım <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> ve <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özellikleri.  
  
## <a name="rafting-and-docking"></a>Radye ve yerleştirme  
 Yapabilir raft, yerleştirme veya mutlak konumlandırılması <xref:System.Windows.Forms.ToolStrip> kontrol eder. <xref:System.Windows.Forms.ToolStrip> öğeleri düzenlenir <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kapsayıcının.  
  
 *Radye* araç çubukları yatay veya dikey boşluk paylaşma olanağı. Bir Windows form olabilir bir <xref:System.Windows.Forms.ToolStripContainer> sırayla olan formun sol, sağ, üst ve alt kenarı konumlandırma ve radye panelleri <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder. Birden çok <xref:System.Windows.Forms.ToolStrip> denetimleri yığın dikey olarak bunları sola veya sağa yerleştirdiğinizde <xref:System.Windows.Forms.ToolStripContainer>. Bunları üstüne veya altına yerleştirebilirsiniz varsa bunlar yatay olarak yerleşir <xref:System.Windows.Forms.ToolStripContainer>. Orta kullanabileceğiniz <xref:System.Windows.Forms.ToolStripContentPanel> , <xref:System.Windows.Forms.ToolStripContainer> geleneksel denetimleri form üzerinde yerleştirmek için.  
  
 Tüm <xref:System.Windows.Forms.ToolStripContainer> denetimleri tasarım zamanında doğrudan seçilebilir ve silinebilir. A <xref:System.Windows.Forms.ToolStripContainer> genişletilebilen ve daraltılabilen ve içerdiği denetimlerle yeniden boyutlandırır.  
  
 *Yerleştirme* formun sol, sağ, üst veya alt kenar üzerinde basit bir denetim konumunun belirtilmesi.  
  
 Üzerinde yerleşik radye avantajı olan <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> denetimleri, diğer denetimlerle yatay veya dikey boşluk paylaşabilir.  
  
 Çoğu <xref:System.Windows.Forms.ToolStrip> denetimleri yerleşik radye kullanmak yerine, diğer denetimler gibi form. Gerektiğini de belirtebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> denetimi serbestçe konumlandırılmış formunda grubundan kaldırarak kendi <xref:System.Windows.Forms.ToolStripContainer> ve ayarı kendi `Dock` özelliğini `None`, ya da mutlak konumunu ilgili ayarlayarak belirtebilirsiniz <xref:System.Windows.Forms.Control.Location%2A> özellik. Bkz: [nasıl yapılır: bir ToolStrip forma ToolStripContainer taşıma](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Bir veya daha fazla <xref:System.Windows.Forms.ToolStripPanel> özellikle birden çok Belgeli Arabirim (MDI) uygulamaları için daha fazla esneklik için denetimleri veya gereksinim duymadığınız bir <xref:System.Windows.Forms.ToolStripContainer>. A <xref:System.Windows.Forms.ToolStripPanel> yerleştirilebilir bir alanı bulmak ve radye sağlar <xref:System.Windows.Forms.ToolStrip> denetimleri ancak değil geleneksel denetimleri. Varsayılan olarak, <xref:System.Windows.Forms.ToolStripPanel> Tasarımcısı'nda görünmez **araç kutusu**, ancak bunu orada sağ tıklayarak koyun **araç kutusu**ve ardından **öğelerini Seç**. Ayrıca programlı bir şekilde erişebileceğiniz <xref:System.Windows.Forms.ToolStripPanel> ister başka bir sınıf.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, Ve <xref:System.Windows.Forms.StatusStrip> öğeleri taşma olanak tanır. Benzer şekilde, Microsoft Office araç çubuklarında bu öğelere davranış budur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip Denetim, Mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
