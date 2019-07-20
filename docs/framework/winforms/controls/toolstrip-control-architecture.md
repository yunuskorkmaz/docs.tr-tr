---
title: ToolStrip Denetim Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363832"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip Denetim Mimarisi

<xref:System.Windows.Forms.ToolStrip> Ve<xref:System.Windows.Forms.ToolStripItem> sınıfları araç çubuğu, durum ve menü öğelerini görüntülemek için esnek, genişletilebilir bir sistem sağlar. Bu sınıfların hepsi <xref:System.Windows.Forms> ad alanında bulunur ve genellikle "ToolStrip" önekiyle ( <xref:System.Windows.Forms.ToolStripOverflow>gibi) veya "Strip <xref:System.Windows.Forms.MenuStrip>" soneki (gibi) ile adlandırılır.

## <a name="toolstrip"></a>ToolStrip

Aşağıdaki konularda ve öğesinden <xref:System.Windows.Forms.ToolStrip> türetilen denetimler açıklanır.

<xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> ,<xref:System.Windows.Forms.StatusStrip>ve için<xref:System.Windows.Forms.ContextMenuStrip>soyut temel sınıftır. Aşağıdaki nesne modelinde <xref:System.Windows.Forms.ToolStrip> devralma hiyerarşisi gösterilmektedir.

