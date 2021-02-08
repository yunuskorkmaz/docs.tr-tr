---
description: "Daha fazla bilgi edinin: DOM 'da ad alanları ve DTD 'Ler"
title: DOM Ad Alanları ve DTD’ler
ms.date: 03/30/2017
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 4445c1a33cca50707940758f812995c6b1db64cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775935"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>DOM Ad Alanları ve DTD’ler

Belge türü tanımları (DTD 'Ler) ad alanı desteğini karmaşıklaştırır. Örneğin, aşağıdaki XML adlarında iki nokta üst üste içeren varsayılan öznitelikleri içerir.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Bu yapı için izin veriliyorsa aşağıdakiler olası çözümlerdir:  
  
- , `x:` Bir ad alanı öneki olarak değerlendirilir, ancak bu ön ek bir `xmlns:x` ad alanı bildirimi kullanılarak çözümlenebilmelidir, bu da DTD 'de bir yerde bulunmalıdır. Bu öneki örnek belgesinde farklı bir şeye eşlemek hatadır.  
  
- , `x:` Bir ad alanı öneki olarak değerlendirilir, ancak bu ön ek, örnek öğelerinin bağlamında her zaman çözümlenir. Bu, önekinin, öğenin göründüğü ad alanı kapsamına bağlı olarak, aslında farklı ad alanı Tekdüzen Kaynak tanımlayıcılarına (URI 'Ler) eşleme olabileceği anlamına gelir `item` . Bu davranış, önceki madde işaretinde verilen çözünürlükten daha öngörülebilir hale gelir, ancak varsayılan özniteliklerin gerçekleştirilmiş olması gerektiğinden diğer karmaşık kollar vardır.  
  
- İki nokta üst üste, bir DTD 'de olduğundan ve özniteliğin adı `x:y` , ön ek ve ad alanı URI 'si olmadığından yok sayılır.  
  
- Varsayılan öznitelikteki iki nokta üst üste, bir DTD içindeki adlarda iki nokta üst üsteyle desteklenmediğini söyleyen bir özel durum oluşturur. Bu, öngörülebilir bir davranışa neden olur, ancak World Wide Web Konsorsiyumu (W3C) yayımlanmış DTD 'lerin çoğunu yükleyemeyeceğiniz anlamına gelir.  
  
- Kullanıcı DTD doğrulaması istediğinde, tüm belge için ad alanı desteği kapalıdır. Bu, W3C DTD 'Leri yüklemek ve tahmin edilebilir bir davranışa neden olabilir.  
  
 Microsoft .NET çerçevesindeki XML, en yüksek W3C uyumluluğu için ikinci seçeneği uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
