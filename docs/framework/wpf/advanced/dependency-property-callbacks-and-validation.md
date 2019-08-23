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
ms.openlocfilehash: 7f00961ba100700c68936cc33facfdc758c77d3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940818"
---
# <a name="dependency-property-callbacks-and-validation"></a>Bağımlılık Özelliği Geri Aramaları ve Doğrulama
Bu konuda, doğrulama belirleme, özelliğin etkin değeri değiştirildiğinde çağrılan geri çağrılar ve geçersiz kılma gibi özelliklerle ilgili özellikler için alternatif özel uygulamalar kullanılarak bağımlılık özelliklerinin nasıl oluşturulacağı açıklanmaktadır. Bunun dışında, değer belirleme üzerindeki etkiler. Bu konuda Ayrıca, bu teknikleri kullanarak varsayılan özellik sistem davranışlarındaki genişlemenin uygun olduğu senaryolar ele alınmaktadır.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliği uygulama ve meta verilerin özel bir bağımlılık özelliğine uygulanma şeklini anladığınızı varsayar. Bağlam için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md) ve [bağımlılık özelliği meta verileri](dependency-property-metadata.md) .  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Doğrulama geri çağırmaları  
 Doğrulama geri çağırmaları, ilk kez kaydettiğinizde bir bağımlılık özelliğine atanabilir. Doğrulama geri çağırması, özellik meta verilerinin bir parçası değildir; Bu, <xref:System.Windows.DependencyProperty.Register%2A> yönteminin doğrudan bir girişi olur. Bu nedenle, bir bağımlılık özelliği için bir doğrulama geri çağırması oluşturulduktan sonra, yeni bir uygulama tarafından geçersiz kılınamaz.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Geri çağrılar bir nesne değeri sağlandıklarından uygulanır. Bunlar, `true` belirtilen değer özelliği için geçerliyse döndürülür; Aksi takdirde, döndürülür. `false` Özelliğin özellik sistemiyle kaydedilen tür için doğru türde olduğu varsayılır, bu nedenle geri çağırmalar içindeki tür denetimi normalde yapılmaz. Geri çağrılar, çeşitli farklı işlemlerde özellik sistemi tarafından kullanılır. Bu, varsayılan değer tarafından başlangıç türü başlatmayı, çağırarak <xref:System.Windows.DependencyObject.SetValue%2A>programlı değişikliği veya belirtilen yeni varsayılan değerle meta verileri geçersiz kılmaya çalışır. Doğrulama geri çağırması bu işlemlerden herhangi biri tarafından çağrılırsa ve döndürürse `false`, bir özel durum oluşturulur. Uygulama yazarları bu özel durumları işleyecek şekilde hazırlanmalıdır. Doğrulama geri çağırmaların ortak kullanımı, numaralandırma değerlerini doğrulayarak veya özellik sıfır veya daha büyük olması gereken ölçümleri ayarladığında, tamsayıların değerlerini kısıtlayan veya Double değerleri kısıtlayan.  
  
 Doğrulama geri çağırmaları özellikle, örnek Doğrulayıcıları değil sınıf Doğrulayıcıları olmak üzere tasarlanmıştır. Geri aramanın parametreleri, doğrulanacak özelliklerin ayarlandığı belirli <xref:System.Windows.DependencyObject> bir iletişim kurmaz. Bu nedenle, doğrulama geri çağırmaları bir özellik değerini etkileyebilecek olası "bağımlılıkları" zorlama için yararlı değildir, burada bir özelliğin örneğe özgü değeri diğer özelliklerin örneğe özgü değerleri gibi faktörlere bağlı olarak veya çalışma zamanı durumu.  
  
 Aşağıda, çok basit bir doğrulama geri çağırma senaryosuna yönelik örnek kod verilmiştir: <xref:System.Double> ilkel olarak yazılan bir özelliğin veya <xref:System.Double.NegativeInfinity>olmadığı <xref:System.Double.PositiveInfinity> doğrulanıyor.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Coerce değeri geri çağırmaları ve özellik değişti olayları  
 Zorunlu değer geri çağırmaları, bağımlılık özelliğinin <xref:System.Windows.DependencyObject> değeri değiştiğinde özellik sistemi tarafından çağrılan <xref:System.Windows.PropertyChangedCallback> uygulamalar gibi, özellikler için belirli örneği geçirir. Bu iki geri çağırmaları birlikte kullanarak, bir özellikte yapılan değişikliklerin başka bir özelliğin zorla veya yeniden değerlemeyi zorlamasının zorlanacağı öğelerde bir dizi özellik oluşturabilirsiniz.  
  
 Bağımlılık özelliklerinin bir bağlantı kullanımı için tipik bir senaryo, en düşük ve en yüksek değer ve gerçek ya da geçerli değer için üçüncü bir özellik olan öğenin her birini bir özellik taşıdığı bir kullanıcı arabirimi temelli özelliğine sahip olduğunuz durumlar olur. Burada, en büyük değer, geçerli değerin yeni en yüksek değeri aşması için ayarlandıysa, geçerli değeri yeni en büyük değerinden büyük olmayacak şekilde ve en düşük ile geçerli olan benzer bir ilişkiyi zorlamak isteyeceksiniz.  
  
 Aşağıda, bu ilişkiyi gösteren üç bağımlılık özelliklerinden yalnızca biri için çok kısa bir örnek kod verilmiştir. Örnek, bir en düşük `CurrentReading` /en yüksek/geçerli ilişkili * okuma özellikleri kümesinin özelliğinin nasıl kaydedildiğini gösterir. Önceki bölümde gösterildiği gibi doğrulamayı kullanır.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Geçerli için geri çağırma özelliği, değişikliği diğer bağımlı özelliklerle iletmek için kullanılır ve bu diğer özellikler için kaydedilen zorunlu değer geri çağırmaları açıkça çağrılır:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Zorunlu değer geri çağırması, geçerli özelliğin potansiyel olarak bağlı olduğu özelliklerin değerlerini denetler ve gerekirse geçerli değeri zorlar:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Özelliklerin varsayılan değerleri zorlanmaz. Varsayılan değere eşit bir özellik değeri, bir özellik değeri hala başlangıçtaki varsayılan değeri varsa veya ile <xref:System.Windows.DependencyObject.ClearValue%2A>diğer değerleri temizleyerek meydana gelebilir.  
  
 Coerce değeri ve özellik değiştirme geri çağırmaları özellik meta verilerinin bir parçasıdır. Bu nedenle, belirli bir bağımlılık özelliği için geri çağırmaları, bu özelliğe ait meta verileri geçersiz kılarak, bağımlılık özelliğine sahip olan türden türettiğiniz bir tür üzerinde var olduğu gibi değiştirebilirsiniz.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Gelişmiş zorlama ve geri arama senaryoları  
  
