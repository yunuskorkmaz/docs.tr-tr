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
ms.openlocfilehash: 06056b492439531aa60becbb7bca250a439bfb68
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567429"
---
# <a name="property-change-events"></a>Özellik Değiştirme Olayları
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]bir özelliğin değerindeki bir değişikliğe yanıt olarak oluşturulan birkaç olayı tanımlar. Genellikle özelliği bir bağımlılık özelliğidir. Olay bazen yönlendirilmiş bir olaydır ve bazen standart ortak dil çalışma zamanı (CLR) olayıdır. Olay tanımı, senaryoya bağlı olarak değişir, çünkü bazı özellik değişiklikleri bir öğe ağacı aracılığıyla daha uygun olduğundan, diğer özellik değişiklikleri genellikle özelliğin değiştiği nesnenin kaygısından kaynaklanır.  
  
## <a name="identifying-a-property-change-event"></a>Özellik değişiklik olayını tanımlama  
 Bir özellik değişikliğini rapor eden tüm olaylar, bir imza deseninin ya da bir adlandırma deseninin virtuale tarafından açıkça bir özellik değiştirildi olayı olarak tanımlanır. Genellikle, SDK belgelerindeki etkinliğin açıklaması, olayın doğrudan bir özellik değeri değişikliğine bağlı olup olmadığını ve özellik ile olay arasında çapraz başvurular sağladığını gösterir.  
  
