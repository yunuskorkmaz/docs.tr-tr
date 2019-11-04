---
title: Stillenebilir Denetimleri Tasarlama Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 0fbb515afbeac05168ced6f0a99f50eb29a5c848
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459655"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Stillenebilir Denetimleri Tasarlama Yönergeleri

Bu belge, kolayca Stillenebilir ve templatable kullanmayı düşündüğünüz bir denetim tasarlarken göz önünde bulundurmanız gereken en iyi yöntemler kümesini özetler. Yerleşik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim kümesine yönelik Tema denetim stillerinde çalışırken çok sayıda deneme ve hata üzerinden bu en iyi yöntemler kümesine ulaştık. Başarılı stillendirme, stilin kendisi olduğu gibi iyi tasarlanmış bir nesne modeli işlevinin çok fazla olduğunu öğrendik. Bu belge için amaçlanan hedef kitle, stil yazarı değil Denetim yazardır.

<a name="Terminology"></a>

## <a name="terminology"></a>Terminoloji

"Stil oluşturma ve şablon oluşturma", denetim yazarının denetimin görsel yönlerini denetimin stili ve şablonuna ertemesini sağlayan teknoloji paketine başvurur. Bu teknoloji paketi şunları içerir:

- Stiller (özellik ayarlayıcıları, Tetikleyiciler ve film şeritleri dahil).

- Kaynakların.

- Denetim şablonları.

- Veri şablonları.

Stil ve şablon oluşturmaya giriş için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.

<a name="Before_You_Start__Understanding_Your_Control"></a>

## <a name="before-you-start-understanding-your-control"></a>Başlamadan önce: denetiminizi anlama

Bu yönergelere geçmeden önce, denetiminizin ortak kullanımını anlamak ve tanımlanması önemlidir. Stil, genellikle bir dizi olasılıklardan oluşur. Yaygın olarak kullanılmak üzere yazılan denetimler (birçok uygulamada, birçok geliştirici tarafından), denetimin görsel görünümünde değişiklikler yapmak için stil oluşturmak için kullanılan zorluk. Aslında, stilli denetim, denetim yazarının amaçları ile de benzemeyebilir. Stil tarafından sunulan esneklik temelde bounddaha az olduğundan kararlarınızı kapsamınıza yardımcı olması için sık kullanılan kullanım fikrini kullanabilirsiniz.

Denetiminizin ortak kullanımını anlamak için, denetimin değer teklifini düşünmek iyi olur. Denetiminiz, başka bir denetimin sunabileceği tabloya ne getirir? Yaygın kullanım belirli görsel görünümü göstermez, ancak bunun yerine denetimin felseı ve kullanımı hakkında makul bir beklentiler kümesi vardır. Bu anlama, ortak durumda denetimin bileşim modeli ve stil tanımlı davranışları hakkında bazı varsayımlar yapmanıza olanak sağlar. Örneğin, yaygın kullanımı anlamak, belirli bir <xref:System.Windows.Controls.ComboBox> yuvarlatılmış köşeler olup olmadığına dair herhangi bir öngörü vermeyecektir, ancak <xref:System.Windows.Controls.ComboBox> muhtemelen bir açılır pencere ve bir şekilde <xref:System.Windows.Controls.ComboBox>açık olup olmadığını değiştirme.

<a name="General_Guidelines"></a>

## <a name="general-guidelines"></a>Genel Yönergeler

- **Şablon sözleşmelerini kesinlikle zorunlu kılmaz.** Bir denetimin şablon sözleşmesi, öğelerin, komutların, bağlamalardan, tetikleyicilerden veya hatta bir denetimin düzgün çalışması için gerekli olan ya da beklenen özellik ayarlarından oluşabilir.

  - Sözleşmeleri mümkün olduğunca en aza indirin.

  - Tasarım zamanı sırasında (bir tasarım aracı kullanılırken), bir denetim şablonunun tamamlanmamış bir durumda olması için sık görülen beklentide bir tasarım. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "oluşturma" durum altyapısı sunmaz, bu nedenle denetimlerin, bu durum geçerli olabilecek beklentilerle oluşturulması gerekir.

  - Şablon sözleşmesinin herhangi bir yönü izlenmediğinden özel durum oluşturmaz. Bu satırlarda, panolar çok fazla veya çok az alt öğe içeriyorsa özel durumlar oluşturmaz.

