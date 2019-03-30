---
title: ToolStrip Denetim Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: bede247ca9e1c2c20ffc8fef9fd4fab89aa78453
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654776"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip Denetim Mimarisi
<xref:System.Windows.Forms.ToolStrip> Ve <xref:System.Windows.Forms.ToolStripItem> sınıfları, araç, durum ve menü öğeleri görüntülemek için esnek, Genişletilebilir bir sistem sağlar. Bu sınıfların tümü bulunur <xref:System.Windows.Forms> ad alanı ve bunların tümü genellikle adlandırılır "ToolStrip" ön ekine sahip (gibi <xref:System.Windows.Forms.ToolStripOverflow>) veya "Şeridinde" soneki ile (gibi <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 Aşağıdaki konularda açıklanmıştır <xref:System.Windows.Forms.ToolStrip> ve ondan türetilen denetimler.  
  
 <xref:System.Windows.Forms.ToolStrip> soyut temel sınıf için <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, ve <xref:System.Windows.Forms.ContextMenuStrip>. Aşağıdaki nesne modeli gösterir <xref:System.Windows.Forms.ToolStrip> Devralma Hiyerarşisi.  
  
 ![ToolStrip nesne modelini gösteren diyagram.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)  
  
 Tüm öğeleri erişebileceğiniz bir <xref:System.Windows.Forms.ToolStrip> aracılığıyla <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonu. Tüm öğeleri erişebileceğiniz bir <xref:System.Windows.Forms.ToolStripDropDownItem> aracılığıyla <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> koleksiyonu. Türetilen bir sınıfta <xref:System.Windows.Forms.ToolStrip>, ayrıca <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> görüntülenmekte olan öğelere erişmek için özelliği. Bu bir taşma menüde olmayan bilgilerdir.  
  
 Aşağıdaki öğeler ile her ikisini de sorunsuz çalışacak şekilde özel olarak tasarlanmış <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleri içinde. Tasarım zamanında için varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.ToolStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> yerine geçen en üst düzey kapsayıcı <xref:System.Windows.Forms.MainMenu>. Anahtar işleme ve birden çok belge arabirimi (MDI) özellikler de sağlar. İşlevsellik, <xref:System.Windows.Forms.ToolStripDropDownItem> ve <xref:System.Windows.Forms.ToolStripMenuItem> ile birlikte çalışma <xref:System.Windows.Forms.MenuStrip>, ancak bunlar türetilmiştir <xref:System.Windows.Forms.ToolStripItem>.  
  
 Aşağıdaki öğeler ile her ikisini de sorunsuz çalışacak şekilde özel olarak tasarlanmış <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleri içinde. Tasarım zamanında için varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.MenuStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> değiştirir <xref:System.Windows.Forms.StatusBar> denetimi. Özel özellikleri <xref:System.Windows.Forms.StatusStrip> özel tablo düzeni dahil, formun boyutlandırma ve taşıma GRIPS, desteği ve `Spring` veren özelliği, bir <xref:System.Windows.Forms.ToolStripStatusLabel> otomatik olarak kullanılabilir alanı dolduracak şekilde.  
  
 Aşağıdaki öğeler ile her ikisini de sorunsuz çalışacak şekilde özel olarak tasarlanmış <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleri içinde. Tasarım zamanında için varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.StatusStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> değiştirir <xref:System.Windows.Forms.ContextMenu>. İlişkilendirebilirsiniz bir <xref:System.Windows.Forms.ContextMenuStrip> herhangi bir denetimi ve sağ fare tıklatın otomatik olarak bağlam menüsünden (veya kısayol menüsünden) görüntüler. Göstermek bir <xref:System.Windows.Forms.ContextMenuStrip> kullanarak program aracılığıyla <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> yöntemi. <xref:System.Windows.Forms.ContextMenuStrip> İptal edilebilen destekler <xref:System.Windows.Forms.ToolStripDropDown.Opening> ve <xref:System.Windows.Forms.ToolStripDropDown.Closing> dinamik nüfus ve birden çok tıklamayla senaryoları işlemek için olayları. <xref:System.Windows.Forms.ContextMenuStrip> görüntüleri, menü öğesi denetim durumu, metin, erişim anahtarları, kısayolları ve basamaklı menüler destekler.  
  
 Aşağıdaki öğeler ile her ikisini de sorunsuz çalışacak şekilde özel olarak tasarlanmış <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönleri içinde. Tasarım zamanında için varsayılan olarak kullanılabilir olmaları <xref:System.Windows.Forms.ContextMenuStrip> denetimi:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip genel özellikleri  
 Aşağıdaki konularda, özellikler ve için genel davranış açıklanmaktadır <xref:System.Windows.Forms.ToolStrip> ve denetimleri türetilmiş.  
  
#### <a name="painting"></a>Boyama  
 Özel boyama yapabileceğiniz <xref:System.Windows.Forms.ToolStrip> çeşitli şekillerde denetimleri. Diğer Windows Formları denetimleri olduğu gibi <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripItem> her ikisi de geçersiz kılınabilir sahip `OnPaint` yöntemleri ve `Paint` olayları. Normal boyama, denetimin istemci alanı göreli koordinat sistemi olduğundan; diğer bir deyişle, denetimin sol üst köşesinde 0 ' dır 0. `Paint` Olay ve `OnPaint` yöntemi için bir <xref:System.Windows.Forms.ToolStripItem> diğer denetim boyama olayları gibi davranır.  
  
 <xref:System.Windows.Forms.ToolStrip> Denetimleri de öğeleri ve kapsayıcı ile daha hassas erişim sağlar <xref:System.Windows.Forms.ToolStripRenderer> boyama arka plan, öğe arka plan, öğesi resmi, öğe ok, öğesi metni için geçersiz kılınabilir yönteme sahip, sınıf ve kenarlığı <xref:System.Windows.Forms.ToolStrip>. Bu yöntemleri için olay bağımsız değişkenleri dikdörtgenler renkleri ve istediğiniz gibi ayarlayabilirsiniz metin biçimleri gibi çeşitli özellikler kullanıma sunar.  
  
 Bir öğenin nasıl boyanacağını birkaç yönden ayarlamak için genellikle geçersiz kılmanız <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Yeni bir öğe yazma ve bir boyama tüm yönlerini denetlemek isterseniz, geçersiz kılma `OnPaint` yöntemi. İçinden `OnPaint`, yöntemlerinden kullanabileceğiniz <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip> yararlanarak arabelleğe çift olduğu <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> ayarı.  
  
#### <a name="parenting"></a>Üst öğe oluşturma  
 Kapsayıcı sahiplik ile ana öğe kavramı daha karmaşık <xref:System.Windows.Forms.ToolStrip> diğer Windows Forms kapsayıcı denetimlerinde denetimleri daha. Taşma, birden çok açılan öğelerini paylaşma gibi dinamik senaryoları desteklemek için gerekli olan <xref:System.Windows.Forms.ToolStrip> öğeleri ve oluşturulmasını desteklemek için bir <xref:System.Windows.Forms.ContextMenuStrip> kontrolü.  
  
 Aşağıdaki listede ana öğe için ilgili üyeleri ve bunların kullanımını açıklar.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> Kaynak açılır öğesi öğe erişir. Bu benzer <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ancak bir denetim döndürmek yerine döndürür bir <xref:System.Windows.Forms.ToolStripItem>.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> Kaynak denetimdir belirler, <xref:System.Windows.Forms.ContextMenuStrip> ne zaman birden çok denetim paylaşmak aynı <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> salt okunur bir erişimcisi için <xref:System.Windows.Forms.ToolStripItem.Parent%2A> özelliği. Döndürülen geçerli bir üst gösterir, bir üst bir sahibinden farklı <xref:System.Windows.Forms.ToolStrip> öğesi, hangi taşma alanında olabilir görüntülendiği içinde.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> döndürür <xref:System.Windows.Forms.ToolStrip> geçerli olan öğeleri koleksiyonu içerir <xref:System.Windows.Forms.ToolStripItem>. Başvurmak için en iyi yolu budur <xref:System.Windows.Forms.ToolStrip.ImageList%2A> veya diğer üst düzey özellikleri <xref:System.Windows.Forms.ToolStrip> taşma işlemek için özel kod yazmadan.  
  
#### <a name="behavior-of-inherited-controls"></a>Devralınan denetimler davranışı  
 Devralma işleminde kullanılan her durumda aşağıdaki denetimleri kilitli:  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel> panellerinde içeren bir <xref:System.Windows.Forms.ToolStripContainer> ve aynı zamanda bireysel <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.  
  
 Örneğin, önceki listesinde bir veya birden fazla denetimin'ı kullanarak yeni bir Windows Forms uygulaması oluşturun. Bir veya daha fazla denetim için erişim değiştiricisi ayarlamak `public` veya `protected`ve ardından projeyi derleyin. İlk formundan devralan bir form ekleyin ve ardından devralınan bir denetim seçin. Denetim, kendi erişim değiştiricisi olduysa gibi davrandığından, kilitli görünür `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer destek devralma  
 <xref:System.Windows.Forms.ToolStripContainer> Denetimini destekler sınırlı devralınan senaryoları, aşağıdaki örneğe benzer:  
  
1.  Yeni bir Windows Forms uygulaması oluşturun.  
  
2.  Ekleme bir <xref:System.Windows.Forms.ToolStripContainer> form.  
  
3.  Erişim değiştiricisi ayarlamak <xref:System.Windows.Forms.ToolStripContainer> için `public` veya `protected`.  
  
4.  Herhangi bir birleşimini ekleme <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.ContextMenuStrip> için denetimleri <xref:System.Windows.Forms.ToolStripPanel> bölgeleri <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Projeyi oluşturun.  
  
6.  İlk formundan devralan bir form ekleyin.  
  
7.  Devralınan seçin <xref:System.Windows.Forms.ToolStripContainer> form üzerinde.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Alt denetimlerin devralınan davranışı  
 Önceki adımları tamamladıktan sonra devralınan aşağıdaki davranış gerçekleşir:  
  
-   Tasarımcıda denetim devralınan bir simge ile görünür.  
  
-   <xref:System.Windows.Forms.ToolStripPanel> Denetimler kilitli; seçin veya bunların içeriğini yeniden düzenleyin.  
  
-   Denetimlere ekleyebilirsiniz <xref:System.Windows.Forms.ToolStripContentPanel>denetimleri taşımak ve alt denetimlerin okunmaları <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Form oluşturduktan sonra değişiklikleriniz kaydedilir.  
  
    > [!NOTE]
    >  Erişim değiştiricileri tümünden kaldırmak <xref:System.Windows.Forms.ToolStripPanel> parçası olan denetimler bir <xref:System.Windows.Forms.ToolStripContainer>. Erişim değiştiricisi <xref:System.Windows.Forms.ToolStripContainer> tam denetim yönetir.  
  
#### <a name="partial-trust"></a>Kısmi Güven  
 Sınırlamaları `ToolStrip`s kısmi güven altında kişisel bilgilerin yetkisiz kişiler veya hizmetler tarafından kullanılabilecek yanlışlıkla girişini engellemek için tasarlanmıştır. Koruyucu ölçüleri aşağıdaki gibidir:  
  
-   `ToolStripDropDown` denetimleri gerekli kıl <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> öğeleri görüntülemek için bir <xref:System.Windows.Forms.ToolStripControlHost>. Bu gibi her iki iç denetimleri için geçerlidir <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar> de kullanıcı tarafından oluşturulan farklı olarak. Bu gereksinim karşılanmadığı durumda, bu öğeler görüntülenmez. Hiçbir özel durum oluşturulur.  
  
-   Ayarı <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> özelliğini `false` izin verilmiyor ve iptal edilebilir <xref:System.Windows.Forms.ToolStripDropDown.Closing> olay parametresi yok sayıldı. Bu, birden fazla tuş vuruşu açılan öğe kapatılıyor olmadan girin mümkün kılar. Bu gereksinim karşılanmazsa gibi öğeleri görüntülenmez. Hiçbir özel durum oluşturulur.  
  
-   Kısmi güven bağlamlarda dışında meydana gelirse olayları işleme birçok tuş vuruşu harekete Geçirilmemesi <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
-   Erişim anahtarlarını olmayan zaman işlenen <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> verilmemiştir.  
  
#### <a name="usage"></a>Kullanım  
 Aşağıdaki kullanım düzenlerine sahip bir boşluğunu <xref:System.Windows.Forms.ToolStrip> düzen, klavye etkileşim ve son kullanıcı davranışı:  
  
-   Birleşik bir <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip> İçinde konumlandırılabilir <xref:System.Windows.Forms.ToolStripPanel> ve çapraz <xref:System.Windows.Forms.ToolStripPanel>s. `Dock` Özelliği yoksayılır ve <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliği `false`, boyutu <xref:System.Windows.Forms.ToolStrip> öğeleri eklendikçe büyür <xref:System.Windows.Forms.ToolStripPanel>. Genellikle, <xref:System.Windows.Forms.ToolStrip> sekme sırasının yer almaz.  
  
-   Yuvalanmış  
  
     <xref:System.Windows.Forms.ToolStrip> Bir tarafı sabit bir konum bir kapsayıcıda yerleştirilir ve, yerleştirilmiş tüm edge boyutuna genişletir. Genellikle, <xref:System.Windows.Forms.ToolStrip> sekme sırasının yer almaz.  
  
-   Mutlak konumlu  
  
     <xref:System.Windows.Forms.ToolStrip> Tarafından yerleştirilen diğer denetimler gibi olmamasıdır <xref:System.Windows.Forms.Control.Location%2A> özelliği, sabit bir boyutu vardır ve genellikle sekme sırasının katılır.  
  
#### <a name="keyboard-interaction"></a>Klavye etkileşimi  
  
##### <a name="access-keys"></a>Erişim anahtarları  
 Aşağıdaki ALT tuşunu veya ile birleştirildiğinde, erişim anahtarlarını klavyeyi kullanarak denetim etkinleştirmek için bir yoludur. <xref:System.Windows.Forms.ToolStrip> Her iki açık ve örtük erişim anahtarlarını destekliyor. Açık tanımı bir ampersan (&) karakteri harf önceki kullanır. Örtük tanımını bazında karakter tabanlı bir eşleşen öğeyi bulmak için çalışır bir algoritma kullanan bir verilen `Text` özelliği.  
  
##### <a name="shortcut-keys"></a>Kısayol Tuşları  
 Tarafından kullanılan kısayol tuşları bir <xref:System.Windows.Forms.MenuStrip> bir birleşimini kullanmak <xref:System.Windows.Forms.Keys> (Bu siparişi özgü değildir) numaralandırma kısayol tuşunu tanımlamak için. Ayrıca <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> "Sil" yerine "Del" görüntüleme gibi bir kısayol tuşu ile yalnızca, metin görüntülenecek özelliği  
  
##### <a name="navigation"></a>Gezinti  
 ALT tuşuna etkinleştirir <xref:System.Windows.Forms.MenuStrip> işaret ettiği <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Burada, CTRL + SEKME arasında gezinir. <xref:System.Windows.Forms.ToolStrip> içindeki denetimleri `ToolStripPanel`s. Sekme tuşunu ve ok tuşları sayısal klavyede bulunan öğeler arasındaki gidin bir <xref:System.Windows.Forms.ToolStrip>. Özel bir algoritma taşma bölgede Gezinti işler. BOŞLUK seçen bir <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, veya <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Odak ve doğrulama  
 ALT anahtarının etkinleştirildiğinde <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ToolStrip> genellikle ne olması ya da o anda odağı içeren denetim odağı kaldırın. İçinde barındırılan bir denetim olup olmadığını <xref:System.Windows.Forms.MenuStrip> veya bir açılan <xref:System.Windows.Forms.MenuStrip>, Denetim odak kullanıcı TAB tuşuna bastığında kazanır. Genel olarak, <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, ve <xref:System.Windows.Forms.Control.Leave> olayları <xref:System.Windows.Forms.MenuStrip> klavye tarafından etkinleştirildiğinde oluşmayabilir. Böyle durumlarda kullanmak <xref:System.Windows.Forms.MenuStrip.MenuActivate> ve <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> olayları yerine.  
  
 Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> olduğu `false`. Çağrı <xref:System.Windows.Forms.ContainerControl.Validate%2A> formunuzdaki doğrulamayı gerçekleştirmek için açıkça.  
  
#### <a name="layout"></a>Düzen  
 Denetim <xref:System.Windows.Forms.ToolStrip> üyelerinin birini seçerek Düzen <xref:System.Windows.Forms.ToolStripLayoutStyle> ile <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> özelliği.  
  
##### <a name="stack-layouts"></a>Yığın düzeni  
 Yığınlama olan öğelerin birbiriyle yanında her iki ucunda düzenleme <xref:System.Windows.Forms.ToolStrip>. Aşağıdaki listede, yığın düzeni açıklanmaktadır.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> varsayılandır. Bu ayar neden <xref:System.Windows.Forms.ToolStrip> otomatik olarak dağıtabilirler düzenini değiştirmek için <xref:System.Windows.Forms.ToolStrip.Orientation%2A> sürükleme ve senaryoları yerleştirme işlemek için özellik.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> işler <xref:System.Windows.Forms.ToolStrip> diğer dikey öğeleri.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> işler <xref:System.Windows.Forms.ToolStrip> diğer yatay öğeleri.  
  
##### <a name="other-features-of-stack-layouts"></a>Yığın düzeni ilişkin diğer özellikleri  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> sonuna belirler <xref:System.Windows.Forms.ToolStrip> hizalandığı öğesi için.  
  
 Ne zaman öğeleri olmayan uygun içinde <xref:System.Windows.Forms.ToolStrip>, taşma düğmesini otomatik olarak görünür. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Özelliği ayarı, bir öğeyi gerektiği gibi her zaman ya da hiç taşma alanında görünüp görünmeyeceğini belirler.  
  
 İçinde <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayı İnceleme <xref:System.Windows.Forms.ToolStripItem.Placement%2A> bir öğe üzerinde ana yerleştirilmiş olup olmadığını belirlemek için özellik <xref:System.Windows.Forms.ToolStrip>, taşma <xref:System.Windows.Forms.ToolStrip>, ya da şu anda hiç görünmüyorsa. Neden bir öğenin gösterilmesi için tipik öğesi üzerinde ana sığmadı nedenleri <xref:System.Windows.Forms.ToolStrip> ve kendi <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliğinin ayarlandığı <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Olun bir <xref:System.Windows.Forms.ToolStrip> koyarak taşınabilir bir <xref:System.Windows.Forms.ToolStripPanel> ve ayarı kendi <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> için <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Diğer Düzen Seçenekleri  
 Diğer düzen Seçenekler <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> ve <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Akış düzeni  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> Düzen, varsayılan için <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, ve <xref:System.Windows.Forms.ToolStripOverflow>. Benzer <xref:System.Windows.Forms.FlowLayoutPanel>. Özelliklerinin <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> Düzen aşağıdaki gibidir:  
  
-   Tüm özelliklerini <xref:System.Windows.Forms.FlowLayoutPanel> tarafından kullanıma sunulan <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> özelliği. Dönüştürmelisiniz <xref:System.Windows.Forms.LayoutSettings> sınıfının bir <xref:System.Windows.Forms.FlowLayoutSettings> sınıfı.  
  
-   Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripItem.Dock%2A> ve <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> satır içinde öğeleri hizalamak için kod özellikleri.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yok sayılır.  
  
-   İçinde <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayı İnceleme <xref:System.Windows.Forms.ToolStripItem.Placement%2A> bir öğe üzerinde ana yerleştirilmiş olup olmadığını belirlemek için özellik <xref:System.Windows.Forms.ToolStrip> veya uygun olmayan.  
  
-   Tutamacı işlenmez ve bu nedenle bir <xref:System.Windows.Forms.ToolStrip> içinde <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> düzen stili bir <xref:System.Windows.Forms.ToolStripPanel> taşınamaz.  
  
-   <xref:System.Windows.Forms.ToolStrip> Taşma düğmesini değil işlenen ve <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> göz ardı edilir.  
  
##### <a name="table-layout"></a>Tablo düzeni  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> Düzen, varsayılan için <xref:System.Windows.Forms.StatusStrip>. Benzer <xref:System.Windows.Forms.TableLayoutPanel>. Özelliklerinin <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> Düzen aşağıdaki gibidir:  
  
-   Tüm özelliklerini <xref:System.Windows.Forms.TableLayoutPanel> tarafından kullanıma sunulan <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> özelliği. Dönüştürmelisiniz <xref:System.Windows.Forms.LayoutSettings> sınıfının bir <xref:System.Windows.Forms.TableLayoutSettings> sınıfı.  
  
-   Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripItem.Dock%2A> ve <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> tablo hücresi içinde öğeleri hizalamak için kod özellikleri.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yok sayılır.  
  
-   İçinde <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayı İnceleme <xref:System.Windows.Forms.ToolStripItem.Placement%2A> bir öğe üzerinde ana yerleştirilmiş olup olmadığını belirlemek için özellik <xref:System.Windows.Forms.ToolStrip> veya uygun olmayan.  
  
-   Tutamacı işlenmez ve bu nedenle bir <xref:System.Windows.Forms.ToolStrip> içinde <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> düzen stili bir <xref:System.Windows.Forms.ToolStripPanel> taşınamaz.  
  
-   <xref:System.Windows.Forms.ToolStrip> Taşma düğmesini değil işlenen ve <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> göz ardı edilir.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 Aşağıdaki konularda açıklanmıştır <xref:System.Windows.Forms.ToolStripItem> ve ondan türetilen denetimler.  
  
 <xref:System.Windows.Forms.ToolStripItem> tarihinden itibaren tüm öğeler için soyut temel sınıf bir <xref:System.Windows.Forms.ToolStrip>. Aşağıdaki nesne modeli gösterir <xref:System.Windows.Forms.ToolStripItem> Devralma Hiyerarşisi.  
  
 ![ToolStripItem nesne modelini gösteren diyagram.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)  
  
 <xref:System.Windows.Forms.ToolStripItem> doğrudan ya da devralma sınıfları <xref:System.Windows.Forms.ToolStripItem>, ya da dolaylı olarak devralındığı <xref:System.Windows.Forms.ToolStripItem> aracılığıyla <xref:System.Windows.Forms.ToolStripControlHost> veya <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem> denetimleri içerilmelidir bir <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, veya <xref:System.Windows.Forms.ContextMenuStrip> ve forma doğrudan eklenemez. Uygun bir alt kümesini içerecek şekilde tasarlanan çeşitli kapsayıcı sınıfları <xref:System.Windows.Forms.ToolStripItem> kontrol eder.  
  
 Aşağıdaki tabloda stok <xref:System.Windows.Forms.ToolStripItem> denetimleri ve içinde görünürler en iyi kapsayıcıları. Tüm rağmen <xref:System.Windows.Forms.ToolStrip> öğesi birinde barındırılabilir <xref:System.Windows.Forms.ToolStrip>-kapsayıcı, türetilmiş bu öğeleri aşağıdaki kapsayıcılarındaki en iyi aramak için tasarlanmıştır:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> Tasarımcı araç kutusunda görünmüyor.  
  
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
 <xref:System.Windows.Forms.ToolStripButton> Düğme öğesi için <xref:System.Windows.Forms.ToolStrip>. İle çeşitli kenarlık stillerini görüntüleyebilir ve temsil eder ve işletimsel durumlarını etkinleştirmek için kullanabilirsiniz. Varsayılan olarak odağı olmasını tanımlayabilirsiniz.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> Etiket işlevsellik sağlar <xref:System.Windows.Forms.ToolStrip> kontrol eder. <xref:System.Windows.Forms.ToolStripLabel> Benzer bir <xref:System.Windows.Forms.ToolStripButton> , odak varsayılan olarak almaz ve onu değil dönüştürebilirsiniz gönderilen yada vurgulanmış olarak.  
  
 <xref:System.Windows.Forms.ToolStripLabel> barındırılan bir öğe olarak erişim anahtarlarını destekliyor.  
  
 Kullanım <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, ve <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> özellikleri bir <xref:System.Windows.Forms.ToolStripLabel> bağlantı denetiminde desteklemek için bir <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> bir sürümü <xref:System.Windows.Forms.ToolStripLabel> kullanmak için özel tasarlanmış <xref:System.Windows.Forms.StatusStrip>. Özel Özellikler <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, ve <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> Araç çubuğuna veya yönlendirmesini bağlı olarak bir menü dikey veya yatay çizgi ekler. Bu, gruplandırması veya gibi bu menü öğeleri arasında ayrım sağlar.  
  
 Ekleyebileceğiniz bir <xref:System.Windows.Forms.ToolStripSeparator> aşağı açılan listeden seçerek tasarım zamanında. Ancak, aynı zamanda otomatik olarak oluşturabileceğiniz bir <xref:System.Windows.Forms.ToolStripSeparator> bir tire (-) Tasarımcı şablon düğümü veya yazarak <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> yöntemi.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> soyut temel sınıf için <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost> özel denetimler, iki şekilde de dahil olmak üzere, diğer denetimler barındırabilirsiniz:  
  
-   Oluşturmak bir <xref:System.Windows.Forms.ToolStripControlHost> türetildiği bir sınıf ile <xref:System.Windows.Forms.Control>. Barındırılan denetim ve özellikleri tam olarak erişmek için dönüştürmelisiniz <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> özelliğini geri gerçek sınıf, temsil eder.  
  
-   Genişletme <xref:System.Windows.Forms.ToolStripControlHost>ve devralınan sınıfın varsayılan oluşturucusunu geçirme, türetilen bir sınıf temel sınıf oluşturucusunu <xref:System.Windows.Forms.Control>. Bu seçenek, ortak denetim yöntemleri ve özellikleri kolay erişim için kaydırma sağlar bir <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> olan <xref:System.Windows.Forms.ComboBox> barındırmak için en iyi duruma getirilmiş bir <xref:System.Windows.Forms.ToolStrip>. Bir alt kümesini barındırılan denetimin özellikleri ve olayları sırasında sunulur <xref:System.Windows.Forms.ToolStripComboBox> düzeyi, ancak arka plandaki <xref:System.Windows.Forms.ComboBox> denetimidir tam olarak erişilebilir <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> özelliği.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> olan <xref:System.Windows.Forms.TextBox> barındırmak için en iyi duruma getirilmiş bir <xref:System.Windows.Forms.ToolStrip>. Bir alt kümesini barındırılan denetimin özellikleri ve olayları sırasında sunulur <xref:System.Windows.Forms.ToolStripTextBox> düzeyi, ancak arka plandaki <xref:System.Windows.Forms.TextBox> denetimidir tam olarak erişilebilir <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> özelliği.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> olan <xref:System.Windows.Forms.ProgressBar> barındırmak için en iyi duruma getirilmiş bir <xref:System.Windows.Forms.ToolStrip>. Bir alt kümesini barındırılan denetimin özellikleri ve olayları sırasında sunulur <xref:System.Windows.Forms.ToolStripProgressBar> düzeyi, ancak arka plandaki <xref:System.Windows.Forms.ProgressBar> denetimidir tam olarak erişilebilir <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> özelliği.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> soyut temel sınıf için <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ve <xref:System.Windows.Forms.ToolStripSplitButton>, hangi barındırabilir öğeleri doğrudan veya bir açılan kapsayıcısında konak ek öğe. Ayarlayarak bunu <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> özelliğini bir <xref:System.Windows.Forms.ToolStripDropDown> ve ayarı <xref:System.Windows.Forms.ToolStrip.Items%2A> özelliği <xref:System.Windows.Forms.ToolStripDropDown>. Bu açılan öğeler ile doğrudan erişim <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> özelliği.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> olan bir <xref:System.Windows.Forms.ToolStripDropDownItem> ile çalışan <xref:System.Windows.Forms.ToolStripDropDownMenu> ve <xref:System.Windows.Forms.ContextMenuStrip> menüleri özel vurgulama, Düzen ve sütun düzenlemeyi işlemek için.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> ifadesine benzer <xref:System.Windows.Forms.ToolStripButton>, ancak kullanıcı tıkladığında bir açılan alan gösterir. Açılan liste okunu ayarlayarak göstermek veya gizlemek <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> özelliği. <xref:System.Windows.Forms.ToolStripDropDownButton> ana bilgisayarlar bir <xref:System.Windows.Forms.ToolStripOverflowButton> overflow öğeleri görüntüleyen <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>Verileceğini  
 <xref:System.Windows.Forms.ToolStripSplitButton> düğme ve açılan düğmeyi işlevselliğini bir araya getirir.  
  
 Kullanım <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> eşitlemek için özellik <xref:System.Windows.Forms.Control.Click> düğme üzerinde gösterilen öğenin seçtiğiniz açılır öğenin olay.  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem genel özellikleri  
 <xref:System.Windows.Forms.ToolStripItem> Aşağıdaki genel özellikleri ve denetimleri devralma seçenekleri sağlar:  
  
-   Çekirdek olayları  
  
-   Görüntü işleme  
  
-   Hizalama  
  
-   Metin ve resim ilişkisi  
  
-   Görüntü stili  
  
#### <a name="core-events"></a>Çekirdek olayları  
 <xref:System.Windows.Forms.ToolStripItem> denetimleri kendi tıklatın, fare ve Boya olayları almak ve bazı klavye da ön işleme gerçekleştirebilir.  
  
#### <a name="image-handling"></a>Görüntü işleme  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, Ve <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> özellikleri, resim işleme çeşitli yönlerini ilgilidir. Resimleri kullanmak <xref:System.Windows.Forms.ToolStrip> denetimleri doğrudan bu özellikleri ayarlama veya çalışma zamanı – yalnızca ayarlayarak <xref:System.Windows.Forms.ToolStrip.ImageList%2A> özelliği.  
  
 Resim ölçeklendirmeyi hem de özellikleri etkileşimi göre belirlenir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripItem>gibi:  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> görüntünün birleşimi tarafından belirlenen şekilde son görüntünün ölçek <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> ayarı ve kapsayıcının <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> ayarı.  
  
    -   Varsa <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> olduğu `true` (varsayılan) ve <xref:System.Windows.Forms.ToolStripItemImageScaling> olduğu <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, hiçbir resim ölçeklendirmeyi gerçekleşir ve <xref:System.Windows.Forms.ToolStrip> boyutu en büyük öğeyi veya önceden belirlenmiş bir minimum boyut olan.  
  
    -   Varsa <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> olan `false` ve <xref:System.Windows.Forms.ToolStripItemImageScaling> olan <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, her iki görüntü ya da <xref:System.Windows.Forms.ToolStrip> ölçeklendirme gerçekleşir.  
  
#### <a name="alignment"></a>Hizalama  
 Değerini <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> özelliği belirler sonuna <xref:System.Windows.Forms.ToolStrip> konumunda bir öğe görünen. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yalnızca çalıştığı yerleşim stilini <xref:System.Windows.Forms.ToolStrip> yığın taşması değerlerden birine ayarlayın.  
  
 Öğeleri yerleştirilir <xref:System.Windows.Forms.ToolStrip> sırada öğeleri öğe koleksiyonunda görünür. Bir öğe olduğu düzenlendiğini programlı olarak değiştirmek için kullanın <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> öğeyi koleksiyona taşımak için yöntemi. Bu yöntem, öğe taşır, ancak bunu çoğaltmaz.  
  
#### <a name="text-and-image-relationship"></a>Metin ve görüntü ilişkisi  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Özelliği üzerinde göreli yerleşimini görüntünün metin gerçekleştireceğini tanımlar bir <xref:System.Windows.Forms.ToolStripItem>. Görüntü, metin ya da her ikisini de eksik öğeleri, özel durumlar kabul edilir şekilde <xref:System.Windows.Forms.ToolStripItem> eksik veya birden çok öğe boş bir kolayca görüntülemez.  
  
#### <a name="display-style"></a>Görüntü stili  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> yalnızca istediğiniz görüntülenirken bir öğenin metin ve resim özelliklerin değerlerini ayarlamanıza olanak tanır. Bu, genellikle farklı bir bağlamda aynı öğeyi gösterilirken yalnızca görüntüleme stilini değiştirmek için kullanılır.  
  
## <a name="accessory-classes"></a>Aksesuar sınıfları  
 Çeşitli diğer işlevleri sağlayan sınıflar içerir:  
  
-   <xref:System.Windows.Forms.ToolStripManager> destekleyen <xref:System.Windows.Forms.ToolStrip>-ilgili görevleri birleştirme, ayarları ve işleyici seçeneklerini gibi tüm uygulamalar için.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> belirli bir stil veya tema uygulamanıza imkan sağlar bir <xref:System.Windows.Forms.ToolStrip> kolayca.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> kalemler ve Fırçalar değiştirilebilir renk tabloyu temel alarak oluşturur (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> Sistem renkleri ve bir düz görsel stil için geçerlidir <xref:System.Windows.Forms.ToolStrip> uygulamalar.  
  
-   <xref:System.Windows.Forms.ToolStripContainer> benzer <xref:System.Windows.Forms.SplitContainer>. Dört yerleşik yan panel kullanır (örneklerini <xref:System.Windows.Forms.ToolStripPanel>) ve bir yönetim paneli (örneği <xref:System.Windows.Forms.ToolStripContentPanel>) tipik bir düzenleme oluşturmak için. Yan paneller kaldıramazsınız ancak bunları gizleyebilirsiniz. Kaldırma ne merkezi panelini gizle. Bir veya daha fazla düzenleyebilirsiniz <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, veya <xref:System.Windows.Forms.StatusStrip> yan paneller ve denetimleri, diğer denetimler için merkezi Masası'nı kullanabilirsiniz. <xref:System.Windows.Forms.ToolStripContentPanel> Da tutarlı bir görünüm için formunun gövdesine Oluşturucu destek almak için bir yol sağlar. <xref:System.Windows.Forms.ToolStripContainer> Birden Çok Belgeli Arabirim (MDI) desteklemez.  
  
-   <xref:System.Windows.Forms.ToolStripPanel> taşıma ve düzenleme için alan sağlar <xref:System.Windows.Forms.ToolStrip> kontrol eder. Bu nedenle seçerseniz, yalnızca tek bir panel kullanabilirsiniz ve <xref:System.Windows.Forms.ToolStripPanel> iyi MDI senaryolarında çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
- [StatusStrip Denetimi](statusstrip-control.md)
- [ContextMenuStrip Denetimi](contextmenustrip-control.md)
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
