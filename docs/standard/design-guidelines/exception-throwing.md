---
title: Özel Durum Oluşturma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709406"
---
# <a name="exception-throwing"></a>Özel Durum Oluşturma
Özel durum-bu bölümde açıklanan oluşturma yönergeleri, yürütme hatası anlamı için iyi bir tanım gerektirir. Yürütme hatası, bir üye için tasarlandıkları şeyi (üye adının ne kadar gösterdiği) yapamayacağı zaman oluşur. Örneğin, `OpenFile` yöntemi çağırana bir açık dosya tutamacı döndüremez, bir yürütme hatası olarak kabul edilir.  
  
 Çoğu geliştirici, sıfıra bölme veya null başvurular gibi kullanım hataları için özel durumları kullanma konusunda rahat hale gelmiştir. Çerçevede, yürütme hataları da dahil olmak üzere tüm hata koşulları için özel durumlar kullanılır.  
  
 **X DO NOT** hata kodlarını döndürür.  
  
 Özel durumlar, çerçeveler içindeki hataların bildirilme yöntemidir.  
  
 **✓ DO** rapor yürütme hataları özel durumları atma.  
  
 **✓ CONSIDER** çağırarak işlem sonlandırılıyor `System.Environment.FailFast` (.NET Framework 2.0 özelliği) kodunuzu daha fazla yürütme için güvenli olduğu bir durumla karşılaşırsa yerine bir özel durum atma.  
  
 **X DO NOT** özel durumlar için normal akışı denetimi, mümkünse kullanın.  
  
 Olası yarış koşullarına sahip sistem arızaları ve işlemler haricinde, çerçeve tasarımcıları, kullanıcıların özel durum oluşturmayan kodlar yazabilmesi için API 'Ler tasarlaması gerekir. Örneğin, kullanıcılar özel durum oluşturmayan bir kod yazabilmesi için bir üyeyi çağırmadan önce önkoşulları denetlemek için bir yol sağlayabilirsiniz.  
  
 Başka bir üyenin ön koşulları 'nı denetlemek için kullanılan üye, genellikle test edici olarak adlandırılır ve işi gerçekten yapan üyeye bir doer denir.  
  
 Sınayıcı-doer deseninin kabul edilemez bir performans yükü olabilir. Bu gibi durumlarda, bu şekilde adlandırılan TRY-Parse deseninin göz önünde bulundurulmaları gerekir (daha fazla bilgi için bkz. [özel durumlar ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) ).  
  
 **✓ CONSIDER** özel durumları atma performans etkileri. Saniyede 100 ' den yüksek olan throw ücretleri, çoğu uygulamanın performansını önemli ölçüde etkileyebilir.  
  
 **✓ DO** belge herkese açık şekilde çağrılabilir üyeleri tarafından bir üye ihlali nedeniyle oluşturulan tüm özel durumları Sözleşme (bir sistem hatası yerine) ve bunları sizin sözleşmesinin bir parçası davran.  
  
 Sözleşmenin bir parçası olan özel durumlar bir sürümden sonrakine değişmemelidir (yani, özel durum türü değişmemelidir ve yeni özel durumlar eklenmemelidir).  
  
 **X DO NOT** olması ya da throw veya yok edebilir Genel üyeler temel bazı seçeneği.  
  
 **X DO NOT** dönüş değeri olarak özel durumları döndüren Genel üyeler olması veya bir `out` parametresi.  
  
 Özel durum tabanlı hata raporlama avantajlarının çoğunu yapmak yerine ortak API 'lerden özel durumlar döndürme.  
  
 **✓ CONSIDER** özel Oluşturucu yöntemleri kullanarak.  
  
 Farklı yerlerden aynı özel durumu oluşturmak yaygındır. Kod blobunun önüne geçmek için özel durumlar oluşturan ve özelliklerini başlatacak yardımcı yöntemleri kullanın.  
  
 Ayrıca, özel durum oluşturan Üyeler satır içine alınır. Throw deyiminizi oluşturucunun içinde taşımak üyenin satır içine eklenmesine izin verebilir.  
  
 **X DO NOT** özel durum filtresi taşlarından özel durumlar oluşturma.  
  
 Özel durum filtresi bir özel durum harekete geçirirse, özel durum CLR tarafından yakalanır ve filtre false değerini döndürür. Bu davranış, yürütülen filtreden ayırt edilemez ve açıkça false döndürüyor ve bu nedenle hata ayıklama çok zor.  
  
 **X AVOID** açıkça finally blokları özel durumları atma. Oluşturulan çağırma yöntemlerinin sonucu olarak, örtülü olarak oluşan özel durumlar kabul edilebilir.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)
