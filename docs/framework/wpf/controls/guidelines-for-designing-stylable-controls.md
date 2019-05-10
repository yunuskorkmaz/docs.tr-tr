---
title: Stillenebilir Denetimleri Tasarlama Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 99644be4a275c1de7f4b89ca23368a26a8b76f5b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614535"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Stillenebilir Denetimleri Tasarlama Yönergeleri
Bu belgede bir kolayca Stillenebilir olmasını düşündüğünüz bir denetim tasarlarken dikkate alınması gereken en iyi yöntemler ve şablonu özetler. Biz bu en iyi deneme yanılma çok fazla dizi tema denetim stilleri yerleşik çalışırken gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim kümesi. Başarılı bir stil stilini olduğu kadar bir işlev bir iyi tasarlanmış bir nesne modelinin olduğunu öğrendik. Bu belgenin hedef kitlesi denetim, stil yazarı yazarıdır.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminoloji  
 "Stil ve şablon oluşturma" görsel stil ve şablon denetimin denetime yönlerini erteleneceği denetim yazarı etkinleştirme teknolojileri paketi bakın. Bu teknoloji paketi içerir:  
  
- Stilleri (özellik ayarlayıcılarına, tetikleyiciler ve görsel Taslaklar dahil).  
  
- Kaynaklar.  
  
- Denetim şablonları.  
  
