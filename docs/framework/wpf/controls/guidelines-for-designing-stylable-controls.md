---
title: "Stillenebilir Denetimleri Tasarlama Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6707a434f64838467033966c9093e1e415b1fb31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-designing-stylable-controls"></a>Stillenebilir Denetimleri Tasarlama Yönergeleri
Bu belge, kolayca Stillenebilir olmasını istediğiniz bir denetimi tasarlarken dikkate alınması gereken en iyi yöntemler ve şablonu bir dizi özetler. Biz bu çok sayıda deneme yanılma yoluyla en iyi yöntemler kümesi için yerleşik tema denetim stillerini üzerinde çalışırken gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim kümesi. Başarılı stil stili olduğu gibi kadar bir işlev iyi tasarlanmış nesne modeli olduğunu öğrendiniz. Bu belgenin hedef kitlesi stil yazarı değil denetim yazarı ' dir.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminoloji  
 "Stil ve şablon" stil ve şablon denetimi için Denetim görsel yönlerini erteleme denetim yazarı sağlayan teknolojiler paketimiz bakın. Bu teknolojiler paketimiz içerir:  
  
-   Stilleri (özellik ayarlayıcıları, tetikleyiciler ve film şeritleri dahil).  
  
-   Kaynaklar.  
  
-   Denetim şablonları.  
  
-   Veri şablonları.  
  
 Stil ve şablon için bir giriş için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Başlamadan önce: Denetiminizi anlama  
 Bu yönergelere girmeden atlama önce ve denetiminizin yaygın kullanım tanımladığınız anlamak önemlidir. Stil olasılıklar genellikle kural tanımaz bir kümesini sunar. Geniş çapta (birçok geliştiriciler tarafından birçok uygulama) kullanılmak üzere yazılmış denetimler stil görünümünü denetimi beklediğinizden çok daha büyük değişiklikler yapmak için kullanılabilir. Aslında, stilde denetimi bile denetim yazarının amaçları benzeyebilir değil. Stil tarafından sunulan esneklik kararlarınızı olduğundan, kararlarınızı kapsam yardımcı olması için ortak kullanım fikrini kullanabilirsiniz.  
  
 Denetiminizin yaygın kullanım anlamak için denetimi değer teklifinde hakkında düşünülecek iyi olur. Ne denetiminizi başka hiçbir denetim sunabileceğiniz tabloya getirir? Genel kullanım, belirli bir görsel görünümünü ancak bunun yerine denetimi felsefesi ve makul beklentiler kullanımı hakkında birtakım anlamına gelmez. Bu anlayış sık karşılaşılan durumda oluşum modeli ve denetimin stili-tanımlanmış davranışları hakkında bazı varsayımlar yapmanıza olanak sağlar. Durumunda <xref:System.Windows.Controls.ComboBox>, örneğin, ortak kullanım anlama, tüm InSight hakkında belirli bir olup olmadığını vermeyecektir <xref:System.Windows.Controls.ComboBox> yuvarlak köşeleri var, ancak bunu olgu bir anlayış verecektir, <xref:System.Windows.Controls.ComboBox> büyük olasılıkla bir açılır pencere gerekir ve açık olup olmadığını geçiş bazı yolu.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Genel Yönergeler  
  
-   **Kesinlikle şablon sözleşmeleri uygulamaz.** Bir denetimin şablon sözleşme öğeleri, komutları, bağlamaları, tetikleyici veya gerekli olan veya düzgün çalışması bir denetim için beklenen bile özellik ayarları oluşabilir.  
  
    -   Sözleşmeleri mümkün olduğunca en aza indirin.  
  
    -   Tasarım, tasarım sırasında (diğer bir deyişle, tasarım aracı kullanırken) zaman beklentiler çerçevesinde tamamlanmamış bir durumda bir denetim şablonu yaygındır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Böyle bir durumda geçerli olabilir beklentisi ile oluşturulacak denetimleriniz şekilde "çıktısından" durumu altyapı sağlamaz.  
  
    -   Herhangi bir değişiklik, şablon sözleşme etmeyen olduğunda özel durumlar oluşturmayın. Çok fazla sayıda veya çok az sayıda alt öğe varsa bu satırlar boyunca paneller özel durumlar oluşturmamalıdır.  
  
