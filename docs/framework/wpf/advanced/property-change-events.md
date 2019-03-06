---
title: Özellik Değiştirme Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: 2997696a6617bb9c17bb98bba0b352cb27c07896
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352002"
---
# <a name="property-change-events"></a>Özellik Değiştirme Olayları
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] başlatılan çeşitli olaylara yanıt olarak bir değişiklik bir özelliğinin değerini tanımlar. Genellikle bir bağımlılık özelliği özelliğidir. Olay bazen gönderilmiş bir olay ve bazı durumlarda standart [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay. Diğer özellik değişiklikleri genellikle ise bazı özellik değişiklikleri daha uygun bir öğe ağacı ile yönlendirilen çünkü olayının tanımı senaryoya bağlı olarak değişir. yalnızca birisi ağdır burada özelliği değiştirilmiş nesne.  
  
## <a name="identifying-a-property-change-event"></a>Özellik değişikliği olay tanımlama  
 Bir özellik değişiminin rapor veren tüm olayları açıkça ya da bir imza deseni veya bir adlandırma deseni, bir özellik değişti olayı olarak tanımlanır. Olay açıklaması genellikle [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] belgeleri gösteren olay doğrudan bir özellik değeri değişiklik bağlıdır ve özelliğe ve olaya arasında çapraz sağlar.  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged olayları  
 Belirli olayları, bir olay veri türü ve özellik değiştirme olayları için açıkça kullanılan temsilci kullanın. Olay veri türü <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, ve temsilci <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Olay verileri hem de temsilci işleyicisi tanımlarken değişen özelliğinin gerçek türü belirtmek için kullanılan genel tür parametresine sahiptir. İki özellik Olay verileri içeren <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> ve <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, her ikisi de olduğu ardından türü geçirilen bağımsız değişken olay verileri.  
  
 Özellik değişti olayını gönderilmiş bir olayı kaydedilir adının "Yönlendirilmiş" bölümünü gösterir. Özellik değişti olayı yönlendirme avantajı değerleri (denetimin bileşik parça) alt öğeleri özelliklerini değiştirirseniz, üst düzey bir denetimin özellik değişti olayları alabiliyor olmasıdır. Örneğin, içeren bir denetim oluşturabilirsiniz. bir <xref:System.Windows.Controls.Primitives.RangeBase> gibi denetleyen bir <xref:System.Windows.Controls.Slider>. Varsa değerini <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özellik değişiklikleri kaydırıcı bölümünde üst denetimi yerine bölümünde değişiklik işlemek isteyebilirsiniz.  
  
 Eski bir değer ve yeni bir değer içerdiğinden, bu olay işleyicisi için özellik değeri bir doğrulayıcı kullanmak daha cazip olabilir. Ancak, çoğu özellik değişti olayları tasarım amacınıza değildir. Genellikle, değerleri ve böylece kodunuzun diğer mantıksal alanlarında bu değerleri üzerinde işlem yapabileceğiniz, ancak gerçekte olay işleyicisi içindeki değerlerin değiştirilmesi önerilmez sağlanır ve işleyicinizi nasıl uygulandığını bağlı olarak yanlışlıkla özyineleme neden olabilir .  
  
 Özel bağımlılık özelliği, özelliği veya örnekleme kodunu tanımlandığı türetilmiş bir sınıf ile çalışıyorsanız, içinde yerleşik olan özellik değişiklikleri izlemek için bir çok daha iyi bir mekanizma yoktur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi: özellik sistemi geri çağırmaları <xref:System.Windows.CoerceValueCallback> ve <xref:System.Windows.PropertyChangedCallback>. Nasıl kullanabileceğiniz hakkında daha fazla ayrıntı için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doğrulama ve zorlama, özellik sistemi bkz [bağımlılık özelliği geri aramaları ve doğrulama](dependency-property-callbacks-and-validation.md) ve [özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged olayları  
 Özellik değişti olayını senaryonun parçası olan türleri başka bir çiftinin <xref:System.Windows.DependencyPropertyChangedEventArgs> ve <xref:System.Windows.DependencyPropertyChangedEventHandler>. Bu özellik değişiklikleri olayları yönlendirilmeyen; Standart oldukları [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olayları. <xref:System.Windows.DependencyPropertyChangedEventArgs> Raporlama türü tarafından türetilmemiştir çünkü bir olağan dışı bir olay verisi <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> yapısı, bir sınıf.  
  
 Kullanan olaylar <xref:System.Windows.DependencyPropertyChangedEventArgs> ve <xref:System.Windows.DependencyPropertyChangedEventHandler> biraz daha yaygın olarak `RoutedPropertyChanged` olayları. Bu tür kullanan bir olay örneğidir <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Gibi <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> özelliği için eski ve yeni bir değer de bildirir. Ayrıca, değiştirebilecekleriniz aynı dikkat edilmesi gereken noktalar değerlerle geçerlidir; Bu genellikle değerleri yeniden gönderen olaya yanıt olarak değiştirme girişiminde önerilmez.  
  
## <a name="property-triggers"></a>Özellik tetikleyicileri  
 Bir yakından ilgili bir özellik değişti olayı için bir özellik tetikleyicisi kavramıdır. Bir özellik tetikleyicisi stil veya şablon içinde oluşturulur ve burada özellik tetikleyicisi atandığı özellik değerine göre koşullu bir davranış oluşturmanıza olanak sağlar.  
  
 Özelliği bir özellik tetikleyicisi için bir bağımlılık özelliği olmalıdır. Olabilir (ve genellikle) salt okunur bağımlılık özelliği. Ne zaman denetim tarafından kullanıma sunulan bir bağımlılık özelliği kısmen en az bir özellik tetikleyicisi olacak şekilde tasarlanan için iyi bir özellik adı "Is" ile başlayıp başlamadığını göstergesidir. Bu adlandırma sahip genellikle salt okunur Boole bağımlılık özelliği bir özellik için birincil senaryo sonuçları gerçek zamanlı kullanıcı arabirimi olabilir ve bu nedenle bir özellik tetikleyicisi aday olan denetim durumu burada raporlama özelliklerdir.  
  
 Bu özelliklerin bazıları, bir özel özellik değişti olayını da vardır. Örneğin, özellik <xref:System.Windows.UIElement.IsMouseCaptured%2A> sahip bir özellik değişti olayını <xref:System.Windows.UIElement.IsMouseCapturedChanged>. Salt okunur özellik değeriyle giriş sistemi tarafından ayarlanan ve giriş sistemi başlatır <xref:System.Windows.UIElement.IsMouseCapturedChanged> her gerçek zamanlı değişir.  
  
 Bir özellik değişiklik yapacak bir özellik tetikleyicisi kullanarak bir true özellik değişti olayı için karşılaştırıldığında, bazı sınırlamaları vardır.  
  
 Özellik tetikleyicileri bir tam eşleşme mantıksal çalışır. Bir özellik ve tetikleyici en iyi duruma görecek söz konusu değeri belirten bir değer belirtin. Örneğin: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Bu sınırlama nedeniyle, Boole özellikleri ya da bir ayrılmış sabit listesi değeri olası değer aralığı her örneği için bir tetikleyici tanımlamak için yönetilebilir olduğu alan özellikleri için özellik tetikleyicisi kullanımları çoğunu olacaktır. Özellik tetikleyicileri için yalnızca bir öğe sayısı sıfır ulaştığında gibi özel değerler var olabilecek veya özellik değeri sıfırdan uzağa yeniden değiştiğinde durumlarda hesapları hiçbir tetikleyici olacaktır (INSTEAD OF Tetikleyicileri tüm durumlarda, bir kod gerekebilir olay işleyicisi veya değeri sıfır olduğunda tetikleyici durumundan yeniden açıp kapatır bir varsayılan davranış).  
  
 Özellik tetikleyicisi sözdizimi, bir "if" deyimi programlamada benzerdir. Tetikleyici koşul true ise, ardından özellik tetikleyicisi "body" "çalışır". Bir özellik tetikleyicisi "body" kodu değil, biçimlendirme. Bu işaretleme, bir veya daha fazla kullanmakla sınırlıdır <xref:System.Windows.Setter> stil veya şablon burada uygulanan nesneyi diğer özelliklerini ayarlamak için öğeleri.  
  
 Çok çeşitli olası değerleri olan bir özellik tetikleyicisi "if" koşulu dengelemek için onu kullanarak varsayılan olarak, aynı özellik değerini ayarlamak için genellikle önerilir bir <xref:System.Windows.Setter>. Bu şekilde <xref:System.Windows.Trigger> kapsanan ayarlayıcı tetikleyici koşul true olduğunda önceliğe sahip olur ve <xref:System.Windows.Setter> olmayan içinde bir <xref:System.Windows.Trigger> tetikleyici koşul false olduğunda önceliğe sahip.  
  
 Özellik tetikleyicileri aynı öğede başka bir özellik durumunu temel senaryolar için burada bir veya daha fazla görünüm özelliklerini değiştirmeniz gerekir, genellikle uygundur.  
  
 Özellik tetikleyicileri hakkında daha fazla bilgi için bkz: [stil ve şablon oluşturma](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
