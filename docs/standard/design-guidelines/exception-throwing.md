---
title: Özel Durum Oluşturma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 18927d242c2ed957d2bc9f8b481beeed775a4e4e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741667"
---
# <a name="exception-throwing"></a>Özel Durum Oluşturma
Özel durum-bu bölümde açıklanan oluşturma yönergeleri, yürütme hatası anlamı için iyi bir tanım gerektirir. Yürütme hatası, bir üye için tasarlandıkları şeyi (üye adının ne kadar gösterdiği) yapamayacağı zaman oluşur. Örneğin, `OpenFile` yöntemi çağırana bir açık dosya tutamacı döndüremez, bir yürütme hatası olarak kabul edilir.

 Çoğu geliştirici, sıfıra bölme veya null başvurular gibi kullanım hataları için özel durumları kullanma konusunda rahat hale gelmiştir. Çerçevede, yürütme hataları da dahil olmak üzere tüm hata koşulları için özel durumlar kullanılır.

 ❌ hata kodları döndürmez.

 Özel durumlar, çerçeveler içindeki hataların bildirilme yöntemidir.

 özel durumlar oluşturarak rapor yürütme hatalarıyla ✔️.

 ✔️, kodunuzun daha fazla yürütme için güvenli olmadığı bir durumla karşılaştığında bir özel durum oluşturmak yerine `System.Environment.FailFast` (.NET Framework 2,0 özelliği) çağırarak işlemi sonlandırmaktan yarar.

 ❌, mümkünse normal denetim akışı için özel durumlar kullanmaz.

 Olası yarış koşullarına sahip sistem arızaları ve işlemler haricinde, çerçeve tasarımcıları, kullanıcıların özel durum oluşturmayan kodlar yazabilmesi için API 'Ler tasarlaması gerekir. Örneğin, kullanıcılar özel durum oluşturmayan bir kod yazabilmesi için bir üyeyi çağırmadan önce önkoşulları denetlemek için bir yol sağlayabilirsiniz.

 Başka bir üyenin ön koşulları 'nı denetlemek için kullanılan üye, genellikle test edici olarak adlandırılır ve işi gerçekten yapan üyeye bir doer denir.

 Sınayıcı-doer deseninin kabul edilemez bir performans yükü olabilir. Bu gibi durumlarda, bu şekilde adlandırılan TRY-Parse deseninin göz önünde bulundurulmaları gerekir (daha fazla bilgi için bkz. [özel durumlar ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) ).

 ✔️ özel durum oluşturma performansı etkilerini göz önünde bulundurun. Saniyede 100 ' den yüksek olan throw ücretleri, çoğu uygulamanın performansını önemli ölçüde etkileyebilir.

 ✔️, üye sözleşmesinin ihlal edildiği (sistem hatası yerine) ve bunları sözleşmenin bir parçası olarak kabul eden, genel olarak çağrılabilir Üyeler tarafından oluşturulan tüm özel durumları belgeleyin.

 Sözleşmenin bir parçası olan özel durumlar bir sürümden sonrakine değişmemelidir (yani, özel durum türü değişmemelidir ve yeni özel durumlar eklenmemelidir).

 ❌, herhangi bir seçeneğe göre oluşturabilecek veya olmayan ortak üyelere sahip DEĞILDIR.

 ❌, dönüş değeri veya bir `out` parametresi olarak özel durumlar döndüren ortak üyelere sahip DEĞILDIR.

 Özel durum tabanlı hata raporlama avantajlarının çoğunu yapmak yerine ortak API 'lerden özel durumlar döndürme.

 ✔️ özel durum Oluşturucu yöntemleri kullanmayı düşünün.

 Farklı yerlerden aynı özel durumu oluşturmak yaygındır. Kod blobunun önüne geçmek için özel durumlar oluşturan ve özelliklerini başlatacak yardımcı yöntemleri kullanın.

 Ayrıca, özel durum oluşturan Üyeler satır içine alınır. Throw deyiminizi oluşturucunun içinde taşımak üyenin satır içine eklenmesine izin verebilir.

 ❌ özel durum filtresi bloklarından özel durumlar oluşturmaz.

 Özel durum filtresi bir özel durum harekete geçirirse, özel durum CLR tarafından yakalanır ve filtre false değerini döndürür. Bu davranış, yürütülen filtreden ayırt edilemez ve açıkça false döndürüyor ve bu nedenle hata ayıklama çok zor.

 ❌ finally bloklarından özel durumları açıkça oluşturmaktan kaçının. Oluşturulan çağırma yöntemlerinin sonucu olarak, örtülü olarak oluşan özel durumlar kabul edilebilir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)
