---
title: "Alan tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dc3249518dd1e1c751de08c22d1c5eb4fa28dc6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="field-design"></a>Alan tasarım
Saklama ilkesini en önemli kavramları nesne odaklı tasarım biridir. Bu ilke, bir nesne içinde depolanan veriler yalnızca o nesneyi erişilebilir olması gerektiğini belirtir.  
  
 Böylece türü üyeleri için kod dışında bozmadan alanları türü (adı veya türü değişiklikleri) yapılan değişiklikler yapılabilir bir türü tasarlanmalıdır söylemek için ilkesini yorumlamak için kullanışlı bir yol olduğu. Bu yorum hemen tüm alanları özel anlamına gelir.  
  
 Bu tür alanları neredeyse tanımı tarafından hiçbir zaman değiştirmek için gerekli olduğundan Biz bu katı sınırlama listesinden sabit ve statik salt okunur alanları hariç tutun.  
  
 **X yok** genel veya korumalı örneği alanları sağlar.  
  
 Genel veya korumalı yapmak yerine alanları erişmek için özellikler sağlamalıdır.  
  
 **✓ YAPMAK** için hiçbir zaman değiştirecek sabitleri sabit alanları kullanın.  
  
 Derleyici, doğrudan kod çağırma içine const alanlarına ait değerlerin yakar. Bu nedenle, sabit değerler hiçbir zaman uyumluluk çiğnemekten riski değiştirilebilir.  
  
 **✓ YAPMAK** ortak statik kullanmak `readonly` alanları önceden tanımlanmış nesne örnekleri için.  
  
 Önceden tanımlanmış türünün örneklerini varsa, bunları genel olarak salt okunur statik alanları türü bildirin.  
  
 **X yok** değişebilir türlerin örnekleri atamak `readonly` alanları.  
  
 Bir örneği sonra değiştirilebilen örnekleri türüyle bir değişebilir türüdür. Örneğin, dizileri, birçok koleksiyonun ve akışlar değişebilir türleridir ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, ve <xref:System.String?displayProperty=nameWithType> tüm sabittir. Bir başvuru türü alanı üzerinde salt okunur değiştiricisi değiştirilmekte olan gelen alanda depolanan örneği engeller, ancak alanın örnek veri örneğini değiştirme arama üyeleri tarafından değiştirilmiş engellemez.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye tasarım yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)
