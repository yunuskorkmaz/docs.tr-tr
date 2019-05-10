---
title: (Visual Basic) işlev dönüşümün uygulanabilirliği
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: 1903a59ec666c7d0b4c585abe5424cc1a0fd902d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642412"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>(Visual Basic) işlev dönüşümün uygulanabilirliği
Saf işlevsel dönüşümlere çok çeşitli durumlarda geçerlidir.  
  
 İşlevsel dönüşüm yaklaşım, ideal olarak sorgulama ve düzenleme yapılandırılmış veriler için uygundur; Bu nedenle de LINQ teknolojileriyle uyar. Ancak LINQ ile kullanmak daha çok geniş bir Uygulanabilirlik işlevsel dönüşümü yoktur. Verileri bir biçimden diğerine dönüştürme üzerinde odaklandığı olduğu herhangi bir işlem büyük olasılıkla işlevsel dönüşüm adayı olarak kabul edilmelidir.  
  
 Bu yaklaşım, ilk bakışta bir aday olarak görünmeyebilir karşılaşılan birçok sorun için geçerlidir. Birlikte veya ayrı olarak LINQ birlikte kullanıldığında, işlevsel dönüşümü için aşağıdaki alanları bulundurulmalıdır:  
  
- XML-tabanlı belge. Tüm XML diyalekti doğru biçimlendirilmiş verilerin işlevsel dönüşüm kolayca işlenebilir. Daha fazla bilgi için [işlevsel XML Dönüşümü (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
- Diğer yapılandırılmış dosya biçimleri. Düz metin belgelere Windows.ini dosyalarından çoğu dosya kendisini çözümleme ve dönüştürme için uygundur bazı yapıdadır.  
  
- Veri akış protokolleri. Veri kodlama ve kod çözme verilerden iletişim protokolleri genellikle basit bir işlev dönüştürme işlemi tarafından temsil edilebilir.  
  
- RDBMS ve OODBMS verileri. İlişkisel ve nesne yönelimli veritabanları, XML, olduğu gibi yaygın olarak kullanılan yapılandırılmış veri kaynağıdır.  
  
- Matematik istatistik ve Bilim çözümler. Bu alanlar, kullanıcının görselleştirme, tahmin etme veya gerçekten Önemsiz sorunları çözmeye yardımcı olmak için büyük veri kümelerini işleme eğilimindedir.  
  
 Bölümünde anlatıldığı gibi [yeniden düzenleme içine saf işlevleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), saf işlevler kullanarak, işlevsel programlama örneği verilmiştir. Ek anında faydaları için saf işlevler kullanarak işlevsel dönüşüm açısından sorunlar hakkında düşünmeye değerli deneyimi sağlar. Bu yaklaşım, ayrıca program ve sınıf tasarımı üzerinde önemli bir etkisi olabilir. Bu, özellikle kendi yukarıda açıklandığı gibi bir veri dönüştürme çözüme uygundur bir sorun olduğunda geçerlidir.  
  
 Bunlar bu Eğitimin kapsamı dışında olsa da, işlevsel dönüşüm perspektife göre etkileyen tasarımları üzerinde işlemler birden fazla aktör olarak nesnelerde merkezi eğilimindedir ve ortaya çıkan çözüm, büyük ölçekli dizi olarak uygulanması eğilimindedir değişiklikler tek tek bir nesne yerine dönüşümleri belirtin.  
  
 Yeniden uygulamanız için en iyi tasarım öğelerinin her ikisi de bir araya getirebilir için Visual Basic hem zorunlu hem de işlevsel yaklaşım desteklediğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere (Visual Basic) giriş](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [(Visual Basic) XML işlevsel dönüşümü](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)
- [(Visual Basic) saf işlevler halinde yeniden düzenleme](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
