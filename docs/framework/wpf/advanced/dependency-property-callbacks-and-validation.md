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
ms.openlocfilehash: c5f7439753037aeb5c2ff558da63e063ad65a5e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186433"
---
# <a name="dependency-property-callbacks-and-validation"></a>Bağımlılık Özelliği Geri Aramaları ve Doğrulama
Bu konu, doğrulama belirleme, özelliğin etkili değeri değiştirildiğinde çağrılan geri aramalar ve geçersiz kılma gibi özellik ile ilgili özellikler için alternatif özel uygulamalar kullanarak bağımlılık özelliklerinin nasıl oluşturulacak olduğunu açıklar değer belirleme üzerinde olası dış etkiler. Bu konu, bu teknikleri kullanarak varsayılan özellik sistemi davranışlarını genişletmenin uygun olduğu senaryoları da tartışır.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliğini uygulamanın temel senaryolarını ve meta verilerin özel bağımlılık özelliğine nasıl uygulandığını anladığınızı varsayar. Bağlam için [Özel Bağımlılık Özellikleri](custom-dependency-properties.md) ve Bağımlılık Özelliği Meta [verilerine](dependency-property-metadata.md) bakın.  
  
<a name="Validation_Callbacks"></a>
## <a name="validation-callbacks"></a>Doğrulama Geri Aramaları  
 Doğrulama geri aramaları, ilk kaydettiğinizde bir bağımlılık özelliğine atanabilir. Doğrulama geri arama özelliği meta verilerinin bir parçası değildir; yöntemin <xref:System.Windows.DependencyProperty.Register%2A> doğrudan bir girişidir. Bu nedenle, bir bağımlılık özelliği için bir doğrulama geri arama oluşturulduktan sonra, yeni bir uygulama tarafından geçersiz kılınamaz.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Geri aramalar, nesne değeri sağlayacak şekilde uygulanır. Sağlanan `true` değer özellik için geçerliyse geri dönerler; aksi takdirde, `false`geri dönerler. Özelliğin, özellik sistemine kayıtlı türe göre doğru türde olduğu varsayılır, bu nedenle geri aramalar içindeki tür kontrol normalde yapılmaz. Geri aramalar özellik sistemi tarafından çeşitli işlemlerde kullanılır. Bu, varsayılan değere göre ilk tür başlatmayı, <xref:System.Windows.DependencyObject.SetValue%2A>çağırarak programlı değişikliği veya sağlanan yeni varsayılan değerle meta verileri geçersiz kılmayı denemeyi içerir. Doğrulama geri arama bu işlemlerden herhangi biri tarafından `false`çağrılır ve döndürür, sonra bir özel durum yükseltilir. Uygulama yazarları bu özel durumları işlemek için hazır olmalıdır. Doğrulama geri aramalarının yaygın kullanımı, numaralandırma değerlerini doğrulamak veya özellik sıfır veya daha büyük olması gereken ölçümler ilerlerken tamsayılar veya iki katına çıkarma değerlerini doğrulamaktır.  
  
 Doğrulama geri aramaları özellikle örnek doğrulayıcılar değil, sınıf doğrulayıcıları olarak tasarlanmıştır. Geri arama parametreleri, doğrulanması <xref:System.Windows.DependencyObject> gereken özelliklerin ayarlandığı belirli bir iletişim kurmaz. Bu nedenle doğrulama geri aramaları, bir özelliğin örneğine özgü değerinin diğer özelliklerin örneğine özgü değerleri gibi etkenlere bağlı olduğu veya özellik değerini etkileyebilecek olası "bağımlılıkları" uygulamak için yararlı değildir veya çalışma zamanı durumu.  
  
 Aşağıda çok basit bir doğrulama geri arama senaryosu için örnek kod: <xref:System.Double> ilkel olarak yazılan <xref:System.Double.PositiveInfinity> bir <xref:System.Double.NegativeInfinity>özelliğin olmadığını doğrulama veya .  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Zorlama Değeri Geri Aramaları ve Özellik Değiştirilen Olaylar  
 Zorlama değeri geri aramaları, bir <xref:System.Windows.DependencyObject> bağımlılık özelliğinin değeri <xref:System.Windows.PropertyChangedCallback> değiştiğinde özellik sistemi tarafından çağrılan uygulamalar gibi, özellikler için belirli bir örneği geçer. Bu iki geri aramayı birlikte kullanarak, bir özellikteki değişikliklerin başka bir özelliği zorlamaya veya yeniden değerlendirmeye zorladığı öğeler üzerinde bir dizi özellik oluşturabilirsiniz.  
  
 Bağımlılık özelliklerinin bağlantısını kullanmak için tipik bir senaryo, öğenin her biri minimum ve maksimum değer için bir özellik ve gerçek veya geçerli değer için üçüncü bir özellik tuttuğu bir kullanıcı arabirimi odaklı özelliğiniz olmasıdır. Burada, en büyük değer yeni en büyük değeri aşacak şekilde ayarlanmışsa, geçerli değeri yeni maksimumdan büyük olmayacak şekilde ve en az geçerli ile benzer bir ilişki için zorlarsınız.  
  
 Aşağıda, bu ilişkiyi gösteren üç bağımlılık özelliğinden sadece biri için çok kısa bir örnek kod verilmiştir. Örnek, Bir `CurrentReading` Min/Max/Current ilgili *Okuma özellikleri kümesinin özelliğinin nasıl kaydolduğunu gösterir. Önceki bölümde gösterildiği gibi doğrulama kullanır.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Geçerli için değiştirilen özellik geri çağırma, bu diğer özellikler için kayıtlı olan zorlama değeri geri aramaları açıkça çağırarak, değişikliği diğer bağımlı özelliklere iletmek için kullanılır:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Zorlama değeri geri arama, geçerli özelliğin bağımlı olduğu özelliklerin değerlerini denetler ve gerekirse geçerli değeri zorlamaz:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Özelliklerin varsayılan değerleri zorla rıdda değildir. Bir özellik değerinin hala ilk varsayılan değeri varsa veya diğer değerleri <xref:System.Windows.DependencyObject.ClearValue%2A>' ile temizleyerek varsayılan değere eşit bir özellik değeri oluşabilir.  
  
 Zorlama değeri ve özellik değiştirilen geri aramalar özellik meta verilerinin bir parçasıdır. Bu nedenle, belirli bir bağımlılık özelliği için geri aramaları, türünüzdeki bu özelliğin meta verilerini geçersiz kılarak, bağımlılık özelliğinin sahibi olan türden türediğiniz bir türde var olduğu için değiştirebilirsiniz.  
  
