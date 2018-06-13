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
ms.openlocfilehash: ac2a44eb92e384851bbe6ac860fd9b46d3377a06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547657"
---
# <a name="property-change-events"></a>Özellik Değiştirme Olayları
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yanıt olarak bir özellik değerinde bir değişiklik ortaya çeşitli olaylarını tanımlar. Genellikle bir bağımlılık özelliği özelliğidir. Olay bazen yönlendirilmiş olay ve bazı durumlarda standart bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay. Diğer özellik değişikliklerini genellikle ise bazı özellik değişikliklerini daha uygun bir öğe ağacı üzerinden yönlendirilir çünkü olay tanımını senaryo bağlı olarak değişir sorun nerede özelliği değiştirildi nesnesine yalnızca biri.  
  
## <a name="identifying-a-property-change-event"></a>Bir özellik değişim olayı tanımlama  
 Özellik değişikliği rapor olayların tümü açıkça ya da bir imza desen veya bir adlandırma deseni, bir özellik değişti olayı olarak tanımlanır. Genellikle, Olay açıklaması [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] belgelerine gösteren olay doğrudan bir özellik değeri değişiklik bağlıdır ve özelliğe ve olaya arasında çapraz başvuru sağlar.  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged olayları  
 Belirli olaylar, bir olay veri türünü ve özellik değişikliği olayları için açıkça kullanılır temsilci kullanın. Olay veri türü <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, ve temsilci <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Olay verileri ve temsilci işleyici tanımlarken değiştirme özelliği gerçek türünü belirtmek için kullanılan bir genel tür parametresi var. Olay verileri iki özellikler içeren <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> ve <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, hangi hem de sonra tür bağımsız değişkeni olarak olay verileri geçirilir.  
  
 Adı "Yönlendirilmiş" bölümü özellik değişti olayını yönlendirilmiş olay olarak kayıtlı olduğunu gösterir. Özellik değişti olayını yönlendirme avantajı değerleri alt öğeleri (denetimin bileşik parça) özelliklerini değiştirirseniz, üst düzey bir denetimin özellik değişti olayları kullanılabilmesidir. Örneği için bir araya getirir bir denetim oluşturabilirsiniz bir <xref:System.Windows.Controls.Primitives.RangeBase> gibi denetleyen bir <xref:System.Windows.Controls.Slider>. Varsa değerini <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> kaydırıcı bölümü değişikliklerinde özelliği, üst denetim yerine bölümü değişiklik işlemek isteyebilirsiniz.  
  
 Bir eski ve yeni bir değer olduğundan, bu olay işleyicisi için özellik değeri bir doğrulayıcı kullanmak için tempting olabilir. Bununla birlikte, çoğu özellik değişti olayları tasarım amacı değil. Genellikle, değerleri böylece kodunuzu diğer mantığı alanlarında bu değerleri üzerinde çalışabilir, ancak gerçekte gelen değerler olay işleyici içinde değiştirilmesi önerilmez sağlanır ve işleyicinizi nasıl uygulandığını bağlı olarak istenmeyen özyineleme neden olabilir .  
  
 Özel bir bağımlılık özelliği özelliğinizi ise veya örneklemesi kod tanımlandığı türetilmiş bir sınıf ile çalışıyorsanız, içinde yerleşik olan özellik değişikliklerini izleme için bir daha iyi bir düzenek yoktur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi: özellik sistem geri çağırmaları <xref:System.Windows.CoerceValueCallback> ve <xref:System.Windows.PropertyChangedCallback>. Nasıl kullanabileceğiniz hakkında daha fazla ayrıntı için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi doğrulama ve zorlama, için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md) ve [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged olayları  
 Özellik değişti olayını senaryosunun bir parçası olan türlerini başka bir çiftidir <xref:System.Windows.DependencyPropertyChangedEventArgs> ve <xref:System.Windows.DependencyPropertyChangedEventHandler>. Bu özellik değişiklikleri olaylarını yönlendirilmeyen; Standart [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olaylar. <xref:System.Windows.DependencyPropertyChangedEventArgs> türünden türemez çünkü raporlama türü olağan dışı olay verisi <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> yapısı, bir sınıf.  
  
 Kullanın olayları <xref:System.Windows.DependencyPropertyChangedEventArgs> ve <xref:System.Windows.DependencyPropertyChangedEventHandler> biraz daha ortak olan `RoutedPropertyChanged` olaylar. Bu türlerini kullanan bir olay örneğidir <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Gibi <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> özelliği için eski ve yeni bir değer de bildirir. Ayrıca, aynı düşünceleri ne yapabileceğiniz hakkında değerleriyle geçerlidir; Bu genellikle olaya yanıt olarak gönderici değerlerine yeniden değiştirmeye önerilmez.  
  
## <a name="property-triggers"></a>Özellik tetikleyicileri  
 Bir yakından ilgili özellik değişti olayı için bir özellik tetikleyici kavramdır. Özellik tetikleyici bir stil veya şablon içinde oluşturulur ve burada özellik tetikleyici atandığı özellik değere göre koşullu bir davranış oluşturmanızı sağlar.  
  
 Özelliği bir özellik tetikleyici için bir bağımlılık özelliği olmalıdır. Bunu olabilir (ve sıklıkla) salt okunur bağımlılık özelliği. Ne zaman bir denetim tarafından kullanıma sunulan bir bağımlılık özelliği en azından kısmen özellik tetikleyici olacak şekilde tasarlanmıştır için iyi bir özellik adı "Olan" ile başlayıp başlamadığını göstergesidir. Bu adlandırma sahip genellikle salt okunur Boolean bağımlılık özelliği birincil senaryo özelliği için gerçek zamanlı kullanıcı arabirimine sonuçları olabilir ve bu nedenle bir özellik tetikleyici adaydır denetim durumu burada raporlama özelliklerdir.  
  
 Bu özelliklerden bazıları de bir özel özellik değişti olayını sahiptir. Örneğin, özellik <xref:System.Windows.UIElement.IsMouseCaptured%2A> özellik değişti olayını sahip <xref:System.Windows.UIElement.IsMouseCapturedChanged>. Salt okunur giriş sistemi tarafından ayarlanan değeriyle özelliği ve giriş sistemi başlatır <xref:System.Windows.UIElement.IsMouseCapturedChanged> her gerçek zamanlı değişir.  
  
 Özellik tetikleyici kullanarak, bir özellik değişikliği için doğru özellik değişti olayını ile karşılaştırıldığında, bazı sınırlamaları vardır.  
  
 Özellik tetikleyicileri bir tam eşleşme mantığı çalışır. Bir özellik ve tetikleyici hareket eder belirli değeri belirten bir değer belirtin. Örneğin: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Bu sınırlama nedeniyle, Boolean özellikleri veya olası değer aralığı her örneği için bir tetikleyici tanımlamak için yönetilebilir olduğu adanmış numaralandırma değeri ele özellikleri için özellik tetikleyici kullanımları çoğunluğu olacaktır. Özellik tetikleyicileri yalnızca bir öğe sayısını sıfır ulaştığında gibi özel değerler var olabilecek veya özellik değeri sıfırdan uzağa doğru yeniden değiştiğinde durumlarda hesapları hiçbir tetikleyici olacaktır (INSTEAD OF Tetikleyicileri tüm durumlarda, bir kod gerekebilir olay işleyicisi burada veya değeri sıfır olduğunda tetikleyici durumundan yeniden değiştirir varsayılan davranışı).  
  
 Özellik tetikleyici sözdizimi, bir "," deyimi programlamada benzerdir. Tetikleme koşulu true ise, ardından özellik tetikleyici "body" "yürütülür". Özellik tetikleyici "body" kod değil, biçimlendirme. Bir veya daha fazla kullanarak bu biçimlendirme sınırlıdır <xref:System.Windows.Setter> öğeler stil veya şablon yere uygulanmakta nesnesinin diğer özellikleri ayarlayın.  
  
 Çok çeşitli olası değerler sahip bir özellik tetikleyici "IF" koşulunu dengelemek için bunu kullanarak aynı özellik değeri varsayılan olarak ayarlamak için genellikle önerilir bir <xref:System.Windows.Setter>. Bu şekilde <xref:System.Windows.Trigger> kapsanan ayarlayıcı tetikleme koşulunu true olduğunda önceliğe sahip olur ve <xref:System.Windows.Setter> olmayan içinde bir <xref:System.Windows.Trigger> Tetikleme koşulu false olduğunda önceliğe sahip olur.  
  
 Özellik tetikleyicileri başka bir özellik aynı öğede durumunu dayalı olduğu bir veya daha fazla görünüm özelliklerini değiştirmeniz gerekir, senaryoları için genellikle uygundur.  
  
 Özellik tetikleyicileri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
