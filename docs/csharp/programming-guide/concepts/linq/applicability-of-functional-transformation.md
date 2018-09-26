---
title: (C#) işlev dönüşümün uygulanabilirliği
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: baa3866c8c2c148a3080522d7c02e28e9d0fd945
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231539"
---
# <a name="applicability-of-functional-transformation-c"></a>(C#) işlev dönüşümün uygulanabilirliği
Saf işlevsel dönüşümlere çok çeşitli durumlarda geçerlidir.  
  
 İşlevsel dönüşüm yaklaşım, ideal olarak sorgulama ve düzenleme yapılandırılmış veriler için uygundur; Bu nedenle de LINQ teknolojileriyle uyar. Ancak LINQ ile kullanmak daha çok geniş bir Uygulanabilirlik işlevsel dönüşümü yoktur. Verileri bir biçimden diğerine dönüştürme üzerinde odaklandığı olduğu herhangi bir işlem büyük olasılıkla işlevsel dönüşüm adayı olarak kabul edilmelidir.  
  
 Bu yaklaşım, ilk bakışta bir aday olarak görünmeyebilir karşılaşılan birçok sorun için geçerlidir. Birlikte veya ayrı olarak LINQ birlikte kullanıldığında, işlevsel dönüşümü için aşağıdaki alanları bulundurulmalıdır:  
  
-   XML-tabanlı belge. Tüm XML diyalekti doğru biçimlendirilmiş verilerin işlevsel dönüşüm kolayca işlenebilir. Daha fazla bilgi için [işlevsel XML Dönüşümü (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Diğer yapılandırılmış dosya biçimleri. Düz metin belgelere Windows.ini dosyalarından çoğu dosya kendisini çözümleme ve dönüştürme için uygundur bazı yapıdadır.  
  
-   Veri akış protokolleri. Veri kodlama ve kod çözme verilerden iletişim protokolleri genellikle basit bir işlev dönüştürme işlemi tarafından temsil edilebilir.  
  
-   RDBMS ve OODBMS verileri. İlişkisel ve nesne yönelimli veritabanları, XML, olduğu gibi yaygın olarak kullanılan yapılandırılmış veri kaynağıdır.  
  
-   Matematik istatistik ve Bilim çözümler. Bu alanlar, kullanıcının görselleştirme, tahmin etme veya gerçekten Önemsiz sorunları çözmeye yardımcı olmak için büyük veri kümelerini işleme eğilimindedir.  
  
 Bölümünde anlatıldığı gibi [saf işlevler halinde yeniden düzenleme (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), saf işlevler kullanarak, işlevsel programlama örneği verilmiştir. Ek anında faydaları için saf işlevler kullanarak işlevsel dönüşüm açısından sorunlar hakkında düşünmeye değerli deneyimi sağlar. Bu yaklaşım, ayrıca program ve sınıf tasarımı üzerinde önemli bir etkisi olabilir. Bu, özellikle kendi yukarıda açıklandığı gibi bir veri dönüştürme çözüme uygundur bir sorun olduğunda geçerlidir.  
  
 Bunlar bu Eğitimin kapsamı dışında olsa da, işlevsel dönüşüm perspektife göre etkileyen tasarımları üzerinde işlemler birden fazla aktör olarak nesnelerde merkezi eğilimindedir ve ortaya çıkan çözüm, büyük ölçekli dizi olarak uygulanması eğilimindedir değişiklikler tek tek bir nesne yerine dönüşümleri belirtin.  
  
 Yeniden uygulamanız için en iyi tasarım öğelerinin her ikisi de bir araya getirebilir için C# hem zorunlu hem de işlevsel yaklaşım desteklediğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Giriş saf işlevsel dönüşümlere (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [(C#) XML işlevsel dönüşümü](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
- [Saf işlevler halinde (C#) yeniden düzenleme](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
