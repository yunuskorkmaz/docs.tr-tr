---
title: "Uygulanabilirlik işlev dönüştürme (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7196e128a6d61b2b28e955a79561db2b9a5e51b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="applicability-of-functional-transformation-c"></a>Uygulanabilirlik işlev dönüştürme (C#)
Saf işlevsel dönüşümleri çok çeşitli durumlarda uygulanabilir.  
  
 İşlev dönüştürme yaklaşım, ideal olarak sorgulama ve yapılandırılmış veri işleme için uygundur; Bu nedenle de LINQ teknolojileriyle sığar. Ancak, işlev dönüştürme LINQ ile kullanmak üzere daha çok daha geniş bir Uygulanabilirlik vardır. Verileri bir biçimden diğerine dönüştürme ana odak olduğu herhangi bir işlem büyük olasılıkla işlev dönüştürme adayı olarak düşünülmelidir.  
  
 Bu yaklaşım bir aday olarak ilk bakışta görünmeyebilir birçok sorunu için geçerli olur. İle birlikte veya ayrı ayrı LINQ gelen kullanıldığında, işlev dönüştürme için aşağıdaki alanlarda bulundurulmalıdır:  
  
-   XML tabanlı belgeler. Doğru biçimlendirilmiş XML dialect verileri kolayca işlevsel dönüştürme yönetilebilir. Daha fazla bilgi için bkz: [işlev dönüştürme XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Diğer yapılandırılmış dosya biçimleri. Düz metin belgelere Windows.ini dosyalarından çoğu dosyaları kendisini çözümleme ve dönüştürme için uygundur bazı yapıya sahip.  
  
-   Veri akış protokolleri. İçine veri kodlama ve kod çözme verilerini iletişim protokolleri genellikle basit işlevsel bir dönüşüm tarafından temsil edilebilir.  
  
-   RDBMS ve OODBMS verileri. İlişkisel ve nesne yönelimli veritabanları, XML gibi yaygın olarak kullanılan yapılandırılmış veri kaynaklarıdır.  
  
-   Mathematic, istatistik ve Bilim çözümleri. Kullanıcı görselleştirme, tahmin veya gerçekten Önemsiz olmayan sorunları çözmeye yardımcı olmak üzere büyük veri kümeleri işlemek için bu alanlar eğilimlidir.  
  
 Bölümünde açıklandığı gibi [saf işlevler halinde yeniden düzenlemesi (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), saf işlevler kullanılarak işlevsel programlama örneği verilmiştir. Hemen faydaları ek saf işlevler kullanılarak değerli bir işlev dönüştürme açısından sorunlar hakkında düşünmeye deneyimi sağlar. Bu yaklaşım da program ve sınıf tasarımı hakkında önemli etkisi olabilir. Bir sorun kendisini yukarıda açıklandığı gibi bir veri dönüştürme çözüme uygundur durumlarda özellikle geçerlidir.  
  
 Bu öğretici kapsamında olmasına rağmen işlev dönüştürme perspektife göre etkilenir tasarımları nesneleri aktörler olarak birden fazla işlemlerde merkezi eğilimindedir ve sonuçta elde edilen çözüm büyük ölçekli dizi olarak uygulanması eğilimindedir Dönüşümleri yerine tek tek nesne durum değişiklikleri.  
  
 Yeniden, uygulamanız için en iyi tasarım öğeleri her ikisi de dahil C# kesinlik temelli ve işlevsel yaklaşımlar destekler, böylece olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [İşlev dönüştürme XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [Saf işlevlerini (C#) yeniden düzenleme](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
