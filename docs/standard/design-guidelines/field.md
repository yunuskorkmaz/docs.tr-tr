---
title: Alan Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 3ab8fe279605c4795bb3a26557d0241b186b273a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026412"
---
# <a name="field-design"></a>Alan Tasarımı
Kapsülleme, en önemli kavramları nesne yönelimli tasarım biridir. Bu ilke, nesnenin içinde depolanan veriler yalnızca o nesneye erişilebilir olması gerektiğini belirtir.  
  
 İlke yorumlamak için kullanışlı bir yol, bir türü türün üyeleri için dışındaki kod bozmadan alanlar (ada veya türe değişiklikler) bu tür değişiklikler yapılabilir olacak şekilde tasarlanmalıdır söyleyin sağlamaktır. Bu yorumu, hemen tüm alanlar özel olması gerektiğini belirtir.  
  
 Bu tür alanlar neredeyse tanımı gereği hiçbir zaman değiştirmek için gerekli olduğundan bu katı kısıtlaması, sabit ve statik salt okunur alanları tutarız.  
  
 **X DO NOT** genel veya korumalı örneği alanları sağlar.  
  
 Ortak veya korumalı yapmak yerine alanları erişmek için özellikler sağlamanız gerekir.  
  
 **✓ DO** için hiçbir zaman değiştirecek sabitleri sabit alanları kullanın.  
  
 Derleyici kod doğrudan çağırma içine const alanların değerlerini harekete. Bu nedenle, sabit değerler hiçbir zaman uyumluluk bozucu riski değiştirilebilir.  
  
 **✓ DO** ortak statik kullanmak `readonly` alanları önceden tanımlanmış nesne örnekleri için.  
  
 Önceden tanımlanmış tür örnekleri varsa, bunları genel olarak salt okunur statik alanları türü bildirin.  
  
 **X DO NOT** değişebilir türlerin örnekleri atamak `readonly` alanları.  
  
 Kesilebilir tür örneklerle örneği oluşturulur sonra değiştirilebilen bir türdür. Örneğin, diziler, çoğu koleksiyonları ve akışları değişebilir türleridir ancak <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, ve <xref:System.String?displayProperty=nameWithType> tüm sabittir. Bir başvuru türü alanı salt okunur değiştiricisi değiştirilmesini alanında depolanan örneği engeller ancak alanın örnek verisinin örneğini değiştirme çağıran üyeleri tarafından değiştirilmesini önlemez.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