![ToolStrip nesne modelini gösteren diyagram.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

İçindeki <xref:System.Windows.Forms.ToolStrip> tüm öğelere <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyon aracılığıyla erişebilirsiniz. İçindeki <xref:System.Windows.Forms.ToolStripDropDownItem> tüm öğelere <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> koleksiyon aracılığıyla erişebilirsiniz. Öğesinden <xref:System.Windows.Forms.ToolStrip>türetilmiş bir sınıfta, yalnızca şu anda görüntülenen öğelere erişmek <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> için özelliğini de kullanabilirsiniz. Bunlar şu anda taşma menüsünde olmayan öğelerdir.

Aşağıdaki öğeler özellikle <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönlerle sorunsuz şekilde çalışacak şekilde tasarlanmıştır. Bunlar, <xref:System.Windows.Forms.ToolStrip> denetim için tasarım zamanında varsayılan olarak kullanılabilir:

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>, yerine <xref:System.Windows.Forms.MainMenu>geçen en üst düzey kapsayıcıdır. Ayrıca, anahtar işleme ve birden çok belge arabirimi (MDI) özellikleri de sağlar. İşlev görür <xref:System.Windows.Forms.ToolStripDropDownItem> ve <xref:System.Windows.Forms.ToolStripMenuItem> ile <xref:System.Windows.Forms.MenuStrip>birlikte çalışarak, öğesinden <xref:System.Windows.Forms.ToolStripItem>türetilseler de.

Aşağıdaki öğeler özellikle <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönlerle sorunsuz şekilde çalışacak şekilde tasarlanmıştır. Bunlar, <xref:System.Windows.Forms.MenuStrip> denetim için tasarım zamanında varsayılan olarak kullanılabilir:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip><xref:System.Windows.Forms.StatusBar> denetimin yerini alır. Özel bir tablo düzeni, formun boyutlandırma ve taşıma griler için destek `Spring` ve bir <xref:System.Windows.Forms.ToolStripStatusLabel> , kullanılabilir alanı otomatik olarak doldurmasına izin veren özelliği içerir.<xref:System.Windows.Forms.StatusStrip>

Aşağıdaki öğeler özellikle <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönlerle sorunsuz şekilde çalışacak şekilde tasarlanmıştır. Bunlar, <xref:System.Windows.Forms.StatusStrip> denetim için tasarım zamanında varsayılan olarak kullanılabilir:

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip>değiştirilir <xref:System.Windows.Forms.ContextMenu>. Bir denetimi herhangi bir <xref:System.Windows.Forms.ContextMenuStrip> denetimle ilişkilendirebilirsiniz ve sağ fare tıklaması bağlam menüsünü (veya kısayol menüsünü) otomatik olarak görüntüler. Yöntemini kullanarak programlı bir <xref:System.Windows.Forms.ContextMenuStrip> şekilde gösterebilirsiniz. <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> <xref:System.Windows.Forms.ContextMenuStrip>Dinamik popülasyon <xref:System.Windows.Forms.ToolStripDropDown.Opening> ve <xref:System.Windows.Forms.ToolStripDropDown.Closing> çoklu tıklama senaryolarını işlemek için iptal edilebilen ve olayları destekler. <xref:System.Windows.Forms.ContextMenuStrip>görüntüleri, menü-öğe denetimi durumunu, metni, erişim anahtarlarını, kısayolları ve basamaklı menüleri destekler.

Aşağıdaki öğeler özellikle <xref:System.Windows.Forms.ToolStripSystemRenderer> ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tüm yönlerle sorunsuz şekilde çalışacak şekilde tasarlanmıştır. Bunlar, <xref:System.Windows.Forms.ContextMenuStrip> denetim için tasarım zamanında varsayılan olarak kullanılabilir:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>ToolStrip genel özellikleri

Aşağıdaki konularda, <xref:System.Windows.Forms.ToolStrip> ve türetilmiş denetimlere genel olan özellikler ve davranışlar açıklanır.

#### <a name="painting"></a>Yar

<xref:System.Windows.Forms.ToolStrip> Denetimlerde özel boyama yapabilirsiniz. Diğer Windows Forms denetimlerinde <xref:System.Windows.Forms.ToolStrip> olduğu gibi, ve <xref:System.Windows.Forms.ToolStripItem> her ikisinde de geçersiz `OnPaint` kılınabilir Yöntemler `Paint` ve olaylar vardır. Düzenli boyama yaparken, koordinat sistemi denetimin istemci alanına göre değişir; diğer bir deyişle, denetimin sol üst köşesi 0, 0 ' dır. İçin `Paint` olayve`OnPaint` yöntemi diğer denetim boyama olayları gibi davranır.<xref:System.Windows.Forms.ToolStripItem>

Denetimler Ayrıca, arka plan, öğe arka planı, öğe görüntüsü, öğe oku, <xref:System.Windows.Forms.ToolStripRenderer> öğe metni ve kenarlığını boyamak için geçersiz kılınabilir Yöntemler içeren sınıf aracılığıyla öğelerin ve kapsayıcının oluşturulmasına daha iyi erişim sağlar. <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStrip>. Bu yöntemlerin olay bağımsız değişkenleri, istediğiniz şekilde ayarlayabileceğiniz dikdörtgenler, renkler ve metin biçimleri gibi çeşitli özellikleri kullanıma sunar.

Bir öğenin nasıl boyanacağını gösteren yalnızca birkaç yönü ayarlamak için, genellikle öğesini geçersiz kılabilirsiniz <xref:System.Windows.Forms.ToolStripRenderer>.

Yeni bir öğe yazıyorsanız ve boyamanın tüm yönlerini denetlemek istiyorsanız, `OnPaint` yöntemini geçersiz kılın. `OnPaint`İçinden yöntemlerini <xref:System.Windows.Forms.ToolStripRenderer>kullanabilirsiniz.

Varsayılan <xref:System.Windows.Forms.ToolStrip> olarak, iki kez tamponlanır ve <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> ayarından yararlanır.

#### <a name="parenting"></a>Olma

Kapsayıcı sahipliği ve üst öğe kavramı, diğer Windows Forms kapsayıcı denetimlerinden farklı <xref:System.Windows.Forms.ToolStrip> denetimlerde daha karmaşıktır. Bu, taşma gibi dinamik senaryoları desteklemek, birden fazla <xref:System.Windows.Forms.ToolStrip> öğe arasında açılan öğeleri paylaşmak ve bir <xref:System.Windows.Forms.ContextMenuStrip> denetimden oluşturmayı desteklemek için gereklidir.

Aşağıdaki listede, üst öğe ile ilgili Üyeler açıklanmakta ve kullanımları açıklanmaktadır.

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>açılan öğenin kaynağı olan öğeye erişir. Bu öğesine <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>benzerdir, ancak bir denetim döndürmek yerine bir <xref:System.Windows.Forms.ToolStripItem>, döndürür.

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>birden çok denetim aynı <xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>olduğunda hangi denetimin kaynak olduğunu belirler.

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>, <xref:System.Windows.Forms.ToolStripItem.Parent%2A> özelliğe yönelik salt okunurdur. Üst öğe, bir üst öğenin, taşma alanında olabilecek, öğenin görüntülendiği geçerli <xref:System.Windows.Forms.ToolStrip> sonucu belirten bir sahibinden farklıdır.

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>öğeleri koleksiyonu geçerli <xref:System.Windows.Forms.ToolStripItem> olanöğeleridöndürür.<xref:System.Windows.Forms.ToolStrip> Bu, taşmayı işlemek için özel <xref:System.Windows.Forms.ToolStrip.ImageList%2A> kod yazmadan üst düzeydeki <xref:System.Windows.Forms.ToolStrip> diğer özelliklere başvurmak için en iyi yoldur.

#### <a name="behavior-of-inherited-controls"></a>Devralınan denetimlerin davranışı

Aşağıdaki denetimler devralma sırasında her kullanıldığında kilitlenir:

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>Bu, Ayrıca, <xref:System.Windows.Forms.ToolStripContainer> ve tek <xref:System.Windows.Forms.ToolStripPanel> denetimleri içeren panolar içerir.

Örneğin, önceki listede bir veya daha fazla denetimden birini kullanarak yeni bir Windows Forms uygulaması oluşturun. Bir veya daha fazla denetimin erişim değiştiricisini veya `public` `protected`olarak ayarlayın ve ardından projeyi derleyin. İlk formdan devralan bir form ekleyin ve ardından devralınmış bir denetim seçin. Denetim kilitli, erişim değiştiricisi `private`gibi davranan şekilde görünür.

#### <a name="toolstripcontainer-support-of-inheritance"></a>Devralma için ToolStripContainer desteği

<xref:System.Windows.Forms.ToolStripContainer> Denetim, aşağıdaki örneğe benzer şekilde, sınırlı devralınmış senaryolar destekler:

1. Yeni bir Windows Forms uygulaması oluşturun.

2. Forma bir <xref:System.Windows.Forms.ToolStripContainer> ekleyin.

3. <xref:System.Windows.Forms.ToolStripContainer> İçin erişim değiştiricisini veya `public` `protected`olarak ayarlayın.

4. <xref:System.Windows.Forms.ToolStrip>' <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> Nin bölgelerine,<xref:System.Windows.Forms.ToolStripPanel> ve denetimlerinin herhangi bir birleşimini ekleyin. <xref:System.Windows.Forms.ToolStripContainer>

5. Projeyi oluşturun.

6. İlk formdan devralan bir form ekleyin.

7. Formda devralınmış <xref:System.Windows.Forms.ToolStripContainer> öğesini seçin.

#### <a name="inherited-behavior-of-child-controls"></a>Alt denetimlerin devralınmış davranışı

Önceki adımları tamamladıktan sonra, aşağıdaki devralınmış davranış oluşur:

- Tasarımcıda, denetim devralınmış bir simgeyle görüntülenir.

- <xref:System.Windows.Forms.ToolStripPanel> Denetimler kilitlidir; içeriğini seçemezsiniz veya yeniden düzenleyemezsiniz.

- <xref:System.Windows.Forms.ToolStripContentPanel>' A denetimler ekleyebilir, denetimleri taşıyabilir ve alt denetimleri <xref:System.Windows.Forms.ToolStripContentPanel>yapabilirsiniz.

- Form oluşturulduktan sonra değişiklikleriniz devam ettiritiliyor.

  > [!NOTE]
  > Erişim değiştiricilerini bir <xref:System.Windows.Forms.ToolStripContainer>parçası olan <xref:System.Windows.Forms.ToolStripPanel> tüm denetimlerden kaldırın. Denetimin tamamını <xref:System.Windows.Forms.ToolStripContainer> yöneten erişim değiştiricisi.

#### <a name="partial-trust"></a>Kısmi Güven

Kısmi güven kapsamındaki `ToolStrip`s 'nin sınırlamaları, yetkisiz kişiler veya hizmetler tarafından kullanılabilen kişisel bilgilerin yanlışlıkla girişini engellemek için tasarlanmıştır. Koruyucu ölçüler aşağıdaki gibidir:

- `ToolStripDropDown`<xref:System.Security.Permissions.UIPermissionWindow.AllWindows> denetimlerin<xref:System.Windows.Forms.ToolStripControlHost>içindeki öğeleri görüntülemesi gerekir. Bu <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, ve<xref:System.Windows.Forms.ToolStripProgressBar> gibi iç denetimlerin yanı sıra Kullanıcı tarafından oluşturulan denetimlere de uygulanır. Bu gereksinim karşılanmazsa, bu öğeler görüntülenmez. Hiçbir özel durum oluşturulmaz.

- Özelliğinin olarak `false` ayarlanmasına izin verilmez ve iptal edilebilen <xref:System.Windows.Forms.ToolStripDropDown.Closing> olay parametresi yok sayılır. <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> Bu, açılan öğeyi yok etmeden birden fazla tuş vuruşu girmeyi olanaksız hale getirir. Bu gereksinim karşılanmazsa, bu tür öğeler görüntülenmez. Hiçbir özel durum oluşturulmaz.

- Çok sayıda tuş vuruşu işleme olayı, dışındaki kısmi güven bağlamlarında <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>gerçekleştiklerinde oluşturulmaz.

- Erişim anahtarları, verilmediği zaman <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> işlenmez.

#### <a name="usage"></a>Kullanım

Aşağıdaki kullanım desenlerinde <xref:System.Windows.Forms.ToolStrip> düzen, klavye etkileşimi ve Son Kullanıcı davranışında bir pul vardır:

- İçine katılmış<xref:System.Windows.Forms.ToolStripPanel>

  , <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel> Ve genelinde<xref:System.Windows.Forms.ToolStripPanel>yeniden konumlandırılabilir. <xref:System.Windows.Forms.ToolStrip.Stretch%2A> `false` <xref:System.Windows.Forms.ToolStrip> Özelliği yok sayılır ve özellik ise öğesi öğesine<xref:System.Windows.Forms.ToolStripPanel>eklendiğinde, ' nin boyutu artar. `Dock` <xref:System.Windows.Forms.ToolStrip> Genellikle, sekme sırasına katılmaz.

- Abileceği

  , <xref:System.Windows.Forms.ToolStrip> Sabit bir konumdaki kapsayıcının bir tarafına yerleştirilir ve boyutu yerleştirilmiş olan tüm kenarı üzerine genişletilir. <xref:System.Windows.Forms.ToolStrip> Genellikle, sekme sırasına katılmaz.

- Mutlak konumlandırılmış

  <xref:System.Windows.Forms.ToolStrip> , Özelliği<xref:System.Windows.Forms.Control.Location%2A> tarafından yerleştirilmesi, sabit bir boyuta sahip ve genellikle sekme sırasına katılıyorsa diğer denetimlere benzer.

#### <a name="keyboard-interaction"></a>Klavye etkileşimi

##### <a name="access-keys"></a>Erişim tuşları

ALT tuşu ile birlikte veya sonrasında, erişim tuşları klavyeyi kullanarak bir denetimi etkinleştirmenin bir yoludur. <xref:System.Windows.Forms.ToolStrip>hem açık hem de örtük erişim anahtarlarını destekler. Açık tanım, harften önceki bir ampersan (&) karakteri kullanır. Örtük tanım, belirli `Text` bir özellikte bulunan karakterlerin sırasına göre eşleşen bir öğe bulmayı deneyen bir algoritma kullanır.

##### <a name="shortcut-keys"></a>Kısayol Tuşları

Tarafından <xref:System.Windows.Forms.MenuStrip> kullanılan kısayol tuşları, kısayol tuşunu tanımlamak için <xref:System.Windows.Forms.Keys> numaralandırmanın (sıra dışı olmayan) bir birleşimini kullanır. <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> Özelliğini, yalnızca metin içeren bir kısayol tuşu görüntülemek için, "Sil" yerine "Del" görüntülenmesi için de kullanabilirsiniz.

##### <a name="navigation"></a>Gezinti

Alt tuşu tarafından <xref:System.Windows.Forms.MenuStrip> işaret edilen tarafından <xref:System.Windows.Forms.Form.MainMenuStrip%2A>etkinleştirilir. Buradan, Ctrl + Sekme öğeleri içindeki <xref:System.Windows.Forms.ToolStrip> `ToolStripPanel`denetimler arasında gezinir. Sayısal tuş takımındaki sekme tuşu ve ok tuşları, içindeki öğeler arasında gezinbir <xref:System.Windows.Forms.ToolStrip>. Özel bir algoritma, taşma bölgesinde gezinmeyi işler. Boşluk çubuğu <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>veya <xref:System.Windows.Forms.ToolStripSplitButton>seçer.

##### <a name="focus-and-validation"></a>Odak ve doğrulama

ALT anahtar tarafından etkinleştirildiğinde, ya da <xref:System.Windows.Forms.MenuStrip> genellikle odağa sahip olan denetimden odağı almaz veya <xref:System.Windows.Forms.ToolStrip> kaldırır. İçinde <xref:System.Windows.Forms.MenuStrip> veya açılan <xref:System.Windows.Forms.MenuStrip>içinde barındırılan bir denetim varsa, Kullanıcı Tab tuşuna bastığında denetim kazanır. Genel <xref:System.Windows.Forms.Control.GotFocus> olarak,,<xref:System.Windows.Forms.Control.LostFocus>, ve <xref:System.Windows.Forms.Control.Leave> olayları klavye<xref:System.Windows.Forms.MenuStrip> tarafından etkinleştirildiklerinde bu durum oluşmayabilir. <xref:System.Windows.Forms.Control.Enter> Bu gibi durumlarda, yerine <xref:System.Windows.Forms.MenuStrip.MenuActivate> ve <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> olaylarını kullanın.

Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A>. `false` Doğrulamayı <xref:System.Windows.Forms.ContainerControl.Validate%2A> gerçekleştirmek için formunuzu açık olarak çağırın.

#### <a name="layout"></a>Düzen

Özelliği<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> <xref:System.Windows.Forms.ToolStrip> ile<xref:System.Windows.Forms.ToolStripLayoutStyle> üyelerinden birini seçerek düzeni kontrol edersiniz.

##### <a name="stack-layouts"></a>Yığın düzenleri

Yığınlama, <xref:System.Windows.Forms.ToolStrip>öğesinin her iki ucunda de her birinin yanındaki öğelerin düzenlenmesi. Aşağıdaki listede yığın düzenleri açıklanmaktadır.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>varsayılandır. Bu ayar, <xref:System.Windows.Forms.ToolStrip> sürükleme ve yerleştirme senaryolarını işlemek için <xref:System.Windows.Forms.ToolStrip.Orientation%2A> özelliğine uygun olarak kendi düzeninin değişmesine neden olur.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow><xref:System.Windows.Forms.ToolStrip> öğeleri birbirlerine dikey olarak işler.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow><xref:System.Windows.Forms.ToolStrip> öğeleri birbirlerine her yatay olarak işler.

##### <a name="other-features-of-stack-layouts"></a>Yığın düzenlerinin diğer özellikleri

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>öğenin hizalanma sonunu <xref:System.Windows.Forms.ToolStrip> belirler.

Öğeler içine <xref:System.Windows.Forms.ToolStrip>sığmadığında, otomatik olarak bir taşma düğmesi görünür. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Özellik ayarı, bir öğenin her zaman gerektiğinde veya hiçbir zaman taşma alanında görünüp görünmeyeceğini belirler.

Olayda, bir öğenin <xref:System.Windows.Forms.ToolStrip>ana öğe, taşma <xref:System.Windows.Forms.ToolStripItem.Placement%2A> <xref:System.Windows.Forms.ToolStrip>veya şu anda hiç gösterilmediğine ait olup olmadığını anlamak için özelliği inceleyebilirsiniz. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> Bir öğenin görüntülenmesinin tipik nedenleri, öğenin Main <xref:System.Windows.Forms.ToolStrip> 'e sığmıyor <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> ve özelliği olarak <xref:System.Windows.Forms.ToolStripItemOverflow.Never>ayarlanmış olması olabilir.

Taşınabilir yapın ve ' a <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> ayarlayarak<xref:System.Windows.Forms.ToolStripGripStyle.Visible>taşınabilir hale getirin. <xref:System.Windows.Forms.ToolStrip>

##### <a name="other-layout-options"></a>Diğer düzen seçenekleri

Diğer düzen seçenekleri ve ' <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>dir.

##### <a name="flow-layout"></a>Akış düzeni

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>, <xref:System.Windows.Forms.ContextMenuStrip> ,<xref:System.Windows.Forms.ToolStripDropDownMenu>ve için<xref:System.Windows.Forms.ToolStripOverflow>varsayılan düzen. Öğesine <xref:System.Windows.Forms.FlowLayoutPanel>benzerdir. <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> Düzenin özellikleri şunlardır:

- Tüm özellikleri <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> özelliği tarafından gösterilir. <xref:System.Windows.Forms.LayoutSettings> Sınıfı bir<xref:System.Windows.Forms.FlowLayoutSettings> sınıfa atamalısınız.

- Satır içindeki öğeleri hizalamak <xref:System.Windows.Forms.ToolStripItem.Dock%2A> için <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> koddaki ve özelliklerini kullanabilirsiniz.

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özellik yoksayıldı.

- Olayda, bir öğenin ana <xref:System.Windows.Forms.ToolStrip> öğeye yerleştirilip yerleştirilmediğini veya uymadığını öğrenmek için <xref:System.Windows.Forms.ToolStripItem.Placement%2A> özelliği inceleyebilirsiniz. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- Bu tutamacı işlenmez ve bu nedenle içindeki bir <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> düzen stili <xref:System.Windows.Forms.ToolStripPanel> taşınamaz.

- Taşma düğmesi işlenmez ve <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> yok sayılır. <xref:System.Windows.Forms.ToolStrip>

##### <a name="table-layout"></a>Tablo düzeni

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>Düzen varsayılandır <xref:System.Windows.Forms.StatusStrip>. Buna benzerdir <xref:System.Windows.Forms.TableLayoutPanel>. <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> Düzenin özellikleri şunlardır:

- Tüm özellikleri <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> özelliği tarafından gösterilir. <xref:System.Windows.Forms.LayoutSettings> Sınıfı bir<xref:System.Windows.Forms.TableLayoutSettings> sınıfa atamalısınız.

- Öğeleri tablo hücresi içinde <xref:System.Windows.Forms.ToolStripItem.Dock%2A> hizalamak <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> için koddaki ve özelliklerini kullanabilirsiniz.

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özellik yoksayıldı.

- Olayda, bir öğenin ana <xref:System.Windows.Forms.ToolStrip> öğeye yerleştirilip yerleştirilmediğini veya uymadığını öğrenmek için <xref:System.Windows.Forms.ToolStripItem.Placement%2A> özelliği inceleyebilirsiniz. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- Bu tutamacı işlenmez ve bu nedenle içindeki bir <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> düzen stili <xref:System.Windows.Forms.ToolStripPanel> taşınamaz.

- Taşma düğmesi işlenmez ve <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> yok sayılır. <xref:System.Windows.Forms.ToolStrip>

## <a name="toolstripitem"></a>ToolStripItem

Aşağıdaki konularda ve öğesinden <xref:System.Windows.Forms.ToolStripItem> türetilen denetimler açıklanır.

<xref:System.Windows.Forms.ToolStripItem>, ' a <xref:System.Windows.Forms.ToolStrip>gidecek tüm öğelerin soyut temel sınıfıdır. Aşağıdaki nesne modelinde <xref:System.Windows.Forms.ToolStripItem> devralma hiyerarşisi gösterilmektedir.

![ToolStripItem nesne modelini gösteren diyagram.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>sınıflar doğrudan öğesinden <xref:System.Windows.Forms.ToolStripItem>devralınır veya <xref:System.Windows.Forms.ToolStripItem> üzerinden <xref:System.Windows.Forms.ToolStripControlHost> <xref:System.Windows.Forms.ToolStripDropDownItem>dolaylı olarak devralınır.

<xref:System.Windows.Forms.ToolStripItem>denetimler <xref:System.Windows.Forms.ToolStrip> ,<xref:System.Windows.Forms.MenuStrip>,, veya<xref:System.Windows.Forms.ContextMenuStrip> içinde yer almalıdır ve doğrudan bir forma eklenemez. <xref:System.Windows.Forms.StatusStrip> Çeşitli kapsayıcı sınıfları, <xref:System.Windows.Forms.ToolStripItem> denetimlerin uygun bir alt kümesini içerecek şekilde tasarlanmıştır.

Aşağıdaki tabloda, hisse senedi <xref:System.Windows.Forms.ToolStripItem> denetimleri ve en iyi şekilde göründükleri kapsayıcılar listelenmektedir. Herhangi bir <xref:System.Windows.Forms.ToolStrip> öğe herhangi bir <xref:System.Windows.Forms.ToolStrip>türetilmiş kapsayıcıda barındırılabilecek olsa da, bu öğeler aşağıdaki kapsayıcılarda en iyi şekilde görünecek şekilde tasarlanmıştır:

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>Tasarımcı araç kutusunda görünmez.

|İçerilen öğe|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
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

<xref:System.Windows.Forms.ToolStripButton>, için <xref:System.Windows.Forms.ToolStrip>düğme öğesidir. Bunu çeşitli kenarlık stilleriyle görüntüleyebilirsiniz ve bunu, işletimsel durumları temsil etmek ve etkinleştirmek için kullanabilirsiniz. Ayrıca, odağı varsayılan olarak odağa sahip olacak şekilde tanımlayabilirsiniz.

### <a name="toolstriplabel"></a>ToolStripLabel

, <xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.ToolStrip> Denetimlerde etiket işlevselliği sağlar. , <xref:System.Windows.Forms.ToolStripLabel>Varsayılan olarak odağı almaz ve gönderildi veya vurgulanmış olarak işlenmiyor. <xref:System.Windows.Forms.ToolStripButton>

<xref:System.Windows.Forms.ToolStripLabel>barındırılan bir öğe, erişim anahtarlarını destekler.

<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.ToolStripLabel> Biriçinde<xref:System.Windows.Forms.ToolStrip>bağlantı denetimini desteklemek için bir üzerinde ,veözelliklerinikullanın.<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>, içinde <xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.StatusStrip>kullanılmak üzere özel olarak tasarlanan bir sürümdür. Özel özellikler, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>ve <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>içerir.

### <a name="toolstripseparator"></a>ToolStripSeparator

, <xref:System.Windows.Forms.ToolStripSeparator> Yönlendirmeye bağlı olarak bir araç çubuğuna veya menüye dikey veya yatay çizgi ekler. Bir menüdeki gibi öğeler arasında gruplandırma veya ayrım sağlar.

Bir <xref:System.Windows.Forms.ToolStripSeparator> açılır listeden seçerek tasarım zamanı ekleyebilirsiniz. Bununla birlikte, tasarımcı şablonu düğümünde veya <xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> yönteminde bir tire (-) yazarak otomatik olarak bir oluşturabilirsiniz.

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>, <xref:System.Windows.Forms.ToolStripComboBox> ,<xref:System.Windows.Forms.ToolStripTextBox>ve için<xref:System.Windows.Forms.ToolStripProgressBar>soyut temel sınıftır. <xref:System.Windows.Forms.ToolStripControlHost>, özel denetimler de dahil olmak üzere diğer denetimleri iki şekilde barındırabilir:

- <xref:System.Windows.Forms.ToolStripControlHost> Öğesinden<xref:System.Windows.Forms.Control>türetilen bir sınıf ile oluşturun. Barındırılan denetim ve özelliklere tam olarak erişmek için <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> özelliği, temsil ettiği gerçek sınıfa dönüştürmeniz gerekir.

- Öğesini <xref:System.Windows.Forms.ToolStripControlHost>genişletin ve devralınmış sınıfın parametresiz oluşturucusunda, öğesinden <xref:System.Windows.Forms.Control>türetilen bir sınıf geçirerek taban sınıf oluşturucusunu çağırın. Bu seçenek, ' de <xref:System.Windows.Forms.ToolStrip>kolay erişim için ortak denetim yöntemlerini ve özelliklerini kaydırabilmenizi sağlar.

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>, içinde barındırmak için <xref:System.Windows.Forms.ComboBox> en iyi duruma <xref:System.Windows.Forms.ToolStrip>getirilmiştir. Barındırılan denetimin özellikler ve olaylarının bir alt kümesi, <xref:System.Windows.Forms.ToolStripComboBox> düzeyinde gösterilir, ancak temel <xref:System.Windows.Forms.ComboBox> denetime <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> özelliği aracılığıyla tam olarak erişilebilir.

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>, içinde barındırmak için <xref:System.Windows.Forms.TextBox> en iyi duruma <xref:System.Windows.Forms.ToolStrip>getirilmiştir. Barındırılan denetimin özellikler ve olaylarının bir alt kümesi, <xref:System.Windows.Forms.ToolStripTextBox> düzeyinde gösterilir, ancak temel <xref:System.Windows.Forms.TextBox> denetime <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> özelliği aracılığıyla tam olarak erişilebilir.

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>, içinde barındırmak için <xref:System.Windows.Forms.ProgressBar> en iyi duruma <xref:System.Windows.Forms.ToolStrip>getirilmiştir. Barındırılan denetimin özellikler ve olaylarının bir alt kümesi, <xref:System.Windows.Forms.ToolStripProgressBar> düzeyinde gösterilir, ancak temel <xref:System.Windows.Forms.ProgressBar> denetime <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> özelliği aracılığıyla tam olarak erişilebilir.

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>, <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.ToolStripSplitButton>, ve için, öğeleri doğrudan veya bir açılan kapsayıcıda ek öğeleri barındırabilen, ve için soyut temel sınıftır. <xref:System.Windows.Forms.ToolStripDropDownButton> <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> Bunu, <xref:System.Windows.Forms.ToolStripDropDown> <xref:System.Windows.Forms.ToolStrip.Items%2A> özelliğini olarak ayarlayarak ve özelliğini ayarlayarak yapabilirsiniz. <xref:System.Windows.Forms.ToolStripDropDown> Bu açılan öğelere doğrudan <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> özelliği aracılığıyla erişin.

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>, ve menüleri için özel <xref:System.Windows.Forms.ToolStripDropDownMenu> vurgulama <xref:System.Windows.Forms.ContextMenuStrip> , düzen ve sütun düzenlemesini işlemek üzere ve ile birlikte çalışarak. <xref:System.Windows.Forms.ToolStripDropDownItem>

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>gibi <xref:System.Windows.Forms.ToolStripButton>görünür, ancak Kullanıcı buna tıkladığında bir açılan alan gösterir. <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> Özelliği ayarlayarak açılan oku gizleyin veya gösterin. <xref:System.Windows.Forms.ToolStripDropDownButton><xref:System.Windows.Forms.ToolStripOverflowButton> üzerinde<xref:System.Windows.Forms.ToolStrip>taşan öğeleri görüntüleyen a ana bilgisayarları.

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>düğme ve açılan düğme işlevlerini birleştirir.

Seçili açılan öğenin <xref:System.Windows.Forms.Control.Click> olayını düğme üzerinde gösterilen öğeyle eşleştirmek için özelliğinikullanın.<xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>

### <a name="toolstripitem-generic-features"></a>ToolStripItem genel özellikleri

<xref:System.Windows.Forms.ToolStripItem>, denetimleri devralma için aşağıdaki genel özellikleri ve seçenekleri sağlar:

- Çekirdek olaylar

- Görüntü işleme

- Hizalama

- Metin ve resim ilişkisi

- Görüntüleme stili

#### <a name="core-events"></a>Çekirdek olaylar

<xref:System.Windows.Forms.ToolStripItem>denetimler kendi tıklama, fare ve boyama olaylarını alır ve ayrıca bazı klavye önişlemleri gerçekleştirebilir.

#### <a name="image-handling"></a>Görüntü Işleme

<xref:System.Windows.Forms.ToolStripItem.Image%2A>, ,,<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>Ve özelliklerigörüntüişlemenin<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> çeşitli yönlerini sağlar. <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A> <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A> Bu özellikleri doğrudan <xref:System.Windows.Forms.ToolStrip> ayarlayarak veya çalışma zamanı – yalnızca <xref:System.Windows.Forms.ToolStrip.ImageList%2A> özelliğini ayarlayarak denetimlerde görüntüleri kullanın.

Görüntü ölçekleme, aşağıdaki gibi, ve <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripItem>özelliklerinin her ikisi de ile etkileşime göre belirlenir:

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>, görüntünün <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> ayarı ve <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> kapsayıcının ayarı birleşimine göre belirlenen şekilde nihai görüntünün ölçeklendirilmesine sahiptir.

  - <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStrip> İse (varsayılan) ve <xref:System.Windows.Forms.ToolStripItemImageScaling> ise <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, görüntü ölçekleme gerçekleşmez ve boyut en büyük öğe veya önceden tanımlanmış en küçük boyut olur. `true`

  - <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> , Ve ise<xref:System.Windows.Forms.ToolStripItemImageScaling>, ne görüntü ne de<xref:System.Windows.Forms.ToolStrip> ölçekleme gerçekleşmez. <xref:System.Windows.Forms.ToolStripItemImageScaling.None> `false`

#### <a name="alignment"></a>Hizalama

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliğin değeri, bir öğenin göründüğü sonunu <xref:System.Windows.Forms.ToolStrip> belirler. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Özelliği yalnızca<xref:System.Windows.Forms.ToolStrip> öğesinin düzen stili yığın taşması değerlerinden birine ayarlandığında işe yarar.

Öğeler, <xref:System.Windows.Forms.ToolStrip> öğeler koleksiyonunda öğelerin göründüğü sırayla yerleştirilir. Bir öğenin düzenlendiği yeri programlı bir şekilde değiştirmek için, <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> yöntemini kullanarak öğeyi koleksiyondaki öğeyi taşıyın. Bu yöntem öğeyi taşımıyor ancak yinelemez.

#### <a name="text-and-image-relationship"></a>Metin ve resim Ilişkisi

Özelliği, resmin içindeki metne <xref:System.Windows.Forms.ToolStripItem>göre göreli yerleşimini tanımlar. <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Bir görüntü, metin veya her ikisi de olmayan öğeler özel durumlar olarak değerlendirilir, <xref:System.Windows.Forms.ToolStripItem> böylece eksik öğe veya öğeler için boş bir nokta görüntülenmez.

#### <a name="display-style"></a>Görüntüleme stili

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>yalnızca istediğiniz şeyi görüntülerken bir öğenin metin ve resim özelliklerinin değerlerini ayarlamanıza olanak sağlar. Bu genellikle, farklı bir bağlamda aynı öğeyi gösterirken yalnızca görüntüleme stilini değiştirmek için kullanılır.

## <a name="accessory-classes"></a>Donatı sınıfları

Çeşitli diğer işlevleri sağlayan sınıflar şunlardır:

- <xref:System.Windows.Forms.ToolStripManager>birleştirme <xref:System.Windows.Forms.ToolStrip>, ayarlar ve işleyici seçenekleri gibi tüm uygulamalar için ilgili görevleri destekler.

- <xref:System.Windows.Forms.ToolStripRenderer>belirli bir stili veya temayı kolay bir <xref:System.Windows.Forms.ToolStrip> şekilde uygulamanıza olanak tanır.

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>değiştirilebilir renk tablosuna (<xref:System.Windows.Forms.ProfessionalColorTable>) göre kalemler ve fırçalar oluşturur.

- <xref:System.Windows.Forms.ToolStripSystemRenderer><xref:System.Windows.Forms.ToolStrip> uygulamalara sistem renkleri ve düz görsel stil uygular.

- <xref:System.Windows.Forms.ToolStripContainer>benzerdir <xref:System.Windows.Forms.SplitContainer>. Tipik bir düzenleme oluşturmak için dört adet sabitlenmiş yan <xref:System.Windows.Forms.ToolStripPanel>panel (örnek örnekleri) ve bir merkezi panel <xref:System.Windows.Forms.ToolStripContentPanel>(bir örneği) kullanır. Yan panelleri kaldıramazsınız, ancak gizleyebilirsiniz. Merkezi paneli kaldırmanız veya gizleyemezler. Yan panellerde bir veya daha <xref:System.Windows.Forms.ToolStrip>fazla <xref:System.Windows.Forms.MenuStrip>, veya <xref:System.Windows.Forms.StatusStrip> denetimini düzenleyebilir ve Merkezi paneli diğer denetimler için kullanabilirsiniz. Ayrıca <xref:System.Windows.Forms.ToolStripContentPanel> , tutarlı bir görünüm için formunuzun gövdesine işleyici desteği almanın bir yolunu sağlar. <xref:System.Windows.Forms.ToolStripContainer>birden çok belge arabirimini (MDI) desteklemez.

- <xref:System.Windows.Forms.ToolStripPanel>denetimleri taşımak ve düzenlemek <xref:System.Windows.Forms.ToolStrip> için alan sağlar. Yalnızca birini seçip MDI senaryolarında iyi <xref:System.Windows.Forms.ToolStripPanel> çalışırsa, yalnızca bir panel kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
- [StatusStrip Denetimi](statusstrip-control.md)
- [ContextMenuStrip Denetimi](contextmenustrip-control.md)
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
