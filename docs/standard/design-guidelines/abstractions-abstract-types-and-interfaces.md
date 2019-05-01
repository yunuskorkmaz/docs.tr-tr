---
title: Soyutlamalar (Soyut Türler ve Arabirimler)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: KrzysztofCwalina
ms.openlocfilehash: fcf566c24677630fdbb1fcd0eb7628f830b3be2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789226"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Soyutlamalar (Soyut Türler ve Arabirimler)
Bir Özet bir sözleşme açıklar ancak sözleşmenin tam bir uygulamayı sağlamayan bir türdür. Soyutlama genellikle soyut sınıflar veya arabirimleri olarak uygulanır ve bunlar gerekli semantiği sözleşmesi uygulama türlerini açıklayan başvuru belgeleri iyi tanımlanmış bir dizi birlikte gelir. .NET Framework'teki en önemli soyutlama bazıları <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, ve <xref:System.Object>.  
  
 Bir Özet anlaşmasını destekler somut bir türde uygulama ve bu somut bir türde framework API'leri kullanan (üzerinde çalışma ile) kullanılarak çerçeveleri genişletebilirsiniz Özet.  
  
 Test zaman dayanacak şekilde bulabildiği anlamlı ve kullanışlı bir soyutlama tasarlamak çok zordur. Ana zorluk üyeleri, daha fazla ve en az doğru ortaklık kümesi almaktır. Bir Özet çok fazla sayıda üye varsa, zor veya uygulamak bile imkansız olur. Taahhüt edilen işlev için çok az sayıda üye varsa, birçok ilgi çekici senaryolarda gereksiz olur.  
  
 Çerçeve içinde çok fazla soyutlama framework'ün kullanılabilirlik da olumsuz şekilde etkileyebilir. Genellikle, oldukça nasıl somut uygulamalarını ve API'leri soyutlama üzerinde çalışan daha büyük resmi içine uyduğunu anlama olmadan bir Özet anlamak zor olabilir. Ayrıca, soyutlamalar ve üye adları genellikle bunları görünümleriniz karmaşık ve unapproachable daha geniş bir bağlama kullanımları, ilk anlama olmadan getiren mutlaka soyuttur.  
  
 Ancak, soyutlama diğer genişletilebilirlik mekanizması genellikle eşleşemez son derece güçlü genişletilebilirlik sağlar. Çekirdek eklentiler gibi birçok mimari desenlerinin tersine çevirme (IOC) denetim, işlem hatları, vb. olur. Ayrıca test çerçevesini edilebilecek son derece önemlidir. İyi soyutlama ağır bağımlılıkları birim testi amacıyla kullanıma saplama mümkün kılar. Özet olarak, soyutlama sought-after zenginliğini modern nesne yönelimli çerçeveleri için sorumludur.  
  
 **X DO NOT** birkaç somut uygulamaları ve soyutlama kullanan API'ler geliştirerek sınanır sürece soyutlamalar sağlar.  
  
 **✓ DO** bir Özet tasarlarken, bir Özet sınıf arasında bir arabirim dikkatle seçin.  
  
 **✓ CONSIDER** başvuru testleri soyutlamalar somut uygulamaları için sağlama. Bu testleri kendi uygulamalarını sözleşmesini doğru uygulama olup olmadığını sınamak kullanıcılara izin vermelidir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