- **Şablon yardımcı öğelerinde çevresel işlevselliği çarpanlara ayırın.** Her denetim, temel işlevlerine ve gerçek değer teklifini odaklanmalıdır ve denetimin ortak kullanımı tarafından tanımlanır. Bu uçta, çevresel davranışları ve görselleştirmeleri etkinleştirmek, diğer bir deyişle, denetimin temel işlevlerine katkıda bulunmayan davranışlar ve görselleştirmeler sağlamak için şablon içinde kompozisyon ve yardımcı öğeleri kullanın. Yardımcı öğeler üç kategoriye ayrılır:

  - **Tek başına** yardımcı türler, bir şablonda "anonim" olarak kullanılan ortak ve yeniden kullanılabilir denetimler veya temel öğelerdir; Yani, yardımcı öğe veya stilli denetim diğerinden haberdar değildir. Teknik olarak, herhangi bir öğe anonim bir tür olabilir, ancak bu bağlamda terim hedeflenen senaryoları etkinleştirmek için özelleştirilmiş işlevselliği kapsülleyen bu türleri açıklar.

  - **Tür tabanlı** yardımcı öğeler, özelleştirilmiş işlevselliği kapsülleyen yeni türlerdir. Bu öğeler genellikle yaygın denetimlerden veya temel elemanlara göre daha dar bir işlev aralığıyla tasarlanmıştır. Tek başına yardımcı öğelerinden farklı olarak, tür tabanlı yardımcı öğeler kullanıldıkları bağlamdan haberdar olur ve genellikle verileri ait oldukları şablonla birlikte paylaşılması gerekir.

  - **Adlandırılmış** yardımcı öğeler, bir denetimin şablon içinde ada göre bulmayı beklediği ortak denetimlerdir veya temel öğelerdir. Bu öğelere şablon içinde iyi bilinen bir ad verilir ve bu, bir denetimin öğeyi bulmasını ve programla birlikte etkileşime geçmesini mümkün kılar. Herhangi bir şablonda yalnızca belirli bir ada sahip bir öğe olabilir.

  Aşağıdaki tabloda denetim stilleri tarafından kullanılan yardımcı öğeler gösterilmektedir (Bu liste ayrıntılı değildir):

  |Öğe|Tür|Kullanan|
  |-------------|----------|-------------|
  |<xref:System.Windows.Controls.ContentPresenter>|Tür tabanlı|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>, vb. (tüm <xref:System.Windows.Controls.ContentControl> türleri)|
  |<xref:System.Windows.Controls.ItemsPresenter>|Tür tabanlı|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, vb. (tüm <xref:System.Windows.Controls.ItemsControl> türleri)|
  |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Adlandırılır|<xref:System.Windows.Controls.ToolBar>|
  |<xref:System.Windows.Controls.Primitives.Popup>|Etikete|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>vb.|
  |<xref:System.Windows.Controls.Primitives.RepeatButton>|Adlandırılır|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>, vb.|
  |<xref:System.Windows.Controls.Primitives.ScrollBar>|Adlandırılır|<xref:System.Windows.Controls.ScrollViewer>|
  |<xref:System.Windows.Controls.ScrollViewer>|Etikete|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>vb.|
  |<xref:System.Windows.Controls.Primitives.TabPanel>|Etikete|<xref:System.Windows.Controls.TabControl>|
  |<xref:System.Windows.Controls.TextBox>|Adlandırılır|<xref:System.Windows.Controls.ComboBox>|
  |<xref:System.Windows.Controls.Primitives.TickBar>|Tür tabanlı|<xref:System.Windows.Controls.Slider>|

