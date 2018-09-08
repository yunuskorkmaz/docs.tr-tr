---
title: Soyutlama uygulamak için temel sınıflar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f326ee895251678c7a23ea84a11e83951edf2cc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194883"
---
# <a name="base-classes-for-implementing-abstractions"></a>Soyutlama uygulamak için temel sınıflar
NET olarak söylemek gerekirse, başka bir sınıfın bu türden türetilmiş bir sınıf bir temel sınıf olur. Amacıyla bu bölümde, ancak bir taban sınıf genellikle ortak bir Özet sağlar veya diğer sınıfların bazılarını yeniden kullanmak uygulama yine de devralma varsayılan için tasarlanmış bir sınıftır. Temel sınıflar, genellikle bir Özet bir hiyerarşinin kökü altındaki çeşitli özel uygulamalar arasındaki devralma hiyerarşilerini ortasında bulunur.  
  
 Bunlar, uygulama Yardımcıları soyutlama uygulamak için hizmet eder. Örneğin, öğelerin sıralı koleksiyonlar için Framework'ün soyutlama biri olan <xref:System.Collections.Generic.IList%601> arabirimi. Uygulama <xref:System.Collections.Generic.IList%601> Önemsiz değildir ve bu nedenle çerçeve gibi birkaç temel sınıf sağlar <xref:System.Collections.ObjectModel.Collection%601> ve <xref:System.Collections.ObjectModel.KeyedCollection%602>, hangi hizmet Yardımcıları özel koleksiyonlar uygulamak için.  
  
 Temel sınıflar içeren çok fazla uygulama eğilimli olduğundan genellikle soyutlama ayrı olarak hizmet vermek için uygun değildir. Örneğin, `Collection<T>` temel sınıfı içerir olgusu nongeneric uygulayan ilgili uygulama çok sayıda `IList` (daha iyi jenerik olmayan koleksiyon ile tümleştirmek için) arabirim ve öğelerin bir koleksiyonunu depolanan bu olgusu bellek alanlarından birinde.  
  
 Daha önce ele alındığı temel sınıflar soyutlama uygulamak için gereken kullanıcılar için her Yardım sağlayabilir, ancak aynı anda önemli bir yükümlülük olabilirler. Bunlar yüzey alanını ekleyin ve devralma hiyerarşilerini derinliğini Artır ve bu nedenle, kavramsal olarak framework genişlemesiyle. Yalnızca bunlar önemli ölçüde framework'ün kullanıcılara sağlarsanız, bu nedenle, temel sınıflar kullanılmalıdır. İçinde kesin bir temel sınıftan devralma yerine iç bir uygulama için büyük/küçük harf temsilci düşünülmelidir framework'ün uygulayıcılar değeri sağlarsanız, kaçınılmalıdır.  
  
 **✓ CONSIDER** yapmayı temel, Özet üye içermeyen olsa bile soyut sınıflar. Bu kullanıcılara açıkça iletişim kurar, sınıfı yalnızca devralınan için tasarlanmıştır.  
  
 **✓ CONSIDER** mainline senaryo türlerinden ayrı bir ad alanı taban sınıfları yerleştirmekten. Tanımına göre temel sınıflar, gelişmiş Genişletilebilirlik senaryoları için tasarlanmıştır ve bu nedenle kullanıcıların çoğunluğunun ilgi çekici olmayan.  
  
 **X AVOID** sınıfı için ortak API'ler kullanımda amaçlanıyorsa bir "Temel" soneki temel sınıflarının adlandırma.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
