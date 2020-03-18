---
title: Fonksiyonel Dönüşümün Uygulanabilirliği (C#)
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: bc2678354bb45f1ed0a4076f278f52d0ee7d350e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594877"
---
# <a name="applicability-of-functional-transformation-c"></a>Fonksiyonel Dönüşümün Uygulanabilirliği (C#)
Saf fonksiyonel dönüşümler çok çeşitli durumlarda uygulanabilir.  
  
 İşlevsel dönüşüm yaklaşımı, yapılandırılmış verileri sorgulamak ve işlemek için idealdir; bu nedenle LINQ teknolojilerine çok uygundur. Ancak, fonksiyonel dönüşüm LINQ ile kullanımdan çok daha geniş bir uygulanabilirliğe sahiptir. Ana odak bir formdan diğerine veri dönüştürme üzerinde olduğu herhangi bir süreç muhtemelen işlevsel dönüşüm için bir aday olarak kabul edilmelidir.  
  
 Bu yaklaşım, ilk bakışta aday olarak görünmeyen birçok sorun için geçerlidir. LINQ ile birlikte veya LINQ ile ayrı olarak kullanıldığında, fonksiyonel dönüşüm aşağıdaki alanlar için düşünülmelidir:  
  
- XML tabanlı belgeler. Herhangi bir XML lehçesinin iyi biçimlendirilmiş verileri işlevsel dönüşüm yoluyla kolayca işlenebilir. Daha fazla bilgi için Bkz. [XML (C#) Fonksiyonel Dönüşümü.](./functional-transformation-of-xml.md)  
  
- Diğer yapılandırılmış dosya biçimleri. Windows.ini dosyalarından düz metin belgelerine kadar, çoğu dosyanın çözümleme ve dönüştürmeye katkıda bulunan bir yapısı vardır.  
  
- Veri akışı protokolleri. Verilerin iletişim protokollerine kodlanması ve verilerin çözülmesi genellikle basit bir işlevsel dönüşümle temsil edilebilir.  
  
- RDBMS ve OODBMS verileri. İlişkisel ve nesne yönelimli veritabanları, xml gibi, yaygın olarak kullanılan yapılandırılmış veri kaynaklarıdır.  
  
- Matematik, istatistik ve bilim çözümleri. Bu alanlar, kullanıcının önemsiz olmayan sorunları görselleştirmesine, tahmin etmesine veya gerçekten çözmesine yardımcı olmak için büyük veri kümelerini işleme eğilimindedir.  
  
 [Refactoring Into Pure Functions (C#)](./refactoring-into-pure-functions.md)olarak açıklandığı gibi, saf işlevleri kullanarak işlevsel programlama bir örnektir. Onların hemen yararları ek olarak, saf işlevleri kullanarak fonksiyonel bir dönüşüm perspektifinden sorunları düşünme değerli deneyim sağlar. Bu yaklaşım aynı zamanda program ve sınıf tasarımı üzerinde büyük etkisi olabilir. Bu, özellikle bir sorun, yukarıda açıklandığı gibi bir veri dönüştürme çözümüne katkıda olduğunda doğrudur.  
  
 Bu öğreticinin kapsamı dışında olmalarına rağmen, işlevsel dönüşüm perspektifinden etkilenen tasarımlar, aktörler den çok süreçlere odaklanma eğilimindedir ve ortaya çıkan çözüm büyük ölçekli bir dizi olarak uygulanma eğilimindedir. dönüşümleri yerine tek tek nesne durumu değişiklikleri.  
  
 Yine, C#'ın hem zorunlu hem de işlevsel yaklaşımları desteklediğini unutmayın, böylece uygulamanız için en iyi tasarım her iki sinin de öğelerini içerebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf İşlevsel Dönüşümlere Giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [XML'nin Fonksiyonel Dönüşümü (C#)](./functional-transformation-of-xml.md)
- [Saf Fonksiyonlara Yeniden Düzenleme (C#)](./refactoring-into-pure-functions.md)