- **Yardım öğelerinde gerekli Kullanıcı tanımlı bağlamaları veya özellik ayarlarını en aza indirin**. Bir yardımcı öğe, denetim şablonu içinde düzgün şekilde çalışması için belirli bağlamalar veya özellik ayarları gerektirirken yaygındır. Yardımcı öğe ve şablonlu denetim, mümkün olduğunca bu ayarları oluştururlar. Özellikleri ayarlarken veya bağlamaları oluştururken, Kullanıcı tarafından ayarlanan değerleri geçersiz kılmamak için dikkatli olunmalıdır. Belirli en iyi yöntemler şunlardır:

  - Adlandırılmış yardımcı öğeler üst öğe ile tanımlanmalıdır ve üst öğe, yardımcı öğesinde gerekli tüm ayarları sağlamalıdır.

  - Tür tabanlı yardımcı öğeler, gerekli tüm ayarları doğrudan kendi üzerinde çağırmalıdır. Bunun yapılması, `TemplatedParent` (kullanılmakta olan şablonun denetim türü) dahil olmak üzere, kullanıldığı bilgi bağlamını sorgulamak için yardımcı öğe gerektirebilir. Örneğin <xref:System.Windows.Controls.ContentPresenter>, <xref:System.Windows.Controls.ContentControl> türetilen türde kullanıldığında `TemplatedParent` `Content` özelliğini <xref:System.Windows.Controls.ContentPresenter.Content%2A> özelliğine otomatik olarak bağlar.

  - Tek başına yardımcı öğeler bu şekilde iyileştirilemez, çünkü tanım, ne yardımcı öğe ne de üst öğe hakkında bilgi sahibi değildir.

- **Bir şablon içindeki öğeleri işaretlemek Için Name özelliğini kullanın**. Program aracılığıyla erişmek için kendi stilinde bir öğe bulması gereken bir denetim, `Name` özelliğini ve `FindName` paradigmasını kullanarak bunu yapmanız gerekir. Bir denetim bir öğe bulunamadığında özel durum oluşturmaz, ancak sessizce ve bu öğeyi gerektiren işlevselliği devre dışı bırakır.

- **Bir stildeki denetim durumunu ve davranışı ifade etmek için en iyi uygulamaları kullanın.** Aşağıda, denetim durumu değişikliklerini ve bir stildeki davranışı ifade etmek için en iyi uygulamaların sıralı bir listesi verilmiştir. Senaryonuzu sağlayan listedeki ilk öğeyi kullanmanız gerekir.

  1. Özellik bağlama. Örnek: <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>arasında bağlama.

  2. Tetiklenen Özellik değişiklikleri veya özellik animasyonları. Örnek: <xref:System.Windows.Controls.Button>üzerine gelme durumu.

  3. Komutundaki. Örnek: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> / <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> <xref:System.Windows.Controls.Primitives.ScrollBar>.

  4. Tek başına yardımcı öğeleri. Örnek: <xref:System.Windows.Controls.TabControl><xref:System.Windows.Controls.Primitives.TabPanel>.

  5. Tür tabanlı yardımcı türleri. Örnek: <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ContentPresenter>, <xref:System.Windows.Controls.Slider><xref:System.Windows.Controls.Primitives.TickBar>.

  6. Adlandırılmış yardımcı öğeleri. Örnek: <xref:System.Windows.Controls.ComboBox><xref:System.Windows.Controls.TextBox>.

  7. Adlandırılmış yardımcı türlerden olayları kabarcıklanmasını. Bir stil öğesinden kabarcıklanmasını olaylarını dinleyebiliyorsanız, olayı üreten öğenin benzersiz olarak tanımlanması gerekir. Örnek: <xref:System.Windows.Controls.ToolBar><xref:System.Windows.Controls.Primitives.Thumb>.

  8. Özel `OnRender` davranışı. Örnek: <xref:System.Windows.Controls.Button><xref:Microsoft.Windows.Themes.ButtonChrome>.

- **Stil tetikleyicilerini (şablon tetikleyicilerinin aksine) gelişigüzel**bir şekilde kullanın. Şablondaki öğelerin özelliklerini etkileyen tetikleyiciler şablonda bildirilmelidir. Denetimin özelliklerini etkileyen Tetikleyiciler (`TargetName`yok), şablonu değiştirmenin tetikleyiciyi de yok etmediği bilinmediğiniz takdirde stilde bildirilmelidir.

- **Varolan stil desenleriyle tutarlı olmalıdır.** Birçok kez bir sorunu çözmenin birden çok yolu vardır. Mümkün olduğunda ve var olan denetim stili desenleriyle tutarlı bir şekilde haberdar olun. Bu, özellikle aynı temel türden (örneğin, <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>vb.) türetilmiş denetimler için önemlidir.

