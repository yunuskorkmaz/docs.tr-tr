---
title: "Soyutlamalar (Soyut türler ve arabirimler)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Soyutlamalar (Soyut türler ve arabirimler)
Bir Özet bir sözleşme açıklar ancak sözleşme tam uygulamasını sağlamaz türüdür. Soyutlamalar genellikle soyut sınıflar veya arabirimleri olarak uygulanır ve sözleşme uygulama türleri gerekli semantiği açıklayan başvuru belgeleri iyi tanımlanmış bir dizi birlikte gelir. .NET Framework'teki en önemli soyutlamalar bazıları <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, ve <xref:System.Object>.  
  
 Bir Özet sözleşmenin desteklediği somut bir türde uygulama ve bu somut türde framework API'leri alabilir (üzerinde işletim ile) kullanılarak çerçeveleri genişletebilirsiniz Özet.  
  
 Test zaman dayanacak yapabiliyor anlamlı ve yararlı bir soyutlama tasarlamak çok zor olabilir. Ana zorluk üyeleri, daha fazla ve en az doğru yetenek kümesini almaktır. Bir Özet çok fazla sayıda üye varsa, zor veya uygulamak bile imkansız olur. Taahhüt edilen işlevselliği için çok az sayıda üye varsa, birçok ilginç senaryolarda gereksiz olur.  
  
 Çerçeve içinde çok fazla soyutlamalar kullanılabilirlik framework'ün da olumsuz etkiler. Genellikle, bir Özet nasıl somut uygulamaları üzerinde soyutlama işletim API'leri ve daha büyük resmi içine uyduğunu anlama olmadan anlamak oldukça zor olabilir. Ayrıca, soyutlamalar ve üyeleri hangi sıklıkta bunları şifreli ve unapproachable kullanımları daha geniş bağlamında ilk anlama olmadan yapar mutlaka soyut adlarıdır.  
  
 Ancak, diğer genişletilebilirlik mekanizmaları genellikle eşleşemez son derece güçlü genişletilebilirlik soyutlamalar sağlar. Eklentileri gibi birçok mimari düzenleri çekirdek tersine çevirme (IOC) denetim, ardışık düzen ve benzeri altındadır. Ayrıca çerçeveleri edilebilirliğini için son derece önemlidir. İyi soyutlamalar birim testi amacıyla ağır bağımlılıkları çıkışı saplama olanaklı hale getirir. Özet olarak, soyutlamalar modern nesne yönelimli çerçeveleri sought-after zenginliğini için sorumludur.  
  
 **X yok** birkaç somut uygulamaları ve soyutlama kullanan API'ler geliştirerek sınanır sürece soyutlamalar sağlar.  
  
 **✓ YAPMAK** bir Özet tasarlarken, bir Özet sınıf arasında bir arabirim dikkatle seçin.  
  
 **✓ DÜŞÜNÜN** başvuru testleri soyutlamalar somut uygulamaları için sağlama. Bu tür testleri, kullanıcıların kendi uygulamalarını doğru sözleşmesini uygulama olup olmadığını sınamak izin vermelidir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
