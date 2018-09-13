---
title: Ad alanları ve DTD'ler DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708276"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Ad alanları ve DTD'ler DOM
Belge türü tanımları (DTD'ler) complicate ad alanı desteği. Örneğin, aşağıdaki XML, iki nokta üst üste adlarında içeren varsayılan öznitelikler içeriyor.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Tento konstruktor je izin verilip verilmediğini olası çözümlemeler aşağıda belirtilmiştir:  
  
-   `x:` Çözümlenebilir kullanarak bir ad alanı öneki, ancak bu öneki olmalıdır olarak kabul edilir bir `xmlns:x` ad alanı bildirimi, ayrıca DTD'nin yere bulunmalıdır. Bu örnek belgeye farklı bir şey bu ön ek eşlemek için bir hatadır.  
  
-   `x:` Bir ad alanı öneki kabul edilir, ancak bu ön eki her zaman örneği öğeleri bağlamında çözümlenir. Önek gerçekten eşleme farklı bir ad alanı Tekdüzen Kaynak Tanımlayıcıları (URI'lar) ad alanı kapsamında bağlı olarak başka bir deyişle `item` öğe görüntülenir. Bu davranış önceki maddede verilen çözümleme daha öngörülebilir olmakla birlikte, varsayılan öznitelikler gerçekleştirilmiş gerektirdiğinden, diğer karmaşık ayrımlar sahip.  
  
-   İki nokta üst üste bir DTD'nin içinde olduğundan ve öznitelik adı olduğundan göz ardı edilir `x:y`, önek ve ad alanı URI.  
  
-   İki nokta üst üste varsayılan özniteliğinde, iki nokta üst üste bir DTD'nin içinde adlarının desteklenmediğine belirten, özel durum oluşturur. Bu tahmin edilebilir bir davranışa neden olur, ancak DTD'ler çok World Wide Web Consortium (W3C) yüklenemiyor anlamına gelir yayımlanmış.  
  
-   Kullanıcı DTD'nin doğrulama istediğinde, ad alanı desteği için belgenin tamamını kapalıdır. W3C DTD'ler ve sonuçları tahmin edilebilir davranış yüklemek mümkün kılar.  
  
 Microsoft .NET Framework XML W3C en büyük uyumluluk için ikinci seçeneği uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
