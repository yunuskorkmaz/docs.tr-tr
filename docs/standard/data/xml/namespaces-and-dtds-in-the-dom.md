---
title: "Ad alanları ve DOM DTD'leri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87a03883622ba63a8d999907305356905b36bf1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Ad alanları ve DOM DTD'leri
Belge türü tanımları (DTD) complicate ad alanı desteği. Örneğin, aşağıdaki XML adlarında iki nokta üst üste içeren varsayılan öznitelikleri içerir.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Bu yapıyı izin verilip verilmediğini olası çözümlemeler aşağıda belirtilmiştir:  
  
-   `x:` Çözümlenebilir kullanarak bir ad alanı öneki, ancak bu öneki olmalıdır olarak kabul edilir bir `xmlns:x` ayrıca DTD içinde herhangi bir yerde bulunmalıdır ad alanı bildirimi. Bu örnek belgeye farklı bir şey bu öneki eşlemek için bir hatadır.  
  
-   `x:` Bir ad alanı öneki kabul edilir, ancak bu öneki örneği öğeleri bağlamında her zaman çözümlenir. Bu öneki gerçekte ad alanı kapsamında bağlı olarak farklı ad Tekdüzen Kaynak Tanımlayıcıları (URI'ler) için eşleme anlamına gelir `item` öğesi görünür. Bu davranış önceki maddede verilen çözümleme'den daha tahmin edilebilir, ancak varsayılan öznitelikler gerçekleştirilip gerektirdiğinden diğer karmaşık ayrımlar sahiptir.  
  
-   İki nokta üst üste DTD içinde olduğundan ve öznitelik adı yoksayıldı `x:y`, önek ve hiçbir ad alanı URI'si.  
  
-   İki nokta üst üste varsayılan özniteliğinde DTD içinde adlarında iki nokta üst üste desteklenmez söyleyen bir özel durum oluşturur. Bu tahmin edilebilir bir davranış olur, ancak birçok World Wide Web Konsorsiyumu (W3C) yüklenemiyor anlamına gelir DTD'leri yayımlanan.  
  
-   Kullanıcı DTD doğrulama istediğinde, tüm belgeyi ad alanı desteğini devre dışı bırakılır. W3C DTD'leri ve tahmin edilebilir bir davranış sonuçlarında yüklemek mümkün kılar.  
  
 Microsoft .NET Framework XML'de maksimum W3C uyumluluk için ikinci seçeneği uygular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
