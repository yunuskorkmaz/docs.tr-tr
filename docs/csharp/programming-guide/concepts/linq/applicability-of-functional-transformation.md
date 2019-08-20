---
title: Işlevsel dönüşümün (C#) uygulanabilirliği
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: bc2678354bb45f1ed0a4076f278f52d0ee7d350e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594877"
---
# <a name="applicability-of-functional-transformation-c"></a>Işlevsel dönüşümün (C#) uygulanabilirliği
Saf işlevsel dönüşümler çok çeşitli durumlarda geçerlidir.  
  
 İşlev dönüştürme yaklaşımı, yapılandırılmış verileri sorgulamak ve işlemek için idealdir; Bu nedenle, LINQ teknolojileriyle iyi uyum vardır. Ancak işlevsel dönüşümde LINQ ile kullanmaktan çok daha geniş bir uygulanabilirlik vardır. Ana odağın bir formdan diğerine veri dönüştürmesiyle ilgili herhangi bir işlem, büyük olasılıkla işlevsel dönüşüm için aday olarak kabul edilmelidir.  
  
 Bu yaklaşım, ilk bakışta aday olarak görünmeyebilir çok sayıda sorun için geçerlidir. LINQ ile birlikte veya LINQ 'tan ayrı olarak kullanıldığında, işlevsel dönüşümde aşağıdaki alanlarda göz önünde bulundurulmalıdır:  
  
- XML tabanlı belgeler. Her XML diyalekti için iyi biçimlendirilmiş veriler, işlevsel dönüşümde kolayca değiştirilebilir. Daha fazla bilgi için bkz. [XML (C#) işlevsel dönüşümü](./functional-transformation-of-xml.md).  
  
- Diğer yapılandırılmış dosya biçimleri. Windows. ini dosyalarından düz metin belgelerine, çoğu dosya çözümleme ve dönüştürme için kendisini hedefleyen bir yapıya sahiptir.  
  
- Veri akışı protokolleri. İletişim protokollerinden verileri içine ve kod çözmede verileri kodlama, genellikle basit bir işlevsel dönüşümle temsil edilebilir.  
  
- RDBMS ve OODBMS verileri. XML gibi ilişkisel ve nesne odaklı veritabanları, yaygın olarak kullanılan yapılandırılmış veri kaynaklarıdır.  
  
- Matematik ve bilimmatik, istatistiksel ve bilimi çözümleri. Bu alanlar, kullanıcının önemsiz olmayan sorunları görselleştirirken, tahmin etmeye veya çözmeye yardımcı olmak için büyük veri kümelerini işlemeyi eğilimlidir.  
  
 [Saf işlevlerde yeniden düzenleme (C#)](./refactoring-into-pure-functions.md)bölümünde açıklandığı gibi, saf işlevleri kullanmak fonksiyonel programlamaya bir örnektir. Kendi anında avantajlarına ek olarak, saf işlevleri kullanmak işlevsel bir dönüşüm perspektifinden ilgili sorunları düşünmeye yönelik değerli deneyim sağlar. Bu yaklaşım ayrıca program ve sınıf tasarımına önemli bir etkiye sahip olabilir. Bu, özellikle bir sorun yukarıda açıklanan bir veri dönüştürme çözümüne ait olduğunda geçerlidir.  
  
 Bu öğreticinin kapsamına aşmakla birlikte, işlevsel dönüştürme perspektifinden etkilenen tasarımlar, nesnelerin aktörlere göre daha fazla işlem üzerinde ortalayarak, sonuçta elde edilen çözüm büyük ölçekli seriler olarak uygulanabilmeye eğilimlidir tek tek nesne durumu değişiklikleri yerine dönüşümler.  
  
 Bu durumda, hem C# zorunlu hem de işlevsel yaklaşımların destekleyeceğini unutmayın. bu nedenle, uygulamanız için en iyi tasarımın her ikisinin de öğeleri bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel Dönüştürmelere giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [XML (C#) işlevsel dönüştürmesi](./functional-transformation-of-xml.md)
- [Saf IŞLEVLERE yeniden düzenleme (C#)](./refactoring-into-pure-functions.md)