### <a name="constraints-and-desired-values"></a>Kısıtlamalar ve Istenen değerler  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Geri çağrılar, bildirdiğiniz mantığa uygun olarak bir değeri zorlamak için özellik sistemi tarafından kullanılır, ancak yerel olarak ayarlanmış özelliğin bir zorunlu değeri, dahili olarak "istenen değeri" devam edecektir. Kısıtlamalar, uygulama ömrü boyunca dinamik olarak değiştirilebilen diğer özellik değerlerini temel alıyorsa, zorlama kısıtlamaları da dinamik olarak değiştirilir ve kısıtlanmış Özellik değeri, istenen değere yakın şekilde almak için değerini değiştirebilir yeni kısıtlamalar verilme olasılığı vardır. Tüm kısıtlamalar yükseltilmemiş ise değer istenen değer olacaktır. Döngüsel bir şekilde birbirlerine bağımlı birden fazla özellik varsa, oldukça karmaşık bazı bağımlılık senaryolarına neden olabilirsiniz. Örneğin, Min/Max/Current senaryosunda, en az ve en fazla kullanıcı ayarlanabilir olmasını seçebilirsiniz. Bu durumda, en yüksek değeri en düşük olan ve tam tersi olarak değiştirmeniz gerekebilir. Ancak, bu zorlama etkin ise ve en fazla minimum değere zorsa, her ikisine de bağlı olduğundan ve değeri sıfır olan değerler arasındaki aralığa sınırlı olduğundan, geçerli olmayan bir durumda kalır. Daha sonra, en yüksek veya en düşük değeri ayarlanıyorsa, geçerli geçerli değeri hala depolandığından ve kısıtlamalar gevşmiş olduğu için istenen değere ulaşmaya çalıştığından, şu değerlerden birini "takip et" olarak görünür.  
  
 Karmaşık bağımlılıklarda Teknik olarak yanlış bir şey yoktur, ancak çok sayıda yeniden deneme gerektiren ve kullanıcı ARABIRIMI doğrudan etkiliyorsa kullanıcıları kafa karıştırıcı olabilecek hafif bir performans olabilir. Özellik değişikliği ve coerce değeri geri çağırmaları konusunda dikkatli olun ve denenmekte olan zorlamasının mümkün olduğunca kesin olarak değerlendirileceğini ve "aşırı kısıtlama" gerçekleştirmeyeceğini unutmayın.  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Değer değişikliklerini Iptal etmek için CoerceValue kullanma  
 Özellik sistemi, değeri <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.DependencyProperty.UnsetValue> özel bir durum olarak döndüren her türlü ele alınacaktır. Bu özel durum, <xref:System.Windows.CoerceValueCallback> Çağrılmakta olan özellik değişikliğinin özellik sistemi tarafından reddedilmesi ve özellik sisteminin bunun yerine özelliğin sahip olduğu önceki değeri rapor etmesi gerektiği anlamına gelir. Bu mekanizma, zaman uyumsuz olarak başlatılan bir özellikte yapılan değişikliklerin geçerli nesne durumu için hala geçerli olduğunu denetlemek ve değilse değişiklikleri bastırmak için yararlı olabilir. Başka bir olası senaryo, hangi özellik değeri belirleme bileşeninin raporlanan değerden sorumlu olduğuna bağlı olarak bir değeri seçmeli olarak gizlenebilir. Bunu yapmak için, geri çağırma ve özellik <xref:System.Windows.DependencyProperty> tanımlayıcısı ' nı <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>giriş olarak kullanabilir ve sonra öğesini işleyebilirsiniz <xref:System.Windows.ValueSource>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
