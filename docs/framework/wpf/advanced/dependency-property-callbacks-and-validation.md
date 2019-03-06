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
ms.openlocfilehash: ff7cbd995ba52f3cea712cb02b72f91d40422c33
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363936"
---
# <a name="dependency-property-callbacks-and-validation"></a>Bağımlılık Özelliği Geri Aramaları ve Doğrulama
Bu konuda doğrulama belirlemeyi özelliğinin geçerli değeri değiştiğinde çağrılan geri çağırmaları gibi özellik güvenlikle ilgili özellikler için diğer özel uygulamaları kullanarak ve geçersiz kılma bağımlılık özellikleri oluşturmayı açıklar olası değer belirleme etkileri dışında. Bu konuda Ayrıca bu teknikler kullanılarak varsayılan özellik sistemi davranışlarını genişletme uygun olduğu senaryolar açıklanmaktadır.  
  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığı altında bağımlılık özelliği ve özel bağımlılık özelliği için meta verileri nasıl uygulanacağını uygulama temel senaryolar anladığınızı varsayar. Bkz: [özel bağımlılık özellikleri](custom-dependency-properties.md) ve [bağımlılık özelliği meta verisi](dependency-property-metadata.md) bağlamı için.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Doğrulama geri çağırmaları  
 İlk kez kaydederken bir bağımlılık özelliği için doğrulama geri çağırmaları atanabilir. Doğrulama geri çağırma özelliği meta verileri bir parçası değildir; doğrudan bir girdisi olduğunu <xref:System.Windows.DependencyProperty.Register%2A> yöntemi. Bu nedenle, bir bağımlılık özelliği için bir doğrulama geri çağırma oluşturulduktan sonra yeni bir uygulama tarafından değiştirilemiyor.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Bir nesne değeri sağlanan şekilde geri çağırmaları uygulanır. Döndürmeleri `true` ; özelliği için belirtilen değer geçerliyse Aksi takdirde, döndürmeleri `false`. Geri çağırmaları içinde tür denetimi normalde yapılmazsa bu nedenle özellik türü başına doğru türde özellik sistemi ile kayıtlı olduğundan varsayılır. Geri çağırmaları farklı işlemler çeşitli özellik sistemi tarafından kullanılır. Çağırarak bu programlı değişiklik, varsayılan değere göre ilk türü başlatma içerir <xref:System.Windows.DependencyObject.SetValue%2A>, ya da yeni varsayılan değer sağlanan meta verileri geçersiz kılma girişiminde bulunur. Doğrulama geri çağırma bu işlemlerden herhangi biri tarafından çağrılır ve döndürür, `false`, sonra da bir özel durum oluşturulur. Uygulama yazarları bu özel durumları işlemeye hazırlıklı olmalıdır. Genel bir doğrulama geri çağırmaları kullanımını numaralandırma değerlerinin doğrulama veya sıfır olmalıdır ölçümleri özellik kümeleri kullanırken, tamsayı veya double değerleri sınırlamak veya büyük.  
  
 Doğrulama geri çağırmaları, özellikle sınıfı doğrulayıcıları, değil örneği doğrulayıcıları olacak şekilde tasarlanmıştır. Belirli bir geri çağırma parametreleri iletişim kurmazlar <xref:System.Windows.DependencyObject> hangi doğrulamak için özellikler kümesi. Bu nedenle doğrulama geri çağırmaları örneği-özel bir özelliğin değerini örneği özgü diğer özelliklerin değerlerine gibi etkenlere bağlı olduğu bir özellik değeri etkileyebilir "bağımlılıklar" olası zorlarken yararlıdır değil veya çalışma zamanı durumu.  
  
 Basit doğrulama geri çağırma senaryosu için örnek kod aşağıda verilmiştir:, doğrulama olarak belirlenmiş bir özellik <xref:System.Double> ilkel olmayan <xref:System.Double.PositiveInfinity> veya <xref:System.Double.NegativeInfinity>.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Coerce değeri geri aramaları ve özellik değişti olayları  
 Coerce değeri geri aramaları belirli geçirmek <xref:System.Windows.DependencyObject> örneği gibi özellikler için <xref:System.Windows.PropertyChangedCallback> bir bağımlılık özelliğinin değeri değiştiğinde, özellik sistemi tarafından çağrılan uygulamaları. Bu iki geri çağırmaları birlikte kullanarak, bir özellik değişiklikleri zorlama veya başka bir özelliğin yeniden değerlendirme burada zorlayacak öğeleri üzerinde bir dizi özellik oluşturabilirsiniz.  
  
 Burada öğesi bir özelliği her minimum ve maksimum değeri tutan bir kullanıcı arayüzüne özelliği ve gerçek veya geçerli bir değer için üçüncü bir özellik varsa, bir bağlantı bağımlılık özellikleri kullanmak için tipik bir senaryodur. Burada, en fazla geçerli değeri yeni üst sınırı aşıldı şekilde değiştirdiyseniz, yeni maksimum ve minimum geçerli için benzer bir ilişki daha büyük bir değer için geçerli değer coerce istersiniz.  
  
 Bu ilişkiyi gösteren üç bağımlılık özellikleri yalnızca biri için çok kısa bir örnek kod aşağıda verilmiştir. Örnekte gösterildiği nasıl `CurrentReading` Min/Maks/geçerli özelliğini ayarlayın, ilgili * özellikleri okunurken kaydedilir. Önceki bölümde gösterildiği gibi doğrulamayı kullanır.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Özellik değişti geri çağırma geçerli, açıkça bu diğer özellikler için kayıtlı coerce değeri geri aramaları çağırarak bağımlı diğer özellikleri değişiklik iletmek için kullanılır:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Coerce değeri geri çağırma geçerli özellikle büyük olasılıkla bağlı olduğu ve gerekirse, geçerli değer olacak şekilde zorlar özelliklerin değerlerini denetler:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  Özelliklerin varsayılan değerlerini zorlanır değil. Özellik değerinin varsayılan değere eşit bir özellik değeri, varsayılan başlangıç hala varsa veya diğer değerler ile temizlenmesi ile ortaya çıkabilecek <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
 Coerce değeri ve özellik değişikliği geri çağırmaları özellik meta verileri bir parçasıdır. Bu nedenle, bağımlılık özelliği, bu özellik için meta veriler geçersiz kılarak sahip olan türden türetilmiş türe göre bulunduğu için belirli bir bağımlılık özelliği geri aramaları değiştirebilirsiniz.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Gelişmiş zorlama ve geri çağırma senaryoları  
  
