---
title: DOM Ad Alanları ve DTD’ler
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 22762e3a7003d9b28a53c7b500829aaa41924c6d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710602"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>DOM Ad Alanları ve DTD’ler
Belge türü tanımları (DTD 'Ler) ad alanı desteğini karmaşıklaştırır. Örneğin, aşağıdaki XML adlarında iki nokta üst üste içeren varsayılan öznitelikleri içerir.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Bu yapı için izin veriliyorsa aşağıdakiler olası çözümlerdir:  
  
- `x:` bir ad alanı öneki olarak değerlendirilir, ancak bu ön ek bir `xmlns:x` ad alanı bildirimi kullanılarak çözümlenebilmelidir ve bu da DTD 'de bir yerde bulunmalıdır. Bu öneki örnek belgesinde farklı bir şeye eşlemek hatadır.  
  
- `x:`, bir ad alanı öneki olarak değerlendirilir, ancak bu ön ek, örnek öğelerinin bağlamında her zaman çözümlenir. Bu, önek aslında `item` öğesinin göründüğü ad alanı kapsamına bağlı olarak farklı ad alanı Tekdüzen Kaynak tanımlayıcılarına (URI) eşleyebileceğiniz anlamına gelir. Bu davranış, önceki madde işaretinde verilen çözünürlükten daha öngörülebilir hale gelir, ancak varsayılan özniteliklerin gerçekleştirilmiş olması gerektiğinden diğer karmaşık kollar vardır.  
  
- İki nokta üst üste, bir DTD 'de olduğundan ve özniteliğin adı `x:y`, ön ek ve ad alanı URI 'SI olmadığından yok sayılır.  
  
- Varsayılan öznitelikteki iki nokta üst üste, bir DTD içindeki adlarda iki nokta üst üsteyle desteklenmediğini söyleyen bir özel durum oluşturur. Bu, öngörülebilir bir davranışa neden olur, ancak World Wide Web Konsorsiyumu (W3C) yayımlanmış DTD 'lerin çoğunu yükleyemeyeceğiniz anlamına gelir.  
  
- Kullanıcı DTD doğrulaması istediğinde, tüm belge için ad alanı desteği kapalıdır. Bu, W3C DTD 'Leri yüklemek ve tahmin edilebilir bir davranışa neden olabilir.  
  
 Microsoft .NET çerçevesindeki XML, en yüksek W3C uyumluluğu için ikinci seçeneği uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
