---
title: Alan tasarım
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d47934c3fed17f75a97ef5da0397c6ceba53d68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571124"
---
# <a name="field-design"></a>Alan tasarım
Saklama ilkesini en önemli kavramları nesne odaklı tasarım biridir. Bu ilke, bir nesne içinde depolanan veriler yalnızca o nesneyi erişilebilir olması gerektiğini belirtir.  
  
 Böylece türü üyeleri için kod dışında bozmadan alanları türü (adı veya türü değişiklikleri) yapılan değişiklikler yapılabilir bir türü tasarlanmalıdır söylemek için ilkesini yorumlamak için kullanışlı bir yol olduğu. Bu yorum hemen tüm alanları özel anlamına gelir.  
  
 Bu tür alanları neredeyse tanımı tarafından hiçbir zaman değiştirmek için gerekli olduğundan Biz bu katı sınırlama listesinden sabit ve statik salt okunur alanları hariç tutun.  
  
 **X DO NOT** genel veya korumalı örneği alanları sağlar.  
  
 Genel veya korumalı yapmak yerine alanları erişmek için özellikler sağlamalıdır.  
  
 **✓ DO** için hiçbir zaman değiştirecek sabitleri sabit alanları kullanın.  
  
 Derleyici, doğrudan kod çağırma içine const alanlarına ait değerlerin yakar. Bu nedenle, sabit değerler hiçbir zaman uyumluluk çiğnemekten riski değiştirilebilir.  
  
 **✓ DO** ortak statik kullanmak `readonly` alanları önceden tanımlanmış nesne örnekleri için.  
  
 Önceden tanımlanmış türünün örneklerini varsa, bunları genel olarak salt okunur statik alanları türü bildirin.  
  
 **X DO NOT** değişebilir türlerin örnekleri atamak `readonly` alanları.  
  
 Bir örneği sonra değiştirilebilen örnekleri türüyle bir değişebilir türüdür. Örneğin, dizileri, birçok koleksiyonun ve akışlar değişebilir türleridir ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, ve <xref:System.String?displayProperty=nameWithType> tüm sabittir. Bir başvuru türü alanı üzerinde salt okunur değiştiricisi değiştirilmekte olan gelen alanda depolanan örneği engeller, ancak alanın örnek veri örneğini değiştirme arama üyeleri tarafından değiştirilmiş engellemez.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
