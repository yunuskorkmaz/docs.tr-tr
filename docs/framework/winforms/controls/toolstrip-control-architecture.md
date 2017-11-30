---
title: ToolStrip Denetim Mimarisi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6884598e6b883ab5e6369be5f2f796a194c7f930
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="toolstrip-control-architecture"></a>ToolStrip Denetim Mimarisi
<xref:System.Windows.Forms.ToolStrip> Ve <xref:System.Windows.Forms.ToolStripItem> sınıfları araç, durum ve menü öğelerini görüntülemek için esnek ve Genişletilebilir bir sistemi sağlar. Bu sınıfların tüm bulunan <xref:System.Windows.Forms> ad alanı ve bunlar tüm genellikle adlandırıldığı "ToolStrip" önekiyle (gibi <xref:System.Windows.Forms.ToolStripOverflow>) veya "Şerit" soneki (gibi <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 Aşağıdaki konularda açıklanmıştır <xref:System.Windows.Forms.ToolStrip> ve bu sınıftan türetilen denetimler.  
  
 <xref:System.Windows.Forms.ToolStrip>için Özet temel sınıf <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, ve <xref:System.Windows.Forms.ContextMenuStrip>. Aşağıdaki nesne modeli gösterilmektedir <xref:System.Windows.Forms.ToolStrip> Devralma Hiyerarşisi.  
  
 ![ToolStrip nesne modeli](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.gif "ToolStripObjectModel")  
ToolStrip nesne modeli  
  
 Tüm öğeleri erişebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> aracılığıyla <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonu. Tüm öğeleri erişebilirsiniz bir <xref:System.Windows.Forms.ToolStripDropDownItem> aracılığıyla <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> koleksiyonu. Türetilen bir sınıfta <xref:System.Windows.Forms.ToolStrip>, aynı zamanda <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> özelliği şu anda görüntülenen öğelere erişmek için. Bunlar bir taşma menüde olmayan öğelerdir.  
  
 Aşağıdaki öğeler ikisi ile sorunsuz çalışması için özel olarak tasarlanmıştır <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleriyle içinde. Tasarım zamanında varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.ToolStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip>yerine geçen en üst düzey kapsayıcıdır <xref:System.Windows.Forms.MainMenu>. Ayrıca anahtar işleme ve birden çok belge arabirimi (MDI) özellikleri sağlar. İşlevsellik, <xref:System.Windows.Forms.ToolStripDropDownItem> ve <xref:System.Windows.Forms.ToolStripMenuItem> ile birlikte çalışma <xref:System.Windows.Forms.MenuStrip>, öğesinden türetilen rağmen <xref:System.Windows.Forms.ToolStripItem>.  
  
 Aşağıdaki öğeler ikisi ile sorunsuz çalışması için özel olarak tasarlanmıştır <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleriyle içinde. Tasarım zamanında varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.MenuStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip>değiştirir <xref:System.Windows.Forms.StatusBar> denetim. Özel özelliklerini <xref:System.Windows.Forms.StatusStrip> özel tablo yerleşimi içerir, formun boyutlandırma ve GRIPS, taşıma için destek ve `Spring` veren özelliği, bir <xref:System.Windows.Forms.ToolStripStatusLabel> otomatik olarak kullanılabilir alanı dolduracak şekilde.  
  
 Aşağıdaki öğeler ikisi ile sorunsuz çalışması için özel olarak tasarlanmıştır <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleriyle içinde. Tasarım zamanında varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.StatusStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip>değiştirir <xref:System.Windows.Forms.ContextMenu>. İlişkilendirebilirsiniz bir <xref:System.Windows.Forms.ContextMenuStrip> herhangi bir denetim ve farenin sağ tıklatın otomatik olarak bağlam menüsünden (veya kısayol menüsünden) görüntüler. Size gösterebilir bir <xref:System.Windows.Forms.ContextMenuStrip> kullanarak program aracılığıyla <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> yöntemi. <xref:System.Windows.Forms.ContextMenuStrip>İptal edilebilen destekler <xref:System.Windows.Forms.ToolStripDropDown.Opening> ve <xref:System.Windows.Forms.ToolStripDropDown.Closing> dinamik popülasyon ve birden çok tıklatma senaryoları işlemek için olaylar. <xref:System.Windows.Forms.ContextMenuStrip>görüntüleri, menü öğesi denetim durumu, metin, erişim tuşları, kısayolları ve basamaklı menüler destekler.  
  
 Aşağıdaki öğeler ikisi ile sorunsuz çalışması için özel olarak tasarlanmıştır <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleriyle içinde. Tasarım zamanında varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.ContextMenuStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip genel özellikleri  
 Aşağıdaki konular özellikleri ve genel için davranışını açıklamak <xref:System.Windows.Forms.ToolStrip> ve denetimleri türetilmiş.  
  
#### <a name="painting"></a>Boyama  
 Özel boyama yapabileceğiniz <xref:System.Windows.Forms.ToolStrip> çeşitli şekillerde kontrol eder. Diğer Windows Forms denetimleri olduğu gibi ile <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripItem> geçersiz kılınabilir sahip `OnPaint` yöntemleri ve `Paint` olaylar. Normal boyama ile koordinat sistemi denetimi istemci alanını göreli olarak; diğer bir deyişle, Denetim sol üst köşesinin 0'dır ve 0. `Paint` Olay ve `OnPaint` yöntemi için bir <xref:System.Windows.Forms.ToolStripItem> diğer denetim boyama olayları gibi davranır.  
  
 <xref:System.Windows.Forms.ToolStrip> Denetimleri de öğeleri ve kapsayıcı aracılığıyla daha hassas erişim sağlar <xref:System.Windows.Forms.ToolStripRenderer> boyama arka plan, öğenin arka plan, öğesi resmi, öğesi okunu, öğesi metni için geçersiz kılınabilir yöntemleri vardır, sınıf ve kenarlığı <xref:System.Windows.Forms.ToolStrip>. Bu yöntemleri için olay bağımsız dikdörtgenler, renk ve istediğiniz gibi değiştirebilirsiniz metin biçimleri gibi çeşitli özellikler kullanıma sunar.  
  
 Yalnızca birkaç yönlerini öğeyi nasıl boyanır ayarlamak için genellikle kılmanız <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Yeni bir öğe yazma ve boyama tüm yönlerini denetlemek istiyorsanız, geçersiz kılma `OnPaint` yöntemi. İçinden `OnPaint`, yöntemleri kullanabilirsiniz <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip> yararlanarak arabelleğe çift olan <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> ayarı.  
  
#### <a name="parenting"></a>Üst öğe ayarlama  
 Kapsayıcı sahipliği ve ana öğe kavramı, daha karmaşık <xref:System.Windows.Forms.ToolStrip> diğer Windows Forms kapsayıcı denetimlerinde denetimleri daha. Birden çok açılan öğelerini paylaşma taşma gibi dinamik senaryoları desteklemek için gerekli olan <xref:System.Windows.Forms.ToolStrip> öğeleri ve oluşturulmasını desteklemek için bir <xref:System.Windows.Forms.ContextMenuStrip> kontrolü.  
  
 Aşağıdaki listede ana öğe için ilgili üyeleri açıklar ve bunların kullanılması açıklanmaktadır.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>kaynağı açılan öğesi, öğenin erişir. Bu benzer <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ancak bir denetimi döndürme yerine döndürür bir <xref:System.Windows.Forms.ToolStripItem>.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>Kaynak denetleyen belirler, <xref:System.Windows.Forms.ContextMenuStrip> zaman birden çok denetim paylaşmak aynı <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>salt okunur bir erişen olup <xref:System.Windows.Forms.ToolStripItem.Parent%2A> özelliği. Bir üst bir sahibinden farklıdır döndürülen geçerli bir üst gösterir <xref:System.Windows.Forms.ToolStrip> öğesi, hangi taşma alanında olabilir görüntülendiği içinde.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A>döndürür <xref:System.Windows.Forms.ToolStrip> geçerli olan öğeler koleksiyonunu içeren <xref:System.Windows.Forms.ToolStripItem>. Başvuru için en iyi yolu budur <xref:System.Windows.Forms.ToolStrip.ImageList%2A> veya diğer özellikleri üst düzey <xref:System.Windows.Forms.ToolStrip> taşma işlemek için özel kod yazma olmadan.  
  
#### <a name="behavior-of-inherited-controls"></a>Devralınan denetimleri davranışı  
 Devralma kullanıldığı zaman aşağıdaki denetimleri kilitlenen:  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>paneller içeren bir <xref:System.Windows.Forms.ToolStripContainer> ve ayrıca tek tek <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.  
  
 Örneğin, önceki listede bir veya daha fazla denetimleri kullanarak yeni bir Windows Forms uygulaması oluşturun. Bir veya daha fazla denetim için erişim değiştiricisi ayarlamak `public` veya `protected`ve projeyi oluşturun. İlk formundan devralan bir form ekleyin ve ardından devralınan bir denetim seçin. Denetim, kendi erişim değiştiricisi boşmuş gibi davranmakta, kilitli görünür `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer destek devralma  
 <xref:System.Windows.Forms.ToolStripContainer> Denetimi sınırlı devralınan senaryoları, aşağıdaki örneğe benzer destekler:  
  
1.  Yeni bir Windows Forms uygulaması oluşturma.  
  
2.  Ekleme bir <xref:System.Windows.Forms.ToolStripContainer> form.  
  
3.  Erişim değiştiricisi ayarlamak <xref:System.Windows.Forms.ToolStripContainer> için `public` veya `protected`.  
  
4.  Herhangi bir bileşimini eklemek <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.ContextMenuStrip> için denetimler <xref:System.Windows.Forms.ToolStripPanel> bölgelerinin <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Projeyi oluşturun.  
  
6.  İlk formundan devralan bir form ekleyin.  
  
7.  Devralınan seçin <xref:System.Windows.Forms.ToolStripContainer> form üzerinde.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Alt denetimler devralınan davranışı  
 Yukarıdaki adımları tamamladıktan sonra aşağıdaki devralınan davranış oluşur:  
  
-   Tasarımcıda denetimi ile devralınan bir simge görüntülenir.  
  
-   <xref:System.Windows.Forms.ToolStripPanel> Denetimleri kilitli; seçin veya içeriklerini yeniden düzenleyin.  
  
-   Denetimlere ekleyebilirsiniz <xref:System.Windows.Forms.ToolStripContentPanel>denetimleri taşımak ve alt denetimleri yapmak <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Değişikliklerinizi form oluşturduktan sonra kalıcı olmasını sağlar.  
  
    > [!NOTE]
    >  Erişim değiştiricileri tümünden kaldırma <xref:System.Windows.Forms.ToolStripPanel> parçası olan denetimleri bir <xref:System.Windows.Forms.ToolStripContainer>. Erişim değiştiricisi <xref:System.Windows.Forms.ToolStripContainer> tam denetim yönetir.  
  
#### <a name="partial-trust"></a>Kısmi Güven  
 Sınırlamaları `ToolStrip`s kısmi güven altında yetkisiz kişilerin veya hizmetler tarafından kullanılabilecek kişisel bilgilerin yanlışlıkla girişini engellemek için tasarlanmıştır. Koruyucu ölçüleri aşağıdaki gibidir:  
  
-   `ToolStripDropDown`denetimleri gerektiren <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> öğeleri görüntülemek için bir <xref:System.Windows.Forms.ToolStripControlHost>. Bu iki iç gibi denetimlere <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar> de kullanıcı tarafından oluşturulan seçeceğine denetimleri gibi. Bu gereksinim karşılanmazsa, bu öğeler görüntülenmez. Hiçbir özel durum oluşur.  
  
-   Ayarı <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> özelliğine `false` izin verilmiyor ve iptal edilebilen <xref:System.Windows.Forms.ToolStripDropDown.Closing> olay parametresi yoksayılır. Bu, açılan öğe durdurulduğundan olmadan birden fazla tuş vuruşu girmeniz mümkün kılar. Bu gereksinim uyulmazsa gibi öğeler görüntülenmez. Hiçbir özel durum oluşur.  
  
-   Kısmi güven bağlamlarda dışında meydana gelirse olayları işleme birçok tuş vuruşu oluşturulmaz <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
-   Erişim tuşları olmayan zaman işlenen <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> değil verilir.  
  
#### <a name="usage"></a>Kullanım  
 Aşağıdaki kullanım desenlerini bir şifrelemeyle sahip <xref:System.Windows.Forms.ToolStrip> düzeni, klavye etkileşimi ve son kullanıcı davranışı:  
  
-   Birleştirilmiş bir<xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip> İçinde konumlandırılmasına <xref:System.Windows.Forms.ToolStripPanel> ve çapraz <xref:System.Windows.Forms.ToolStripPanel>s. `Dock` Özelliği yoksayılır ve <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliği `false`, boyutu <xref:System.Windows.Forms.ToolStrip> öğeleri eklendikçe büyür <xref:System.Windows.Forms.ToolStripPanel>. Genellikle, <xref:System.Windows.Forms.ToolStrip> sekme sırası katılmıyor.  
  
-   Yerleşik  
  
     <xref:System.Windows.Forms.ToolStrip> Sabit bir konumda bir kapsayıcı bir tarafındaki yerleştirilir ve onu yerleşik kenarın tamamını boyutuna genişletir. Genellikle, <xref:System.Windows.Forms.ToolStrip> sekme sırası katılmıyor.  
  
-   Mutlak olarak konumlandırılmış  
  
     <xref:System.Windows.Forms.ToolStrip> Tarafından yerleştirilen diğer denetimleri gibi olmamasıdır <xref:System.Windows.Forms.Control.Location%2A> özelliği, sabit bir boyutu vardır ve genellikle sekme sırası katılır.  
  
#### <a name="keyboard-interaction"></a>Klavye etkileşimi  
  
##### <a name="access-keys"></a>Erişim tuşları  
 İle veya ALT tuşu aşağıdaki birleştirilmiş, erişim tuşları klavyeyi kullanarak bir denetimi etkinleştirmek için bir yoludur. <xref:System.Windows.Forms.ToolStrip>Her iki açık ve kapalı erişim anahtarları destekler. Açık bir tanımını bir ampersan (&) karakteri harf önceki kullanır. Örtük tanımını karakter terabayt göre eşleşen bir öğe bulmaya çalışır bir algoritma kullanan bir verilen `Text` özelliği.  
  
##### <a name="shortcut-keys"></a>Kısayol tuşları  
 Kısayol tuşları tarafından kullanılan bir <xref:System.Windows.Forms.MenuStrip> oluşan bir bileşim kullanmanız <xref:System.Windows.Forms.Keys> (hangi sipariş özgü değildir) numaralandırması kısayol tuşunu tanımlamak için. Aynı zamanda <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> "Sil" yerine "Del" görüntüleme gibi bir kısayol tuşu yalnızca metinle görüntülenecek özelliği  
  
##### <a name="navigation"></a>Gezinme  
 ALT tuşu etkinleştirir <xref:System.Windows.Forms.MenuStrip> gösterdiği <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Buradan, arasında CTRL + SEKME gider <xref:System.Windows.Forms.ToolStrip> içinde denetimleri `ToolStripPanel`s. Sekme tuşuna ve sayısal tuş takımında ok tuşları öğeleri arasında gezinme bir <xref:System.Windows.Forms.ToolStrip>. Özel bir algoritma taşma bölgede Gezinti işler. Boşluk çubuğu seçer bir <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, veya <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Odak ve doğrulama  
 ALT anahtar ile etkinleştirildiğinde <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ToolStrip> genellikle hiçbiri alın veya odağa sahip denetim odağı kaldırmaz. İçinde barındırılan bir denetim olup olmadığını <xref:System.Windows.Forms.MenuStrip> veya bir açılan <xref:System.Windows.Forms.MenuStrip>, denetimi, kullanıcı SEKME tuşuna bastığında odak kazanır. Genel olarak, <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, ve <xref:System.Windows.Forms.Control.Leave> olayları <xref:System.Windows.Forms.MenuStrip> klavye tarafından etkinleştirildiğinde oluşmayabilir. Bu gibi durumlarda kullanmak <xref:System.Windows.Forms.MenuStrip.MenuActivate> ve <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> olayları yerine.  
  
 Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> olan `false`. Çağrı <xref:System.Windows.Forms.ContainerControl.Validate%2A> formunuzda doğrulama gerçekleştirmek için açıkça.  
  
#### <a name="layout"></a>Düzen  
 Denetim <xref:System.Windows.Forms.ToolStrip> üyelerini birini seçerek düzeni <xref:System.Windows.Forms.ToolStripLayoutStyle> ile <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> özelliği.  
  
##### <a name="stack-layouts"></a>Yığın düzeni  
 Yığınlama olan öğelerin birbiriyle yanında her iki ucundaki düzenleme <xref:System.Windows.Forms.ToolStrip>. Aşağıdaki listede yığın düzenleri açıklanmaktadır.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>varsayılandır. Bu ayar neden <xref:System.Windows.Forms.ToolStrip> otomatik olarak ile uyumlu olarak düzenini değiştirmek için <xref:System.Windows.Forms.ToolStrip.Orientation%2A> sürükleme ve senaryoları yerleştirme işlemek için özellik.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>işler <xref:System.Windows.Forms.ToolStrip> diğer dikey öğeler.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>işler <xref:System.Windows.Forms.ToolStrip> diğer yatay öğeler.  
  
##### <a name="other-features-of-stack-layouts"></a>Yığın düzeni diğer özellikleri  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>sonuna belirler <xref:System.Windows.Forms.ToolStrip> öğesi hizalandığı için.  
  
 Ne zaman öğe değil sığar içinde <xref:System.Windows.Forms.ToolStrip>, taşma düğmesini otomatik olarak görünür. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Özelliği ayarı, bir öğe gerektiği gibi her zaman ya da hiç taşma alanında görünüp görünmeyeceğini belirler.  
  
 İçinde <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayı incelemek <xref:System.Windows.Forms.ToolStripItem.Placement%2A> bir öğe üzerinde ana yerleştirilmiş olup olmadığını belirlemek için özellik <xref:System.Windows.Forms.ToolStrip>, taşma <xref:System.Windows.Forms.ToolStrip>, ya da şu anda hiç görünmüyorsa. Öğe ana sığmadı neden bir öğe görüntülenmez tipik nedenler: <xref:System.Windows.Forms.ToolStrip> ve kendi <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliği ayarlandığı <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Olun bir <xref:System.Windows.Forms.ToolStrip> koyarak taşınabilir bir <xref:System.Windows.Forms.ToolStripPanel> ve ayarı kendi <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> için <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Diğer Düzen Seçenekleri  
 Bir düzen seçenekleri <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> ve <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Akış düzeni  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>Düzen olduğu için varsayılan <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, ve <xref:System.Windows.Forms.ToolStripOverflow>. Aşağıdakine benzer <xref:System.Windows.Forms.FlowLayoutPanel>. Özelliklerini <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> düzeni aşağıdaki gibidir:  
  
-   Tüm özelliklerini <xref:System.Windows.Forms.FlowLayoutPanel> tarafından sunulan <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> özelliği. Cast gerekir <xref:System.Windows.Forms.LayoutSettings> sınıfının bir <xref:System.Windows.Forms.FlowLayoutSettings> sınıfı.  
  
-   Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripItem.Dock%2A> ve <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> satırdaki öğeleri hizalamak için kod özelliklerinde.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yoksayılır.  
  
-   İçinde <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayı incelemek <xref:System.Windows.Forms.ToolStripItem.Placement%2A> bir öğe üzerinde ana yerleştirilmiş olup olmadığını belirlemek için özellik <xref:System.Windows.Forms.ToolStrip> veya değil uygun.  
  
-   Tutamacı işlenmez, bu nedenle bir <xref:System.Windows.Forms.ToolStrip> içinde <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> düzen stili bir <xref:System.Windows.Forms.ToolStripPanel> taşınamaz.  
  
-   <xref:System.Windows.Forms.ToolStrip> Taşma düğmesini değil işlenmiş ve <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> göz ardı edilir.  
  
##### <a name="table-layout"></a>Tablo düzeni  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>Düzen olduğu için varsayılan <xref:System.Windows.Forms.StatusStrip>. Aşağıdakine benzer <xref:System.Windows.Forms.TableLayoutPanel>. Özelliklerini <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> düzeni aşağıdaki gibidir:  
  
-   Tüm özelliklerini <xref:System.Windows.Forms.TableLayoutPanel> tarafından sunulan <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> özelliği. Cast gerekir <xref:System.Windows.Forms.LayoutSettings> sınıfının bir <xref:System.Windows.Forms.TableLayoutSettings> sınıfı.  
  
-   Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripItem.Dock%2A> ve <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> tablo hücresi içinde öğeleri hizalamak için kod özelliklerinde.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yoksayılır.  
  
-   İçinde <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayı incelemek <xref:System.Windows.Forms.ToolStripItem.Placement%2A> bir öğe üzerinde ana yerleştirilmiş olup olmadığını belirlemek için özellik <xref:System.Windows.Forms.ToolStrip> veya değil uygun.  
  
-   Tutamacı işlenmez, bu nedenle bir <xref:System.Windows.Forms.ToolStrip> içinde <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> düzen stili bir <xref:System.Windows.Forms.ToolStripPanel> taşınamaz.  
  
-   <xref:System.Windows.Forms.ToolStrip> Taşma düğmesini değil işlenmiş ve <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> göz ardı edilir.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 Aşağıdaki konularda açıklanmıştır <xref:System.Windows.Forms.ToolStripItem> ve bu sınıftan türetilen denetimler.  
  
 <xref:System.Windows.Forms.ToolStripItem>yerleştirilmesini tüm öğeleri için Özet temel sınıf bir <xref:System.Windows.Forms.ToolStrip>. Aşağıdaki nesne modeli gösterilmektedir <xref:System.Windows.Forms.ToolStripItem> Devralma Hiyerarşisi.  
  
 ![ToolStripItem nesne modeli](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.gif "ToolStripItemObjectModel")  
ToolStripItem nesne modeli  
  
 <xref:System.Windows.Forms.ToolStripItem>sınıflar ya da devral doğrudan <xref:System.Windows.Forms.ToolStripItem>, ya da bunlar dolaylı olarak devralınmalıdır <xref:System.Windows.Forms.ToolStripItem> aracılığıyla <xref:System.Windows.Forms.ToolStripControlHost> veya <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem>denetimleri bulunan, içinde bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, veya <xref:System.Windows.Forms.ContextMenuStrip> ve forma doğrudan eklenemez. Çeşitli kapsayıcı sınıfları uygun bir alt kümesini içerecek şekilde tasarlanmıştır <xref:System.Windows.Forms.ToolStripItem> kontrol eder.  
  
 Aşağıdaki tabloda hisse senedi listeler <xref:System.Windows.Forms.ToolStripItem> denetimleri ve hangi göründükleri en iyi kapsayıcıları. Herhangi bir rağmen <xref:System.Windows.Forms.ToolStrip> öğesi barındırılması birinde <xref:System.Windows.Forms.ToolStrip>-kapsayıcı, türetilmiş bu öğeler aşağıdaki kapsayıcılarındaki en iyi aramak için tasarlanmıştır:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown>Tasarımcı Araç Kutusu'nda görünmez.  
  
|Kapsanan öğesi|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|Evet|Hayır|Hayır|Hayır|Evet|  
|<xref:System.Windows.Forms.ToolStripComboBox>|Evet|Evet|Evet|Hayır|Evet|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Evet|Hayır|Hayır|Evet|Evet|  
|<xref:System.Windows.Forms.ToolStripLabel>|Evet|Hayır|Hayır|Evet|Evet|  
|<xref:System.Windows.Forms.ToolStripSeparator>|Evet|Evet|Evet|Hayır|Evet|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Evet|Hayır|Hayır|Evet|Evet|  
|<xref:System.Windows.Forms.ToolStripTextBox>|Evet|Evet|Evet|Hayır|Evet|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Hayır|Evet|Evet|Hayır|Hayır|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Hayır|Hayır|Hayır|Evet|Hayır|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Evet|Hayır|Hayır|Evet|Hayır|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Evet|Evet|Hayır|Evet|Evet|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton>Düğme öğesi için <xref:System.Windows.Forms.ToolStrip>. İle çeşitli kenarlık stilleri görüntülemek ve temsil eder ve İşlemsel durumlar etkinleştirmek için kullanın. Varsayılan olarak odağı olmasını da tanımlayabilirsiniz.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> Etiket işlevsellik sağlar <xref:System.Windows.Forms.ToolStrip> kontrol eder. <xref:System.Windows.Forms.ToolStripLabel> Benzer bir <xref:System.Windows.Forms.ToolStripButton> , odak varsayılan olarak almaz ve bu değil işlemek basılmış veya vurgulanan olarak.  
  
 <xref:System.Windows.Forms.ToolStripLabel>barındırılan bir öğe olarak erişim anahtarları destekler.  
  
 Kullanım <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, ve <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> özellikleri bir <xref:System.Windows.Forms.ToolStripLabel> bağlantı denetiminde desteklemek için bir <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel>bir sürümü <xref:System.Windows.Forms.ToolStripLabel> kullanmak için özellikle tasarlanmış <xref:System.Windows.Forms.StatusStrip>. Özel Özellikler <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, ve <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> Bir araç veya yönlendirmesini bağlı olarak menü dikey veya yatay çizgi ekler. Gruplandırması veya gibi bu menüdeki öğeler arasında ayrım sağlar.  
  
 Ekleyebileceğiniz bir <xref:System.Windows.Forms.ToolStripSeparator> aşağı açılan listeden seçerek tasarım zamanında. Ancak, aynı zamanda otomatik olarak oluşturabileceğiniz bir <xref:System.Windows.Forms.ToolStripSeparator> bir tire (-) Tasarımcısı şablonu düğümünde ya da buna yazarak <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> yöntemi.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost>için Özet temel sınıf <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost>özel denetimler, iki yolla dahil, diğer denetimler barındırabilir:  
  
-   Oluşturmak bir <xref:System.Windows.Forms.ToolStripControlHost> türeyen bir sınıf ile <xref:System.Windows.Forms.Control>. Barındırılan denetim ve özellikleri tam olarak erişmek için atamalısınız <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> özelliğine geri gerçek sınıf onu temsil eder.  
  
-   Genişletme <xref:System.Windows.Forms.ToolStripControlHost>ve türeyen bir sınıf geçirme temel sınıf oluşturucu devralınan sınıfın varsayılan bir oluşturucu, arama <xref:System.Windows.Forms.Control>. Bu seçenek, ortak denetim yöntemleri ve özellikleri kolay erişim için Kaydır sağlar bir <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox>olan <xref:System.Windows.Forms.ComboBox> içinde barındırmak için en iyi hale getirilmiş bir <xref:System.Windows.Forms.ToolStrip>. Konumunda barındırılan denetimin özellikleri ve olayları bir alt kümesini açığa <xref:System.Windows.Forms.ToolStripComboBox> düzeyi, ancak temel <xref:System.Windows.Forms.ComboBox> denetimidir üzerinden erişilebilir tam olarak <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> özelliği.  
  
### <a name="toolstriptextbox"></a>Toolstrip'nin  
 <xref:System.Windows.Forms.ToolStripTextBox>olan <xref:System.Windows.Forms.TextBox> içinde barındırmak için en iyi hale getirilmiş bir <xref:System.Windows.Forms.ToolStrip>. Konumunda barındırılan denetimin özellikleri ve olayları bir alt kümesini açığa <xref:System.Windows.Forms.ToolStripTextBox> düzeyi, ancak temel <xref:System.Windows.Forms.TextBox> denetimidir üzerinden erişilebilir tam olarak <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> özelliği.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar>olan <xref:System.Windows.Forms.ProgressBar> içinde barındırmak için en iyi hale getirilmiş bir <xref:System.Windows.Forms.ToolStrip>. Konumunda barındırılan denetimin özellikleri ve olayları bir alt kümesini açığa <xref:System.Windows.Forms.ToolStripProgressBar> düzeyi, ancak temel <xref:System.Windows.Forms.ProgressBar> denetimidir üzerinden erişilebilir tam olarak <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> özelliği.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem>için Özet temel sınıf <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ve <xref:System.Windows.Forms.ToolStripSplitButton>, hangi barındırabilir öğeleri doğrudan veya bir açılan kapsayıcıda konak ek öğeleri. Ayarlayarak bunu <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> özelliğine bir <xref:System.Windows.Forms.ToolStripDropDown> ve ayarı <xref:System.Windows.Forms.ToolStrip.Items%2A> özelliği <xref:System.Windows.Forms.ToolStripDropDown>. Bu aşağı açılan öğeler doğrudan aracılığıyla erişim <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> özelliği.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem>olan bir <xref:System.Windows.Forms.ToolStripDropDownItem> ile birlikte çalışır <xref:System.Windows.Forms.ToolStripDropDownMenu> ve <xref:System.Windows.Forms.ContextMenuStrip> menüleri özel vurgulama, Düzen ve sütun düzenlemeyi işlemek için.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton>gibi görünüyor <xref:System.Windows.Forms.ToolStripButton>, ancak kullanıcı tıkladığında açılır alanı gösterir. Aşağı açılan okunu ayarlayarak göstermek veya gizlemek <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> özelliği. <xref:System.Windows.Forms.ToolStripDropDownButton>ana bilgisayarlar bir <xref:System.Windows.Forms.ToolStripOverflowButton> taşması öğeleri görüntüler <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>Verileceğini  
 <xref:System.Windows.Forms.ToolStripSplitButton>düğmesini ve açılan düğme işlevleri bir araya getirir.  
  
 Kullanım <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> eşitlemek için özellik <xref:System.Windows.Forms.Control.Click> düğmeyi gösterilen öğenin ile seçilen açılan öğesinin olay.  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem genel özellikleri  
 <xref:System.Windows.Forms.ToolStripItem>Aşağıdaki genel özellikleri ve denetimleri devralma seçenekleri sağlar:  
  
-   Çekirdek olayları  
  
-   Görüntü işleme  
  
-   Hizalama  
  
-   Metin ve resim arasındaki ilişki  
  
-   Görüntü stili  
  
#### <a name="core-events"></a>Çekirdek olayları  
 <xref:System.Windows.Forms.ToolStripItem>denetimleri kendi tıklatın, fare ve boyama olayları alır ve aynı zamanda ön işleme bazı klavye gerçekleştirebilirsiniz.  
  
#### <a name="image-handling"></a>Görüntü işleme  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, Ve <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> özellikleri görüntü işleme çeşitli yönlerini ilgilidir. Resimleri kullanmak <xref:System.Windows.Forms.ToolStrip> denetimleri doğrudan bu özellikleri ayarlama veya çalışma zamanı – yalnızca ayarlayarak <xref:System.Windows.Forms.ToolStrip.ImageList%2A> özelliği.  
  
 Resim ölçekleme özelliklerini hem de etkileşim tarafından belirlenir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripItem>aşağıdaki gibi:  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>görüntünün birleşimi tarafından belirlendiği şekilde nihai görüntüsünün ölçek <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> ayarı ve kapsayıcının <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> ayarı.  
  
    -   Varsa <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> olan `true` (varsayılan) ve <xref:System.Windows.Forms.ToolStripItemImageScaling> olan <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, hiçbir görüntü ölçeklendirme oluşur ve <xref:System.Windows.Forms.ToolStrip> boyutu en büyük öğeyi veya önceden belirlenmiş bir minimum boyut olan.  
  
    -   Varsa <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> olan `false` ve <xref:System.Windows.Forms.ToolStripItemImageScaling> olan <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, hiçbiri görüntü ya da <xref:System.Windows.Forms.ToolStrip> ölçeklendirme oluşur.  
  
#### <a name="alignment"></a>Hizalama  
 Değeri <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> özelliği belirler sonuna <xref:System.Windows.Forms.ToolStrip> öğeyi göründüğü adresindeki. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yalnızca çalışır düzen stilini <xref:System.Windows.Forms.ToolStrip> yığın taşması değerlerden birine ayarlayın.  
  
 Öğeler üzerinde yerleştirilir <xref:System.Windows.Forms.ToolStrip> öğeler öğeleri koleksiyonunda görünür sırayla. Bir öğe burada yerleştirilmeden programlı olarak değiştirmek için kullanın <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> öğeyi koleksiyonda taşımak için yöntem. Bu yöntem öğesi taşır, ancak bunu çoğaltmaz.  
  
#### <a name="text-and-image-relationship"></a>Metin ve görüntü ilişkisi  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Özelliği üzerinde görüntünün metin göre göreli yerleşimini tanımlayan bir <xref:System.Windows.Forms.ToolStripItem>. Görüntü, metin ya da her ikisini de eksikliği öğeleri özel durumlar kabul edilir şekilde <xref:System.Windows.Forms.ToolStripItem> eksik veya birden çok öğe için boş bir nokta görüntülemez.  
  
#### <a name="display-style"></a>Görüntü stili  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>bir öğenin metin ve görüntü özelliklerini değerlerini istediğinizi yalnızca görüntülenirken ayarlamanıza olanak sağlar. Bu genellikle yalnızca görüntüle stil aynı öğe farklı bir bağlamda gösterilirken değiştirmek için kullanılır.  
  
## <a name="accessory-classes"></a>Aksesuar sınıfları  
 Diğer çeşitli işlevleri sağlayan sınıflar içerir:  
  
-   <xref:System.Windows.Forms.ToolStripManager>destekleyen <xref:System.Windows.Forms.ToolStrip>-ilgili görevleri birleştirme, ayarları ve Oluşturucu seçenekleri gibi tüm uygulamalar için.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>belirli bir stili veya tema uygulamanıza imkan sağlayan bir <xref:System.Windows.Forms.ToolStrip> kolayca.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer>kalemler ve değiştirebilen renk tabloyu temel alan Fırçalar oluşturur (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer>Sistem renklerini ve düz görsel bir stil geçerlidir <xref:System.Windows.Forms.ToolStrip> uygulamalar.  
  
-   <xref:System.Windows.Forms.ToolStripContainer>benzer <xref:System.Windows.Forms.SplitContainer>. Dört yerleşik yan paneller kullanır (örneklerini <xref:System.Windows.Forms.ToolStripPanel>) ve bir merkezi paneli (örneği <xref:System.Windows.Forms.ToolStripContentPanel>) tipik bir düzenleme oluşturmak için. Yan Panelleri kaldırılamıyor, ancak bunları gizleyebilirsiniz. Kaldırma ne merkezi masasını gizle. Bir veya daha fazla düzenleyebilirsiniz <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, veya <xref:System.Windows.Forms.StatusStrip> yan paneller ve denetimleri, diğer denetimler için merkezi Masası'nı kullanabilirsiniz. <xref:System.Windows.Forms.ToolStripContentPanel> De tutarlı bir görünüm için formunun gövdesine Oluşturucu destek almak için bir yol sağlar. <xref:System.Windows.Forms.ToolStripContainer>birden çok belge arabirimi (MDI) desteklemez.  
  
-   <xref:System.Windows.Forms.ToolStripPanel>taşıma ve düzenleme için alan sağlar <xref:System.Windows.Forms.ToolStrip> kontrol eder. Bu nedenle seçerseniz, yalnızca bir panelini kullanabilirsiniz ve <xref:System.Windows.Forms.ToolStripPanel> iyi MDI senaryolarında çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ToolStrip denetimine genel bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip Teknoloiji özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)  
 [ToolStrip denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [MenuStrip denetimi](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [StatusStrip denetimi](../../../../docs/framework/winforms/controls/statusstrip-control.md)  
 [ContextMenuStrip denetimi](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)  
 [BindingNavigator denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