-   **Şablon yardımcı öğeleri içine çevre işlevselliğini dağıtın.** Her denetim, çekirdek işlevselliğini ve gerçek değer teklifinde odaklanan ve denetimin ortak kullanımı tarafından tanımlanmalıdır. Sonlandırmak için çevre davranışları ve görselleştirmeleri, yani etkinleştirmek için şablon davranışları ve denetim çekirdek işlevselliğini katkıda değil görselleştirmeleri içinde birleşim ve yardımcı öğeleri kullanın. Yardımcı öğeler üç kategoriye ayrılır:  
  
    -   **Tek başına** Yardımcısı türleridir genel ve yeniden kullanılabilir denetimler olan temelleri kullanılan veya "anonim" bir şablonda ne yardımcı öğe, ne de stilde denetimi diğerinden haberdar anlamına gelir. Teknik olarak, herhangi bir öğe anonim bir tür olabilir, ancak bu bağlamda terimi hedeflenen senaryoları etkinleştirmek için özel işlevleri kapsülleyen bu türleri açıklanmaktadır.  
  
    -   **Tür tabanlı** Yardımcısı öğeleridir özel işlevleri kapsülleyen yeni türleri. Bu öğeleri genellikle işlevselliği ortak denetimleri veya ilkel daha dar bir aralıktaki tasarlanmıştır. Tek başına yardımcı öğelerinin aksine, tür tabanlı Yardımcısı, bunlar kullanılır ve genellikle veri şablonuyla ait oldukları denetimiyle paylaşmalıdır bağlamı farkında öğelerdir.  
  
    -   **Adlı** Yardımcısı öğeleridir ortak denetimleri ya da kendi şablonunda ada göre bulmak için bir denetim bekliyor temelleri. Bu öğeleri öğeyi bulmak ve program aracılığıyla ile etkileşim bir denetim için olası hale getirerek, şablonu içinde bilinen bir ad verilir. Yalnızca herhangi bir şablonda belirli bir ada sahip bir öğe olabilir.  
  
     Aşağıdaki tabloda yardımcı öğeleri (Bu liste geniş kapsamlı değildir) denetim stilleri tarafından bugün değişiklik gösterir:  
  
    |Öğe|Tür|Kullanan|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Tür tabanlı|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>ve benzeri (tüm <xref:System.Windows.Controls.ContentControl> türleri)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Tür tabanlı|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>ve benzeri (tüm <xref:System.Windows.Controls.ItemsControl> türleri)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Adlı|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Tek başına|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>, vb.|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|Adlı|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>, vb.|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|Adlı|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Tek başına|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>, vb.|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Tek başına|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|Adlı|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Tür tabanlı|<xref:System.Windows.Controls.Slider>|  
  
-   **Gerekli kullanıcı tarafından belirtilen bağlamaları veya özellik ayarlarını yardımcı öğeler üzerinde en aza**. Denetim şablonu içinde düzgün çalışması için belirli bağlamaları veya özellik ayarlarını gerektirecek şekilde bir yardımcı öğe için yaygın bir durumdur. Şablonlu denetim ve yardımcı öğe olabildiğince, bu ayarları oluşturması gerekir. Ne zaman özelliklerini ayarlama veya bağlamaları oluşturma, kullanıcı tarafından ayarlanan değerler geçersiz dikkatli olunmalıdır. Belirli en iyi yöntemler aşağıdaki gibidir:  
  
    -   Adlandırılmış yardımcı öğeler üst öğe tarafından tanımlanması gerektiğini ve üst yardımcı öğe üzerinde gerekli tüm ayarları oluşturmanız gerekir.  
  
    -   Tür tabanlı yardımcı öğeler, kendilerini üzerinde doğrudan gerekli tüm ayarları oluşturmanız gerekir. Bunun yapılması gerekebilir. sorgu için yardımcı öğe içinde kullanıldığı, dahil olmak üzere bilgi bağlamı için kendi `TemplatedParent` (içinde kullanıldığı şablonu denetim türü). Örneğin, <xref:System.Windows.Controls.ContentPresenter> otomatik olarak bağlar `Content` özelliği, `TemplatedParent` için kendi <xref:System.Windows.Controls.ContentPresenter.Content%2A> kullanıldığında özelliği bir <xref:System.Windows.Controls.ContentControl> türetilmiş türü.  
  
    -   Tanımı gereği, ne yardımcı öğe, ne de üst hakkında diğer bildiği için tek başına yardımcı öğeleri bu şekilde iyileştirilemiyor.  
  
-   **Bir şablon içindeki bayrağı öğelere Name özelliğini kullanın**. Bunu kullanarak programlı olarak erişmek için kendi stili içinde bir öğeyi bulmak için gereken bir denetimi yapması gerektiğini `Name` özelliği ve `FindName` kip. Bir öğe bulunamadı, ancak sessizce ve dikkatlice o öğeye gereken işlevini devre dışı bir denetim bir özel durum oluşturmamalıdır.  
  
-   **Denetim durumu ve stil davranışını ifade etmek için en iyi yöntemleri kullanın.** Denetim durum değişikliklerini ve stil davranışını ifade etmek için en iyi uygulamalar sıralı bir listesi verilmiştir. Senaryonuzu sağlayan listede ilk öğe kullanmanız gerekir.  
  
    1.  Özellik bağlama. Örnek: arasındaki bağlama <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2.  Özellik değişiklikleri veya özellik animasyonları tetiklendi. Örnek: hover durumu bir <xref:System.Windows.Controls.Button>.  
  
    3.  Komutu. Örnek: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> içinde <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4.  Tek başına yardımcı öğeleri. Örnek: <xref:System.Windows.Controls.Primitives.TabPanel> içinde <xref:System.Windows.Controls.TabControl>.  
  
    5.  Tür tabanlı yardımcı türü. Örnek: <xref:System.Windows.Controls.ContentPresenter> içinde <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> içinde <xref:System.Windows.Controls.Slider>.  
  
    6.  Adlandırılmış yardımcı öğeler. Örnek: <xref:System.Windows.Controls.TextBox> içinde <xref:System.Windows.Controls.ComboBox>.  
  
    7.  Adlandırılmış yardımcı türlerden kabarcıklanma olayları. Bir stil öğesinden kabarcıklanma olaylarını dinleme, olay oluşturma öğesi benzersiz olarak tanımlanabilir istemeniz gerekir. Örnek: <xref:System.Windows.Controls.Primitives.Thumb> içinde <xref:System.Windows.Controls.ToolBar>.  
  
    8.  Özel `OnRender` davranışı. Örnek: <xref:Microsoft.Windows.Themes.ButtonChrome> içinde <xref:System.Windows.Controls.Button>.  
  