### <a name="constraints-and-desired-values"></a>Sınırlamalar ve istenen değerleri  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Geri çağırmaları bildirdiğiniz mantığı, ancak yerel olarak ayarlanmış coerced değeri uygun bir değer coerce için özellik sistemi tarafından kullanılacak özellik hala korur "istenen value" dahili olarak. Uygulama ömrü boyunca dinamik olarak değişebildiği diğer özellik değerleri kısıtlamalara dayalı, baskı kısıtlamaları da dinamik olarak değiştirilir ve kısıtlı özelliğin değerini istediğiniz değer olarak olarak yakın almak için değiştirebilirsiniz. yeni kısıtlamalara mümkün. Tüm kısıtlamalar kaldırıldığında, değeri istediğiniz değeri olur. Döngüsel bir şekilde birbirlerine bağımlı olan birden çok özellikleri varsa bazı nispeten karmaşık bağımlılık senaryolar potansiyel olarak çıkarabilir. Örneğin, Min/Maks/geçerli senaryosunda, Minimum ve maksimum kullanıcı ayarlanabilir seçebilirsiniz. Bu durumda, en fazla her zaman az ve büyük olduğunu coerce gerekebilir. Ancak ikisine de bağlı olduğundan ve sıfır değerleri arasında bir aralığa kısıtlanmış, zorlama etkindir ve en az olacak şekilde zorlar, geçerli kısıtlanmasından içinde bırakır. En yüksek veya düşük değiştirdiyseniz, istenen geçerli değerini hala depolandığı ve kısıtlamalar gevşetiliyormuş gibi istediğiniz değeri ulaşmaya için daha sonra geçerli "değerlerden birini izleyin" görünüyor.  
  
 Karmaşık bağımlılıkları ile teknik olarak yanlış bir şey yoktur, ancak çok sayıda reevaluations gerektiren ve kullanıcı arabirimini doğrudan etkileyen de kullanıcılar için kafa karıştırıcı olabilir, küçük bir performans zarar olabilir. Değiştirilen özellik dikkatli olun, Coerce değeri geri aramaları ve denenen zorlama mümkün olduğunca belirsiz olarak davranılıp ve değil "overconstrain" olduğundan emin olun.  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>CoerceValue değer değişiklikleri iptal etmek için kullanma  
 Özellik sistemi tüm işler <xref:System.Windows.CoerceValueCallback> değerini döndüren <xref:System.Windows.DependencyProperty.UnsetValue> bir özel durum olarak. Bu özel durum olarak sonuçlanan özellik değişikliğini anlamına <xref:System.Windows.CoerceValueCallback> çağrılan özellik sistemi tarafından reddedilmesi ve özellik sistemi özelliği önceki değerini yerine bildirmesi. Bu mekanizma, zaman uyumsuz olarak başlatılan bir özellik değişiklikleri geçerli nesne durumu için hala geçerli olduğunu kontrol edin ve aksi takdirde değişiklikleri bastırmak için yararlı olabilir. Özelliğin hangi bileşenin bağlı olarak değer belirleme için bildirilen değer sorumlu olduğu bir değer seçerek gizleyebilirsiniz, başka bir olası senaryodur. Bunu yapmak için kullanabileceğiniz <xref:System.Windows.DependencyProperty> geri çağırma ve özellik tanımlayıcısı için giriş olarak geçirilen <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>ve ardından <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