- Veri şablonları.  
  
 Stil ve şablon için bir giriş için bkz [stil ve şablon oluşturma](styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Başlamadan önce: Denetiminizi anlama  
 Bu yönergeleri kullanmaya başlamadan önce anlamanız ve ortak kullanımı da, Denetim, tanımladığınız önemlidir. Stil olasılıklar genellikle kural tanımaz bir kümesini sunar. Geniş çapta (birçok uygulamada, birçok geliştirici tarafından) kullanılacak yazılır denetimler stil görünümünü denetim değiştirebilen değişiklik yapmak için kullanılabilir. Aslında, stil uygulanmış denetimi bile denetim yazarın amaçları benzeyebilir değil. Stil tarafından sunulan esnekliği kararlarınızı olduğundan, ortak kullanım fikrini kararlarınızı kapsam yardımcı olması için kullanabilirsiniz.  
  
 Denetimin ortak kullanımını anlamak için denetimin değer teklifi hakkında düşünmek geçerlidir. Ne denetiminiz başka bir denetimde sunduğu tabloya getirir? Belirli bir görsel görünümünü ancak yerine denetimin felsefesi ve kullanımı hakkında beklentileri makul bir dizi ortak kullanımı göstermez. Bu anlayış, bazı varsayımlarda ortak durumda bileşim modeli ve denetimin stili tanımlı Davranışlar hakkında olanak tanır. Durumunda, <xref:System.Windows.Controls.ComboBox>, örneğin, ortak kullanım anlama, herhangi bir öngörü hakkında belirli bir olmadığını vermeyecektir <xref:System.Windows.Controls.ComboBox> yuvarlatılmış köşeler var, ancak bu olgu bir anlayış verir, <xref:System.Windows.Controls.ComboBox> büyük olasılıkla bir açılır pencere gerekir ve açık olup olmadığını geçiş bazı yoludur.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Genel Yönergeler  
  
- **Kesinlikle şablonu sözleşmeleri uygulamaz.** Bir denetimin şablonunu sözleşme öğeleri, komutları, bağlamaları, tetikleyici veya gerekli olan veya düzgün çalışması bir denetim için beklenen bile özellik ayarları oluşabilir.  
  
    - Sözleşmeler mümkün olduğunca en aza indirin.  
  
    - Tasarım (diğer bir deyişle, bir tasarım aracını kullanırken) zaman, tasarım sırasında beklentisi eksik bir durumda bir denetim şablonu yaygındır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Böyle bir durum geçerli olmayabilir beklentisiyle oluşturulacak denetiminiz için bir "çıktısından" durumu altyapısı sunmaz.  
  
    - Şablon sözleşmenin herhangi bir yönü takip edilmemesi olduğunda özel durumlar oluşturmayın. Bunlar çok fazla veya çok az sayıda alt öğe varsa bu satırlar boyunca, paneller özel durum oluşturmamalıdır.  
  
- **Şablon Yardımcısı öğelerine çevre işlevselliğini dağıtın.** Her denetim, temel işlevleri ve gerçek değer önerisi odaklanan ve denetimin ortak kullanımı tarafından tanımlanan. Bu bitiş, oluşturma ve Yardımcısı öğeleri çevre birimi davranışlardan ve görselleştirmeler, yani etkinleştirmek için şablon davranışları ve denetim çekirdek işlevselliğini katkıda bulunmuyor görselleştirmeler içinde kullanın. Yardımcı öğeleri üç kategoriye ayrılır:  
  
    - **Tek başına** Yardımcısı türleridir genel ve yeniden kullanılabilir denetimleri olan temelleri kullanılan veya "anonim" bir şablonda yardımcı öğe ne stil uygulanmış denetimi diğerinden haberdar olduğu anlamına gelen. Teknik olarak, herhangi bir öğeyi anonim bir tür olabilir, ancak bu bağlamda terimi hedeflenen senaryoları etkinleştirmek için özel işlevi kapsülleyen türlerine açıklar.  
  
    - **Türüne göre** Yardımcısı öğeleridir özel işlevleri kapsülleyen yeni türleri. Bu öğeler, genellikle daha dar bir dizi işlev ortak denetimleri ya temelleri ile tasarlanmıştır. Tek başına yardımcı öğelerinin aksine, türüne göre Yardımcısı, bunlar kullanılır ve genellikle veri şablonuyla ait oldukları denetimiyle paylaşmalıdır bağlamı farkında öğeleridir.  
  
    - **Adlı** Yardımcısı öğeleridir ortak denetimleri veya onun şablonunda ada göre bulma bir denetim bekliyor basit. Bu öğeleri bir denetim öğesini bulun ve program aracılığıyla etkileşim çözmelerine şablonu içinde bilinen bir ad verilir. Yalnızca bir öğe herhangi bir şablonda belirli bir ada sahip olabilir.  
  
     Aşağıdaki tabloda, (Bu liste kapsamlı değildir) denetim stilleri tarafından hemen işe Yardımcısı öğeleri gösterir:  
  
    |Öğe|Tür|Kullanan|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Türüne göre|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>ve benzeri (tüm <xref:System.Windows.Controls.ContentControl> türleri)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Türüne göre|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>ve benzeri (tüm <xref:System.Windows.Controls.ItemsControl> türleri)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|adlı|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Tek başına|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>, vb.|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|adlı|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>, vb.|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|adlı|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Tek başına|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>, vb.|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Tek başına|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|adlı|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Türüne göre|<xref:System.Windows.Controls.Slider>|  
  
- **Kullanıcı tarafından belirtilen gerekli bağlamaları veya yardımcı öğeler üzerinde özellik ayarları en aza**. Denetim şablonu içinde düzgün çalışması için belirli bağlamaları veya özellik ayarları istemek bir yardımcı öğe yaygındır. Şablonlu denetim ve yardımcı öğe, bu ayarları, mümkün olan en kısa artacak oluşturması gerekir. Ne zaman özelliklerini ayarlama veya bağlantıları oluşturma, kullanıcı tarafından ayarlanan değerler geçersiz kılmamak dikkat edilmelidir. Belirli en iyi yöntemler aşağıdaki gibidir:  
  
    - Adlandırılmış yardımcı öğeler tarafından üst tanımlanması gerektiğini ve gerekli tüm ayarları Yardımcısı öğesinde üst oluşturmanız gerekir.  
  
    - Türüne göre yardımcı öğeler, kendilerini üzerinde doğrudan gerekli tüm ayarları oluşturmanız gerekir. Bunun yapılması gerekebilir sorgu için yardımcı öğe içinde kullanıldığı, dahil olmak üzere bilgi bağlamı için kendi `TemplatedParent` (Denetim türü içinde kullanıldığı şablonunun). Örneğin, <xref:System.Windows.Controls.ContentPresenter> otomatik olarak bağlar `Content` özelliği, `TemplatedParent` için kendi <xref:System.Windows.Controls.ContentPresenter.Content%2A> kullanıldığında özelliği bir <xref:System.Windows.Controls.ContentControl> türetilmiş tür.  
  
    - Tanımı gereği, yardımcı öğe ne üst hakkında diğer bildiği için tek başına yardımcı öğeler bu şekilde iyileştirilemiyor.  
  
- **Bir şablon içindeki bayrağı öğelere Name özelliğini kullanın**. Bunu kullanarak program aracılığıyla erişmek için kendi stilinde bir öğeyi bulmak için gereken bir denetimi yapması gerektiğini `Name` özelliği ve `FindName` paradigma. Bir öğe bulunamadı, ancak o öğenin gerekli işlevselliği sessizce ve düzgün bir şekilde devre dışı bırakma, denetim bir özel durum oluşturmamalıdır.  
  
- **Denetim durumunu ve davranışını bir stil ifade etmek için en iyi yöntemleri kullanın.** Denetim durumunu ve davranışını bir stil ifade etmek için en iyi sıralı bir listesi verilmiştir. Senaryonuzu sağlayan listede ilk öğe kullanmanız gerekir.  
  
    1. Özellik bağlama. Örnek: arasında bağlama <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2. Özellik değişiklikleri veya özellik animasyonları tetiklenir. Örnek: vurgulu durumu bir <xref:System.Windows.Controls.Button>.  
  
    3. komutu. Örnek: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> içinde <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4. Tek başına yardımcı öğeler. Örnek: <xref:System.Windows.Controls.Primitives.TabPanel> içinde <xref:System.Windows.Controls.TabControl>.  
  
    5. Türüne göre yardımcı türü. Örnek: <xref:System.Windows.Controls.ContentPresenter> içinde <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> içinde <xref:System.Windows.Controls.Slider>.  
  
    6. Adlandırılmış yardımcı öğeler. Örnek: <xref:System.Windows.Controls.TextBox> içinde <xref:System.Windows.Controls.ComboBox>.  
  
    7. Adlandırılmış yardımcı türlerinden kabarcıklanma olaylar. Bir stil öğesinden kabarcıklanma olaylarını dinlemek, olay oluşturma öğeyi benzersiz şekilde tanımlanabilir istemeniz gerekir. Örnek: <xref:System.Windows.Controls.Primitives.Thumb> içinde <xref:System.Windows.Controls.ToolBar>.  
  
    8. Özel `OnRender` davranışı. Örnek: <xref:Microsoft.Windows.Themes.ButtonChrome> içinde <xref:System.Windows.Controls.Button>.  
  
- **Stil Tetikleyiciler (aksine, şablon Tetikleyicileri) tedbirli şekilde kullanın**. Şablonda öğelerde şablondaki özellikleri etkileyen Tetikleyiciler bildirilmelidir. Denetim özelliklerini etkileyen Tetikleyiciler (hiçbir `TargetName`) şablonu değiştirmenin tetikleyici de yok olduğunu bilmiyorsanız stil içinde bildirilebilir.  
  
- **Mevcut stil desenleri ile tutarlı olun.** Birden çok kez bir sorunu çözmek için birden çok yolu vardır. Dikkat edilmesi ve mümkün olan tutarlı denetlemek stil desenleri. Bu aynı temel türünden türetilen denetimler için özellikle önemlidir, (örneğin, <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>, vb.).  
  
- **Oluşturmadan genel özelleştirme senaryolarını etkinleştirmek için özellikler kullanıma**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Böylece denetim kullanıcısının yalnızca iki özelleştirme yöntemleriyle bırakılır takılabilir/özelleştirilebilir kısımları desteklemiyor: özellikler doğrudan ayarlama veya stilleri kullanarak özellikleri. Aklınızda özellikleri aksi yeniden şablon oluşturmak gerektiren çok sık, yüksek öncelikli özelleştirme senaryolarında hedeflenen sınırlı sayıda yüzey uygun olur. Ne zaman ve nasıl özelleştirme senaryolarını etkinleştirmek için en iyi uygulamalar şunlardır:  
  
    - Yaygın özelleştirmeleri denetim özellikleri olarak gösterilen ve şablon tarafından kullanılan.  
  
    - Daha az ortak (nadiren kullanılsa bile değil) özelleştirmeleri ekli özellikler kullanıma sunulan ve şablon tarafından kullanılan.  
  
    - Yeniden şablon oluşturma bilinen ancak nadir özelleştirmeleri için kabul edilebilir.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Tema konuları  
  
- **Tema stilleri tüm temalar arasında tutarlı özellik semantiklere sahip, ancak garanti dener**. Belgelerinin bir parçası olarak, Denetim denetimin özellik semantiklerini, diğer bir deyişle, "anlamını" bir denetim için bir özellik açıklayan bir belge olmalıdır. Örneğin, <xref:System.Windows.Controls.ComboBox> denetim anlamını tanımlamanız gerekir <xref:System.Windows.Controls.Control.Background%2A> özelliği içinde <xref:System.Windows.Controls.ComboBox>. Varsayılan stiller denetlemek için bu belgede tanımlanan tüm temalar arasında semantikleri izlemeyi değiştirilemeyeceğini belirlemelidir. Denetim kullanıcılar, diğer taraftan, özellik semantiği tema temayı değiştirebilirsiniz bilmeniz gerekir. Bazı durumlarda, belirli bir özelliğe göre belirli bir temaya gerekli görsel kısıtlamalar altında ifade olmayabilir. (Klasik tema, örneğin, tek bir kenarlığa sahip değil `Thickness` birçok denetim için uygulanabilir.)  
  
- **Tema stilleri tüm temalar arasında tutarlı bir tetikleyici semantiklere sahip gerekmez**. Tetikleyici veya animasyon aracılığıyla bir denetim stili tarafından kullanıma sunulan davranışını tema tema farklılık gösterebilir. Denetim kullanıcıları bir denetim mutlaka tüm temalar arasında belirli bir davranışı elde etmek için mekanizma kullanması değil bilmeniz gerekir. Bir tema, örneğin, bir animasyon vurgulu davranışı ifade için burada başka bir tema, bir tetikleyici kullanır kullanabilir. Bu davranış korunmasında özelleştirilmiş denetimlerinde tutarsızlıklara neden olabilir. (Bu durumda tetikleyici kullanılarak ifade arka plan özelliğini değiştirme gibi denetimin üzerine gelindiğinde kullanılacak durumunu etkileyebilir değil. Vurgulu durumu animasyon kullanarak uygulanmışsa ancak arka plan değiştirme onarılamaz şekilde animasyon ve bu nedenle durum geçişi bozar.)  
  
- **Tema stilleri tüm temalar arasında tutarlı "layout" semantiklere sahip gerekmez**. Örneğin, varsayılan stil denetimi tüm Temalar da aynı boyut miktarını kaplayabilir veya bir denetim kenar boşluklarını aynı içerik sahip olacağını garanti garanti gerekmez / tüm temalar arasında doldurma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [Denetim Yazımına Genel Bakış](control-authoring-overview.md)
