---
title: Soyutlamalar (Soyut türler ve arabirimler)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ad8b2dd3dbf2a7a75c98a3115d4351dfea4e1a0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135074"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Soyutlamalar (Soyut türler ve arabirimler)
Bir Özet bir sözleşme açıklar ancak sözleşmenin tam bir uygulamayı sağlamayan bir türdür. Soyutlama genellikle soyut sınıflar veya arabirimleri olarak uygulanır ve bunlar gerekli semantiği sözleşmesi uygulama türlerini açıklayan başvuru belgeleri iyi tanımlanmış bir dizi birlikte gelir. .NET Framework'teki en önemli soyutlama bazıları <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, ve <xref:System.Object>.  
  
 Bir Özet anlaşmasını destekler somut bir türde uygulama ve bu somut bir türde framework API'leri kullanan (üzerinde çalışma ile) kullanılarak çerçeveleri genişletebilirsiniz Özet.  
  
 Test zaman dayanacak şekilde bulabildiği anlamlı ve kullanışlı bir soyutlama tasarlamak çok zordur. Ana zorluk üyeleri, daha fazla ve en az doğru ortaklık kümesi almaktır. Bir Özet çok fazla sayıda üye varsa, zor veya uygulamak bile imkansız olur. Taahhüt edilen işlev için çok az sayıda üye varsa, birçok ilgi çekici senaryolarda gereksiz olur.  
  
 Çerçeve içinde çok fazla soyutlama framework'ün kullanılabilirlik da olumsuz şekilde etkileyebilir. Genellikle, oldukça nasıl somut uygulamalarını ve API'leri soyutlama üzerinde çalışan daha büyük resmi içine uyduğunu anlama olmadan bir Özet anlamak zor olabilir. Ayrıca, soyutlamalar ve üye adları genellikle bunları görünümleriniz karmaşık ve unapproachable daha geniş bir bağlama kullanımları, ilk anlama olmadan getiren mutlaka soyuttur.  
  
 Ancak, soyutlama diğer genişletilebilirlik mekanizması genellikle eşleşemez son derece güçlü genişletilebilirlik sağlar. Çekirdek eklentiler gibi birçok mimari desenlerinin tersine çevirme (IOC) denetim, işlem hatları, vb. olur. Ayrıca test çerçevesini edilebilecek son derece önemlidir. İyi soyutlama ağır bağımlılıkları birim testi amacıyla kullanıma saplama mümkün kılar. Özet olarak, soyutlama sought-after zenginliğini modern nesne yönelimli çerçeveleri için sorumludur.  
  
 **X DO NOT** birkaç somut uygulamaları ve soyutlama kullanan API'ler geliştirerek sınanır sürece soyutlamalar sağlar.  
  
 **✓ DO** bir Özet tasarlarken, bir Özet sınıf arasında bir arabirim dikkatle seçin.  
  
 **✓ CONSIDER** başvuru testleri soyutlamalar somut uygulamaları için sağlama. Bu testleri kendi uygulamalarını sözleşmesini doğru uygulama olup olmadığını sınamak kullanıcılara izin vermelidir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
