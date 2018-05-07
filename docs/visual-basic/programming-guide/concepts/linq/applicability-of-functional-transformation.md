---
title: Uygulanabilirlik işlev dönüştürme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: bdb487ce0de986a1dba36908352a8270cfde2700
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>Uygulanabilirlik işlev dönüştürme (Visual Basic)
Saf işlevsel dönüşümleri çok çeşitli durumlarda uygulanabilir.  
  
 İşlev dönüştürme yaklaşım, ideal olarak sorgulama ve yapılandırılmış veri işleme için uygundur; Bu nedenle de LINQ teknolojileriyle sığar. Ancak, işlev dönüştürme LINQ ile kullanmak üzere daha çok daha geniş bir Uygulanabilirlik vardır. Verileri bir biçimden diğerine dönüştürme ana odak olduğu herhangi bir işlem büyük olasılıkla işlev dönüştürme adayı olarak düşünülmelidir.  
  
 Bu yaklaşım bir aday olarak ilk bakışta görünmeyebilir birçok sorunu için geçerli olur. İle birlikte veya ayrı ayrı LINQ gelen kullanıldığında, işlev dönüştürme için aşağıdaki alanlarda bulundurulmalıdır:  
  
-   XML tabanlı belgeler. Doğru biçimlendirilmiş XML dialect verileri kolayca işlevsel dönüştürme yönetilebilir. Daha fazla bilgi için bkz: [işlev dönüştürme XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Diğer yapılandırılmış dosya biçimleri. Düz metin belgelere Windows.ini dosyalarından çoğu dosyaları kendisini çözümleme ve dönüştürme için uygundur bazı yapıya sahip.  
  
-   Veri akış protokolleri. İçine veri kodlama ve kod çözme verilerini iletişim protokolleri genellikle basit işlevsel bir dönüşüm tarafından temsil edilebilir.  
  
-   RDBMS ve OODBMS verileri. İlişkisel ve nesne yönelimli veritabanları, XML gibi yaygın olarak kullanılan yapılandırılmış veri kaynaklarıdır.  
  
-   Mathematic, istatistik ve Bilim çözümleri. Kullanıcı görselleştirme, tahmin veya gerçekten Önemsiz olmayan sorunları çözmeye yardımcı olmak üzere büyük veri kümeleri işlemek için bu alanlar eğilimlidir.  
  
 Bölümünde açıklandığı gibi [yeniden düzenleme içine saf işlevleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), saf işlevler kullanılarak işlevsel programlama örneği verilmiştir. Hemen faydaları ek saf işlevler kullanılarak değerli bir işlev dönüştürme açısından sorunlar hakkında düşünmeye deneyimi sağlar. Bu yaklaşım da program ve sınıf tasarımı hakkında önemli etkisi olabilir. Bir sorun kendisini yukarıda açıklandığı gibi bir veri dönüştürme çözüme uygundur durumlarda özellikle geçerlidir.  
  
 Bu öğretici kapsamında olmasına rağmen işlev dönüştürme perspektife göre etkilenir tasarımları nesneleri aktörler olarak birden fazla işlemlerde merkezi eğilimindedir ve sonuçta elde edilen çözüm büyük ölçekli dizi olarak uygulanması eğilimindedir Dönüşümleri yerine tek tek nesne durum değişiklikleri.  
  
 Yeniden, uygulamanız için en iyi tasarım öğeleri her ikisi de dahil şekilde Visual Basic kesinlik temelli ve işlevsel yaklaşımlar desteklediğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [İşlev dönüştürme XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [Saf işlevleri (Visual Basic) yeniden düzenleme](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