### <a name="routedpropertychanged-events"></a>Kabatedpropertychanged olayları  
 Belirli olaylar, özellik değişiklik olayları için açıkça kullanılan bir olay veri türü ve temsilcisini kullanır. Olay veri türü <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, ve <xref:System.Windows.RoutedPropertyChangedEventHandler%601>temsilcisidir. Olay verileri ve temsilcisinin her ikisi de, işleyiciyi tanımlarken değişen özelliğin gerçek türünü belirtmek için kullanılan genel bir tür parametresine sahiptir. Olay verileri iki özellik <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> içerir ve <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>her ikisi de olay verilerinde tür bağımsız değişkeni olarak geçirilir.  
  
 Adın "Dolaştırılan" bölümü, özellik değiştirilen olayın yönlendirilmiş olay olarak kaydedildiğini gösterir. Özellik değişti olayını yönlendirmenin avantajı, alt öğelerdeki Özellikler (denetimin bileşik parçaları) değerlerini değiştirmek için bir denetimin en üst düzeyinin Özellik değişmiş olayları almasına sahip olması olabilir. Örneğin, gibi bir <xref:System.Windows.Controls.Primitives.RangeBase> denetimi <xref:System.Windows.Controls.Slider>içeren bir denetim oluşturabilirsiniz. <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> Özelliğin değeri kaydırıcı bölümünde değişirse, bu değişikliği bölüm yerine üst denetimde işlemek isteyebilirsiniz.  
  
 Eski bir değere ve yeni bir değere sahip olduğunuzdan, bu olay işleyicisini Özellik değeri için bir doğrulayıcı olarak kullanmak mümkün olabilir. Bununla birlikte, çoğu özellik tarafından değiştirilen olayların tasarım amacı değildir. Genellikle değerler, kodunuzun diğer Logic alanlarında bu değerler üzerinde işlem yapabilmeniz için sağlanır, ancak gerçekten de olay işleyicisindeki değerleri değiştirmeniz önerilmez ve işleyicinizin nasıl uygulandığına bağlı olarak yanlışlıkla özyineleme yapılmasına neden olabilir .  
  
 Özelliği özel bir bağımlılık özelliği ise veya örnek kodu tanımladığınız türetilmiş bir sınıfla çalışıyorsanız, özellik sisteminde yerleşik olarak bulunan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik değişikliklerinin izlenmesi için çok daha iyi bir mekanizma vardır: özellik sistemi geri <xref:System.Windows.CoerceValueCallback> çağırmaları <xref:System.Windows.PropertyChangedCallback>ve. Doğrulama ve zorlama için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemini nasıl kullanabileceğiniz hakkında daha fazla ayrıntı için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md) ve [Özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged olayları  
 Bir özellik değişmiş olay senaryosunun parçası olan bir diğer tür çifti ve ' <xref:System.Windows.DependencyPropertyChangedEventArgs> <xref:System.Windows.DependencyPropertyChangedEventHandler>dir. Bu özellik değişiklikleri için olaylar yönlendirilmez; Bunlar standart CLR olaylardır. <xref:System.Windows.DependencyPropertyChangedEventArgs>, öğesinden <xref:System.EventArgs>türetilmediği için olağandışı bir olay veri raporlama türüdür; <xref:System.Windows.DependencyPropertyChangedEventArgs> , bir sınıf değil, bir yapıdır.  
  
 Ve <xref:System.Windows.DependencyPropertyChangedEventArgs> kullanan<xref:System.Windows.DependencyPropertyChangedEventHandler> olaylar ,olaylardanbirazdaha`RoutedPropertyChanged` yaygın olarak kullanılır. Bu türleri kullanan bir olaya bir örnek vardır <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Benzer <xref:System.Windows.RoutedPropertyChangedEventArgs%601>şekilde <xref:System.Windows.DependencyPropertyChangedEventArgs> , özelliği için eski ve yeni bir değeri de raporlar. Ayrıca, değerlerle yapabileceklerinizle ilgili dikkat edilecek noktalar geçerlidir; olaya yanıt olarak, gönderen üzerinde değerleri yeniden değiştirmeyi denemeniz önerilmez.  
  
## <a name="property-triggers"></a>Özellik tetikleyicileri  
 Özellik değişti olayına yakından ilgili bir kavram, bir özellik tetikleyicisine sahiptir. Bir stil veya şablon içinde bir özellik tetikleyicisi oluşturulur ve özellik tetikleyicisinin atandığı özelliğin değerine göre koşullu bir davranış oluşturmanıza olanak sağlar.  
  
 Özellik tetikleyicisi özelliği bir bağımlılık özelliği olmalıdır. Salt okuma bağımlılığı özelliği (ve sık olarak) olabilir. Bir denetim tarafından sunulan bağımlılık özelliğinin en az kısmen bir özellik tetikleyicisi olarak tasarlandığına ilişkin iyi bir göstergedir. Özellik adı "SIS" ile başlıyorsa. Bu adlandırmayla ilgili özellikler genellikle, özelliğin birincil senaryosunun gerçek zamanlı kullanıcı arabirimine sonuçlara sahip olabilecek ve bu nedenle bir özellik tetikleyicisi adayından oluşan bir salt okunurdur Boolean Dependency özelliğidir.  
  
 Bu özelliklerden bazılarının Ayrıca özel bir özellik değiştirilmiş olayı vardır. Örneğin, özelliğin <xref:System.Windows.UIElement.IsMouseCaptured%2A> değiştirilen bir olayı <xref:System.Windows.UIElement.IsMouseCapturedChanged>vardır. Özelliğin kendisi salt okunurdur ve değeri giriş sistemi tarafından ayarlanır ve giriş sistemi her gerçek zamanlı değişikliğe göre yükseltilir <xref:System.Windows.UIElement.IsMouseCapturedChanged> .  
  
 Bir özellik değişikliği üzerinde işlem yapmak için bir özellik tetikleyicisi kullanılması, doğru özellik değiştirildi olayı ile karşılaştırıldığında bazı sınırlamalara sahiptir.  
  
 Özellik Tetikleyicileri tam eşleştirme mantığı aracılığıyla çalışır. Tetikleyicinin işlem yapması için belirli bir değeri belirten bir özellik ve bir değer belirtirsiniz. Örneğin: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Bu sınırlama nedeniyle, özellik tetikleyicisi kullanımlarının çoğu, Boole özellikleri veya özel bir numaralandırma değeri alan özellikler için olacaktır, burada olası değer aralığı her durum için bir tetikleyici tanımlamak üzere yeterince yönetilebilir olur. Ya da özellik Tetikleyicileri yalnızca bir öğe sayısı sıfıra ulaştığında ve bu durum, özellik değeri sıfırdan farklı değiştiğinde (tüm durumlar için Tetikleyiciler yerine) yalnızca özel değerler için mevcut olabilir. Burada olay işleyicisi veya değer sıfır olmadığında yeniden tetikleme durumundan geri geçiş yapan varsayılan bir davranış.  
  
 Özellik tetikleyicisi sözdizimi, programlamada bir "if" ifadesine benzer. Tetikleme koşulu true ise, özellik tetikleyicisinin "Body" değeri "yürütülür" olur. Özellik tetikleyicisinin "Body" kodu değil, biçimlendirme. Bu biçimlendirme bir veya daha fazla <xref:System.Windows.Setter> öğe kullanarak stilin veya şablonun uygulandığı nesnenin diğer özelliklerini ayarlamak için sınırlıdır.  
  
 Çok sayıda olası değere sahip olan bir özellik tetikleyicisinin "if" koşulunu kaydırmak için, genellikle aynı özellik değerinin ' ı kullanarak <xref:System.Windows.Setter>varsayılan olarak ayarlanması önerilir. Bu şekilde, <xref:System.Windows.Trigger> Tetikleme koşulu true olduğunda içerilen ayarlayıcı önceliğe sahip olur <xref:System.Windows.Setter> ve tetikleyici koşulu false olduğunda, bir içinde olmayan bir <xref:System.Windows.Trigger> önceliğe sahip olur.  
  
 Özellik Tetikleyicileri genellikle bir veya daha fazla görünüm özelliğinin aynı öğe üzerindeki başka bir özelliğin durumuna göre değiştirilmesi gereken senaryolar için uygundur.  
  
 Özellik Tetikleyicileri hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