- **Yeniden şablon oluşturmadan ortak özelleştirme senaryolarını etkinleştirmek için özellikleri kullanıma sunun**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] takılabilir/özelleştirilebilir bölümleri desteklemez, bu nedenle bir denetim kullanıcısı yalnızca iki özelleştirme yöntemi ile bırakılır: özellikleri doğrudan ayarlama veya stilleri kullanarak özellikleri ayarlama. Göz önünde bulundurularak, daha sonra yeniden şablon oluşturma gerektirmeyen, çok yaygın, yüksek öncelikli özelleştirme senaryolarına hedeflenmiş sınırlı sayıda özelliği yüzeye almak uygun olacaktır. Özelleştirme senaryolarına ne zaman ve nasıl etkinleştirileceği için en iyi uygulamalar şunlardır:

  - Çok yaygın özelleştirmeler, denetimde özellikler olarak kullanıma sunulmalı ve şablon tarafından tüketilecektir.

  - Daha az yaygın (nadir olmasa da) özelleştirmeler iliştirilmiş özellikler olarak kullanıma sunulmalı ve şablon tarafından tüketilmelidir.

  - Bilinen ancak nadir özelleştirmeler için yeniden şablon gerektirecek şekilde kabul edilebilir.

<a name="Theme_Considerations"></a>

## <a name="theme-considerations"></a>Tema konuları

- **Tema stillerinin tüm temalar genelinde tutarlı Özellik semantiğinin olması gerekir, ancak herhangi bir garanti**vermez. Belgelerinin bir parçası olarak, denetiminizin Özellik semantiğini açıklayan bir belge olmalıdır, diğer bir deyişle, bir denetimin özelliğinin "anlamı". Örneğin, <xref:System.Windows.Controls.ComboBox> denetimi <xref:System.Windows.Controls.ComboBox>içindeki <xref:System.Windows.Controls.Control.Background%2A> özelliğinin anlamını tanımlamalıdır. Denetiminizin varsayılan stilleri, bu belgede tanımlanan semantiğini tüm temalar genelinde izlemeyi denemelidir. Diğer yandan denetim kullanıcıları, özellik semantiğinin temadan temaya değiştirebildiği farkında olmalıdır. Belirli durumlarda, belirli bir özellik belirli bir tema için gereken görsel kısıtlamalar altında ifade edilemez. (Örneğin, klasik temanın, `Thickness` birçok denetim için uygulanabileceğini tek bir kenarlığı yoktur.)

- **Tema stillerinin tüm temalar arasında tutarlı tetikleyici semantiklerine sahip olması gerekmez**. Tetikleyiciler veya animasyonlar aracılığıyla bir denetim stili tarafından kullanıma sunulan davranış temadan temaya farklı olabilir. Denetim kullanıcıları, bir denetimin tüm temalar genelinde belirli bir davranışa ulaşmak için aynı mekanizmayı gerektirmeyeceği farkında olmalıdır. Örneğin, bir tema, başka bir temanın tetikleyici kullandığı vurgulama davranışını ifade etmek için bir animasyon kullanabilir. Bu, özelleştirilmiş denetimlerde davranış koruma ile tutarsızlıklara neden olabilir. (Örneğin, arka plan özelliğinin değiştirilmesi, bu durum bir tetikleyici kullanılarak ifade edildiği takdirde denetimin üzerine gelme durumunu etkilemeyebilir. Ancak, üzerine gelme durumu bir animasyon kullanılarak uygulanırsa, arka plana geçiş işlemi animasyonu geri alınamaz ve bu nedenle durum geçişi olur.)

- **Tema stillerinin tüm temalar arasında tutarlı "Layout" semantiklerine sahip olması gerekmez**. Örneğin, varsayılan stil, bir denetimin tüm temalarda aynı miktarda boyut kaplayacağı veya bir denetimin tüm temalar genelinde aynı içerik kenar boşluklarına/doldurmaya sahip olacağını garanti etmek zorunda değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetim Yazımına Genel Bakış](control-authoring-overview.md)