-   **Stil tetikleyicilerini (şablon tetikleyicilerinin aksine) tutumlu kullanmak**. Şablondaki öğeler üzerindeki özellikleri etkileyen Tetikleyiciler şablonda bildirilmesi gerekir. Denetim özellikleri etkileyen Tetikleyiciler (hiçbir `TargetName`) şablonu değiştirmenin tetikleyiciyi de yok olduğunu bilmiyorsanız stil içinde bildirilen.  
  
-   **Varolan stil desenleri ile tutarlı olmalıdır.** Birçok kez bir sorunu çözmek için birden çok yolu vardır. Farkında olmanız ve olası, var olan tutarlı denetlemek stil desenleri. Bu özellikle aynı temel türden türetilmiş denetimler için önemlidir (örneğin, <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>, vb.).  
  
-   **Oluşturmadan genel özelleştirme senaryolarını etkinleştirmek için özelliklerini ortaya**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]böylece bir denetimi kullanıcısı yalnızca iki özelleştirme yöntemi ile bırakılır takılabilir/özelleştirilebilir kısımları desteklemez: özellikler doğrudan ayarlama veya stilleri kullanarak özellikleri. Aklınızda özellikleri Aksi halde yeniden şablon oluşturmak gerektiren yaygın, yüksek öncelikli özelleştirme senaryolarında hedeflenen sınırlı sayıda yüzey uygundur. Ne zaman ve nasıl özelleştirme senaryolarını etkinleştirmek için en iyi yöntemler şunlardır:  
  
    -   Yaygın özelleştirmeler denetimi özellikleri olarak sunulur ve şablon tarafından tüketilen.  
  
    -   Daha az yaygın (ancak nadir olmayan) özelleştirmeler ekli özellikler sunulmalı ve şablon tarafından tüketilen.  
  
    -   Yeniden şablon oluşturma bilinen fakat nadir özelleştirmeleri için kabul edilebilir.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Tema konuları  
  
-   **Tema stilleri dener tüm temalar arasında tutarlı özellik semantiklerine sahip, ancak garanti**. Kendi belgelerinin bir parçası denetim denetimin özelliği semantiği, diğer bir deyişle, "anlamını" bir denetim için bir özellik açıklayan bir belge olmalıdır. Örneğin, <xref:System.Windows.Controls.ComboBox> denetim anlamını tanımlamanız gerekir <xref:System.Windows.Controls.Control.Background%2A> özelliği içinde <xref:System.Windows.Controls.ComboBox>. Denetim için varsayılan stiller tüm temalar arasında bu belgede tanımlanan semantikleri izlemeyi denemelisiniz. Denetim kullanıcıları, diğer yandan, özellik semantiklerine tema tema değiştirebilirsiniz bilmeniz gerekir. Bazı durumlarda, belirli bir özelliğe göre belirli bir temaya gerekli görsel kısıtlamalar altında ifade olmayabilir. (Klasik tema, örneğin, tek bir kenarlığa sahip değil `Thickness` birçok denetim için uygulanabilir.)  
  
-   **Tema stilleri tüm temalar arasında tutarlı tetikleyici semantiklerine sahip gerekmez**. Tetikleyiciler veya animasyonları aracılığıyla bir denetim stili tarafından sunulan davranış tema tema farklılık gösterebilir. Denetim kullanıcıları bir denetim mutlaka tüm temalar arasında belirli bir davranışı elde etmek için aynı mekanizmayı kullanması değil bilmeniz gerekir. Bir tema, örneğin, bir animasyon vurgulu davranışı ifade etmek için burada başka bir tema bir tetikleyici kullanan kullanabilir. Bu davranış korunmasında özelleştirilmiş denetimlerinde tutarsızlığa yol açabilir. (Bu durumda bir tetikleyici kullanılarak ifade arka plan özelliğini değiştirmek örneğin, denetimin vurgulu durumunu etkileyebilir değil. Vurgulu durumu bir animasyon kullanılarak uygulanır, ancak arka planı değiştirmek onarılamaz şekilde animasyonu ve bu nedenle durum geçişi bozar.)  
  
-   **Tema stilleri tüm temalar arasında tutarlı "Düzen" semantiklerine sahip gerekmez**. Örneğin, varsayılan stili denetim boyutu ile aynı miktarda tüm temalar kaplar veya bir denetim aynı içerik kenar boşluklarını sahip olacağını garanti garanti gerekmez / tüm temalar arasında doldurma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