<a name="Advanced"></a>
## <a name="advanced-coercion-and-callback-scenarios"></a>Gelişmiş Zorlama ve Geri Arama Senaryoları  
  
### <a name="constraints-and-desired-values"></a>Kısıtlamalar ve İstenilen Değerler  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> Geri aramalar, beyan ettiğiniz mantığa uygun olarak bir değeri zorlamak için özellik sistemi tarafından kullanılır, ancak yerel olarak ayarlanmış bir özelliğin zorla değerdeğeri yine de dahili olarak "istenen değeri" korur. Kısıtlamalar, uygulama ömrü boyunca dinamik olarak değişebilen diğer özellik değerlerine dayanıyorsa, zorlama kısıtlamaları da dinamik olarak değiştirilir ve kısıtlı özellik, istenilen değere yaklaşmak için değerini değiştirebilir. yeni kısıtlamalar göz önüne alındığında mümkündür. Tüm kısıtlamalar kaldırılırsa, değer istenilen değer haline gelir. Dairesel bir şekilde birbirine bağımlı olan birden çok özelliğiniz varsa, oldukça karmaşık bağımlılık senaryoları tanıyabilirsiniz. Örneğin, Min/Max/Current senaryosunda, Minimum ve Maksimum kullanıcı ayarlanabilir olmasını seçebilirsiniz. Bu öyleyse, Maksimum'un her zaman Minimum'dan büyük olduğunu ve bunun tersi olduğunu zorlamanız gerekebilir. Ancak bu zorlama etkinse ve Maksimum Minimum'a zorlanırsa, Akımı her ikisine de bağımlı olduğu ve sıfır olan değerler arasındaki aralıkla sınırlandırıldığı için, kararsız bir durumda bırakır. Daha sonra, Maksimum veya Minimum ayarlanırsa, Geçerli'nin istenen değeri hala depolandığı ve kısıtlamalar gevşetildikçe istenen değere ulaşmaya çalıştığı için, Geçerli değerlerden birini "takip" eder gibi görünür.  
  
 Karmaşık bağımlılıklarla teknik olarak yanlış bir şey yoktur, ancak çok sayıda yeniden değerlendirme gerektiriyorsa hafif bir performans zararı olabilir ve kullanıcı kullanıcı larını doğrudan etkiliyorsa da kafa karıştırıcı olabilirler. Değiştirilen özellik ve zorlama değeri geri aramaları ile dikkatli olun ve denenen zorlamanın mümkün olduğunca açık bir şekilde ele alınabilmesini ve "aşırı kısıtlama" sağlamadığından emin olun.  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Değer Değişikliklerini İptal Etmek Için Zorlama Değerini Kullanma  
 Özellik sistemi, değeri <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.DependencyProperty.UnsetValue> özel bir durum olarak döndüren leri ele alacaktır. Bu özel durum, <xref:System.Windows.CoerceValueCallback> çağrılması ile sonuçlanan özellik değişikliğinin özellik sistemi tarafından reddedilmesi ve özellik sisteminin bunun yerine mülkün sahip olduğu önceki değeri bildirmesi gerektiği anlamına gelir. Bu mekanizma, eş zamanlı olarak başlatılan bir özellik değişikliklerinin geçerli nesne durumu için hala geçerli olup olmadığını denetlemek ve değilse değişiklikleri bastırmak için yararlı olabilir. Başka bir olası senaryo, bildirilen değerden hangi özellik değeri belirleme bileşeninin sorumlu olduğuna bağlı olarak bir değeri seçerek bastırabilmektir. Bunu yapmak için, geri <xref:System.Windows.DependencyProperty> arama ve özellik tanımlayıcısı için giriş olarak geçirilen <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>kullanabilirsiniz , <xref:System.Windows.ValueSource>ve sonra .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
