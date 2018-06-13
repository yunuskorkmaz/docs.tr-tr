---
title: Bağımlılık Özelliği Geri Aramaları ve Doğrulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], validation
- coerce value callbacks [WPF]
- callbacks [WPF], validation
- dependency properties [WPF], callbacks
- validation of dependency properties [WPF]
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
ms.openlocfilehash: e181c2d9610619587642f982959f809b96b011dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541339"
---
# <a name="dependency-property-callbacks-and-validation"></a>Bağımlılık Özelliği Geri Aramaları ve Doğrulama
Bu konuda doğrulamayı belirleme, özelliğin geçerli değeri değiştiğinde çağrılan geri aramalar gibi özelliği ile ilgili özellikler için alternatif özel uygulamalar kullanarak ve geçersiz kılma bağımlılık özelliklerin nasıl oluşturulacağı açıklanmaktadır olası değeri belirleme etkileri dışında. Bu konuda Ayrıca varsayılan özellik sistemi davranışlarını bu teknikleri kullanarak genişletmenin uygun olduğu senaryolar anlatılmaktadır.  
  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bir bağımlılık özelliği ve meta verilerin özel bir bağımlılık özelliği için nasıl uygulanacağını uygulamanın temel senaryolarını anladığınızı varsayar. Bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) bağlamı için.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Doğrulamalarının  
 İlk kez kaydederken doğrulamalarının bağımlılık özelliği için atanmış olabilir. Doğrulama geri çağırma özellik meta verilerinin bir parçası değildir; bir doğrudan girişi olduğundan <xref:System.Windows.DependencyProperty.Register%2A> yöntemi. Bu nedenle, bir bağımlılık özelliği için bir doğrulama geri çağırma oluşturulduktan sonra yeni bir uygulama tarafından değiştirilemiyor.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Bir nesne değeri sağlanan şekilde geri çağırmaları uygulanır. Döndürmeleri `true` sağlanan değer; özelliği için geçerli ise, aksi takdirde döndürmeleri `false`. Geri aramalar içinde tür denetlemesi normal şekilde yapılmaz şekilde özellik türü başına doğru türde özellik sistemi ile kaydedildiğini varsayılır. Geri aramalar farklı işlemler çeşitli özellik sistemi tarafından kullanılır. Çağırarak bu programlı Değiştir, varsayılan değere göre ilk türü başlatma içerir <xref:System.Windows.DependencyObject.SetValue%2A>, veya sağlanan yeni varsayılan değer ile meta verileri geçersiz kılmak çalışır. Doğrulama geri çağırma bu işlemlerin herhangi biri tarafından çağrılır ve döndürür, `false`, sonra da bir özel durum oluşturuldu. Uygulama yazarları bu özel durumları işlemek için hazırlıklı olmalıdır. Ortak bir doğrulama geri çağırmaları kullanımını numaralandırma değerlerini doğrulama veya özellik sıfır olmalıdır ölçümleri ayarladığında tamsayı veya double değerlerini kısıtlamadır veya daha büyük.  
  
 Doğrulama geri çağırmaları özellikle sınıf doğrulayıcıları, değil örneği doğrulayıcıları olacak şekilde tasarlanmıştır. Geri arama parametrelerini belirli bir iletişim kurmazlar <xref:System.Windows.DependencyObject> üzerinde hangi doğrulamak için özellikleri ayarlayın. Bu nedenle doğrulama geri çağırmaları burada örneğe özgü bir özellik örneğe özgü diğer özelliklerin değerlerine gibi etkenlere bağlı değeri, "bir özellik değeri etkileyebilir bağımlılıkları" olası zorlama için yararlı değildir veya çalışma zamanı durumu.  
  
 Geri arama çok basit doğrulama senaryosu için örnek kod aşağıda verilmiştir:, doğrulama olarak belirtilmiş bir özellik <xref:System.Double> ilkel değil <xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Coerce değeri geri aramalar ve özellik değişikliği olayları  
 Coerce değeri geri aramalar belirli geçirmek <xref:System.Windows.DependencyObject> gibi özellikleri, örneğin <xref:System.Windows.PropertyChangedCallback> bir bağımlılık özelliğinin değeri değiştiğinde özellik sistemi tarafından çağrılan uygulamaları. Bu iki geri aramalar birlikte kullanarak, bir özellik değişiklikleri zorlama veya başka bir özelliğin yeniden değerlendirme burada zorlayacağı öğelerde bir dizi özellik oluşturabilirsiniz.  
  
 Burada öğesi bir özelliği her için minimum ve maksimum değeri tutan bir kullanıcı arayüzüne özelliği ve gerçek veya geçerli değer için üçüncü bir özellik varsa, bağlantı bağımlılık özellikleri kullanmak için tipik bir senaryodur. Burada, en fazla geçerli değeri yeni üst sınırı aştı şekilde değiştirdiyseniz, en fazla yeni maksimum ve minimum geçerli için benzer bir ilişki geçerli bir değere coerce istersiniz.  
  
 Bu ilişkiyi gösteren üç bağımlılık özellikleri yalnızca biri için çok kısa bir örnek kod aşağıda verilmiştir. Örnekte gösterildiği nasıl `CurrentReading` Min/Max/geçerli ayarlamayın ilişkili * özellikleri okunurken kaydedilir. Önceki bölümde gösterildiği gibi doğrulama kullanır.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Özellik değişti geri çağırma geçerli bağımlı diğer özellikleri değişikliği açıkça bu diğer özellikler için kaydedilen coerce değeri geri aramaları çağırılarak kullanılır:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Coerce değeri geri araması geçerli özelliği büyük olasılıkla bağlı olduğu ve gerekirse, geçerli değer olacak şekilde zorlar özelliklerinin değerlerini denetler:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Özelliklerinin varsayılan değerlerini yüklenen değil. Özellik değerinin varsayılan değere eşit bir özellik değeri hala ilk varsayılan varsa veya diğer değerlerle temizleme aracılığıyla oluşabilecek <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Coerce değeri ve özellik değişikliği geri aramalar özellik meta verileri bir parçasıdır. Bu nedenle, bu özellik için meta veriler geçersiz kılarak bağımlılık özelliği sahibi türü öğesinden türetilen bir tür var. gibi belirli bağımlılık özelliği için geri çağırmaları değiştirebilirsiniz.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Gelişmiş zorlama ve geri çağırma senaryoları  
  
