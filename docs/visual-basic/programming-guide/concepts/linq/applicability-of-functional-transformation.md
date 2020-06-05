---
title: İşlev Dönüşümün Uygulanabilirliği
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: db24871e3763c5acc79cf21b4afb90a93ed8bd53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383708"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>Işlevsel dönüşümün uygulanabilirliği (Visual Basic)
Saf işlevsel dönüşümler çok çeşitli durumlarda geçerlidir.  
  
 İşlev dönüştürme yaklaşımı, yapılandırılmış verileri sorgulamak ve işlemek için idealdir; Bu nedenle, LINQ teknolojileriyle iyi uyum vardır. Ancak işlevsel dönüşümde LINQ ile kullanmaktan çok daha geniş bir uygulanabilirlik vardır. Ana odağın bir formdan diğerine veri dönüştürmesiyle ilgili herhangi bir işlem, büyük olasılıkla işlevsel dönüşüm için aday olarak kabul edilmelidir.  
  
 Bu yaklaşım, ilk bakışta aday olarak görünmeyebilir çok sayıda sorun için geçerlidir. LINQ ile birlikte veya LINQ 'tan ayrı olarak kullanıldığında, işlevsel dönüşümde aşağıdaki alanlarda göz önünde bulundurulmalıdır:  
  
- XML tabanlı belgeler. Her XML diyalekti için iyi biçimlendirilmiş veriler, işlevsel dönüşümde kolayca değiştirilebilir. Daha fazla bilgi için bkz. [XML 'In Işlevsel dönüşümü (Visual Basic)](functional-transformation-of-xml.md).  
  
- Diğer yapılandırılmış dosya biçimleri. Windows. ini dosyalarından düz metin belgelerine, çoğu dosya çözümleme ve dönüştürme için kendisini hedefleyen bir yapıya sahiptir.  
  
- Veri akışı protokolleri. İletişim protokollerinden verileri içine ve kod çözmede verileri kodlama, genellikle basit bir işlevsel dönüşümle temsil edilebilir.  
  
- RDBMS ve OODBMS verileri. XML gibi ilişkisel ve nesne odaklı veritabanları, yaygın olarak kullanılan yapılandırılmış veri kaynaklarıdır.  
  
- Matematik ve bilimmatik, istatistiksel ve bilimi çözümleri. Bu alanlar, kullanıcının önemsiz olmayan sorunları görselleştirirken, tahmin etmeye veya çözmeye yardımcı olmak için büyük veri kümelerini işlemeyi eğilimlidir.  
  
 [Saf işlevlerde yeniden düzenleme (Visual Basic)](refactoring-into-pure-functions.md)bölümünde açıklandığı gibi, saf işlevleri kullanmak fonksiyonel programlamaya bir örnektir. Kendi anında avantajlarına ek olarak, saf işlevleri kullanmak işlevsel bir dönüşüm perspektifinden ilgili sorunları düşünmeye yönelik değerli deneyim sağlar. Bu yaklaşım ayrıca program ve sınıf tasarımına önemli bir etkiye sahip olabilir. Bu, özellikle bir sorun yukarıda açıklanan bir veri dönüştürme çözümüne ait olduğunda geçerlidir.  
  
 Bu öğreticinin kapsamına aşmakla birlikte, işlevsel dönüştürme perspektifinden etkilenen tasarımlar, nesnelerin aktörlere göre daha fazla işlem üzerinde ortalayarak, sonuçta elde edilen çözüm ayrı nesne durumu değişiklikleri yerine büyük ölçekli dönüşümler dizisi olarak uygulanabilmektedir.  
  
 Visual Basic, hem zorunlu hem de işlevsel yaklaşımların destekleyeceğini unutmayın. bu nedenle, uygulamanız için en iyi tasarımın her ikisinin de öğeleri bulunabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [XML işlevsel dönüştürmesi (Visual Basic)](functional-transformation-of-xml.md)
- [Saf IŞLEVLERE yeniden düzenleme (Visual Basic)](refactoring-into-pure-functions.md)
