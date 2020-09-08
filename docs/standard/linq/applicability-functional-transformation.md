---
title: İşlevsel dönüştürme uygulanabilirliği-LINQ to XML
description: İşlevsel dönüştürmeleri ne zaman kullanabileceğinizi öğrenin.
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: cfba2a32887891cd4b735c76e940ff2400e55bef
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553550"
---
# <a name="applicability-of-functional-transformation-linq-to-xml"></a>İşlevsel dönüşümün uygulanabilirliği (LINQ to XML)

Saf işlevsel dönüşümler çok çeşitli durumlarda geçerlidir.

İşlev dönüştürme yaklaşımı, yapılandırılmış verileri sorgulamak ve işlemek için idealdir; Bu nedenle, LINQ teknolojileriyle iyi uyum vardır. Ancak işlevsel dönüşümde LINQ ile kullanmaktan çok daha geniş bir uygulanabilirlik vardır. Ana odağın bir formdan diğerine veri dönüştürmesiyle ilgili herhangi bir işlem, büyük olasılıkla işlevsel dönüşüm için aday olarak kabul edilmelidir.

Bu yaklaşım, ilk bakışta aday olarak görünmeyebilir çok sayıda sorun için geçerlidir. LINQ ile birlikte veya LINQ 'tan ayrı olarak kullanıldığında, işlevsel dönüşümde aşağıdaki alanlarda göz önünde bulundurulmalıdır:

- XML tabanlı belgeler. Her XML diyalekti için iyi biçimlendirilmiş veriler, işlevsel dönüşümde kolayca değiştirilebilir. Daha fazla bilgi için bkz. [XML 'In işlevsel dönüşümü](functional-transformation-xml.md).
- Diğer yapılandırılmış dosya biçimleri. Windows.ini dosyalarından düz metin belgelerine, çoğu dosya çözümleme ve dönüştürme için kendisini hedefleyen bir yapıya sahiptir.
- Veri akışı protokolleri. İletişim protokollerinden verileri içine ve kod çözmede verileri kodlama, genellikle basit bir işlevsel dönüşümle temsil edilebilir.
- RDBMS ve OODBMS verileri. XML gibi ilişkisel ve nesne odaklı veritabanları, yaygın olarak kullanılan yapılandırılmış veri kaynaklarıdır.
- Matematik ve bilimmatik, istatistiksel ve bilimi çözümleri. Bu alanlar, kullanıcının önemsiz olmayan sorunları görselleştirirken, tahmin etmeye veya çözmeye yardımcı olmak için büyük veri kümelerini işlemeyi eğilimlidir.

[Saf işlevlerde yeniden düzenleme](refactor-pure-functions.md)bölümünde açıklandığı gibi, saf işlevleri kullanmak fonksiyonel programlamaya bir örnektir. Kendi anında avantajlarına ek olarak, saf işlevleri kullanmak işlevsel bir dönüşüm perspektifinden ilgili sorunları düşünmeye yönelik değerli deneyim sağlar. Bu yaklaşım ayrıca program ve sınıf tasarımına önemli bir etkiye sahip olabilir. Bu, özellikle bir sorun yukarıda açıklanan bir veri dönüştürme çözümüne ait olduğunda geçerlidir.

Bu öğreticinin kapsamına aşmakla karşılaşmakla birlikte, işlevsel dönüştürme perspektifinden etkilenen tasarımlar, nesnelerin aktörlere göre daha fazla işlem üzerinde ortalayarak, sonuçta elde edilen çözüm ayrı nesne durumu değişiklikleri yerine bir dizi büyük ölçekli dönüşümlerle birlikte uygulanmasına eğilimlidir.

 Daha sonra, C# ve Visual Basic hem zorunlu hem de işlevsel yaklaşımlar desteklediğinizden, uygulamanız için en iyi tasarımın her ikisinin de öğeleri birleştirebileceğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md)
- [XML işlevsel dönüştürmesi](functional-transformation-xml.md)
- [Saf işlevlerde yeniden düzenleme](refactor-pure-functions.md)