### <a name="constraints-and-desired-values"></a>Kısıtlamalar ve istediğiniz değerleri  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Geri aramalar bildirdiğiniz mantığa, ancak yerel olarak ayarlanmış bir coerced değerini uygun bir değer coerce için özellik sistemi tarafından kullanılacak özelliği hala "istenen değeri" dahili olarak korur. Kısıtlamalar uygulama ömrü boyunca dinamik olarak değişebilir diğer özellik değerleri dayanır, baskı kısıtlamaları da dinamik olarak değiştirilir ve kısıtlı özelliği istenen değeri olarak yakın almak için kendi değerini değiştirebilir yeni kısıtlamalara mümkün. Tüm kısıtlamalar kaldırıldığında değeri istenen değeri olur. Döngüsel bir şekilde birbirine bağlı birden çok özellik varsa, bazı oldukça karmaşık bağımlılık senaryolar potansiyel olarak ortaya çıkarabilir. Örneğin, Min/Max/Geçerli senaryoda, Minimum ve maksimum kullanıcı ayarlanabilir tercih. Bu durumda, maksimum her zaman sınırdan küçük ve büyük olduğunu coerce gerekebilir. Ancak ikisine de bağlı olduğundan ve sıfır değerleri arasında bir aralığa kısıtlı bu zorlama etkindir ve en küçük olacak şekilde zorlar, geçerli kısıtlanmasından içinde durumda bırakır. Maksimum veya minimum değer değiştirdiyseniz, istenen değeri hala depolanır ve kısıtlamalar gevşetiliyormuş gibi istenen değere ulaşmaya çalışırken çünkü daha sonra geçerli "değerlerden birini izleyin" göründüğü.  
  
 Karmaşık bağımlılıklar konusunda teknik olarak yanlış bir şey yok ancak çok sayıda reevaluations gerektiren ve kullanıcı arabirimini doğrudan etkiler, ayrıca kullanıcılar için kafa karıştırıcı olabilir, küçük bir performans zarar olabilir. Değiştirilen özellik dikkatli olun, coerce değeri geri çağrıları ve yapılmaya çalışılan baskının mümkün olduğunca kesin bir şekilde işlenebilir ve değil "overconstrain" olduğundan emin olun.  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Değer değişiklikleri iptal etmek için CoerceValue kullanma  
 Özellik sistemi herhangi değerlendirir <xref:System.Windows.CoerceValueCallback> değerini döndüren <xref:System.Windows.DependencyProperty.UnsetValue> bir özel durum olarak. Bu özel durum ile sonuçlandı özellik değişikliği anlamına <xref:System.Windows.CoerceValueCallback> çağrılan özellik sistemi tarafından reddedilmesi ve özellik sistemi yerine özelliği önceki değerini bildirmesi. Bu mekanizma zaman uyumsuz olarak başlatılan değişiklikleri bir özellik için geçerli nesne durumu için hala geçerli olduğundan emin olun ve değilse değişiklikleri bastırma yararlı olabilir. Başka bir olası hangi özellik bileşene bağlı olarak değeri belirleme raporlandığını değeri sorumlu olduğu bir değer seçerek gizleyebilirsiniz senaryodur. Bunu yapmak için kullanabileceğiniz <xref:System.Windows.DependencyProperty> geri çağırma ve özellik tanımlayıcısı için giriş olarak geçirilen <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>ve ardından işleme <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
