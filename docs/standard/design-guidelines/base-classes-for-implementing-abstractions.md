---
title: "Soyutlamalar uygulamak için temel sınıflar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96264456ac6afc569c46caf5faed6c37ea22bc8e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="base-classes-for-implementing-abstractions"></a>Soyutlamalar uygulamak için temel sınıflar
Kesinlikle olarak bakıldığında, başka bir sınıf ondan türetilmiş bir sınıf bir taban sınıf olur. Bu bölümde amacıyla ancak, bir taban sınıf çoğunlukla ortak bir Özet sağlar veya diğer sınıflar bazı yeniden kullanmak uygulama devralma ancak varsayılan için tasarlanmış bir sınıftır. Temel sınıflar genellikle ortasında bir Özet hiyerarşisinin kökü altındaki çeşitli özel uygulamalar arasındaki devralma hiyerarşileri sit.  
  
 Bunlar, uygulama Yardımcıları soyutlamalar uygulamak için hizmet. Örneğin, öğelerinin sıralı koleksiyonlar için Framework'ün soyutlamalar biri <xref:System.Collections.Generic.IList%601> arabirimi. Uygulama <xref:System.Collections.Generic.IList%601> Önemsiz, değil ve bu nedenle Framework gibi birkaç temel sınıf sağlar <xref:System.Collections.ObjectModel.Collection%601> ve <xref:System.Collections.ObjectModel.KeyedCollection%602>, hangi hizmet Yardımcıları özel koleksiyonlar uygulamak için.  
  
 Temel sınıflar çok fazla uygulama içerir eğilimli olduğundan genellikle soyutlamalar kendileri tarafından hizmet vermek için uygun değildir. Örneğin, `Collection<T>` temel sınıf içeren uygulama nongeneric uygulayan olgu ilgili çok sayıda `IList` (daha iyi nongeneric koleksiyonları ile tümleştirmek için) arabirim ve öğeleri koleksiyonu depolanan olduğunu olgusu bellek kendi alanlarından birinde.  
  
 Daha önce ele alındığı temel sınıflar soyutlamalar uygulamak için gereken kullanıcılar için çok değerli bir kaynak Yardım sağlayabilir, ancak aynı anda önemli bir yükümlülük olabilirler. Bunlar yüzey alanını ekleyin ve devralma hiyerarşileri derinliğini artırın ve böylece kavramsal framework zorlaştırabilir. Bu nedenle, yalnızca bunlar framework kullanıcılara önemli değer'ı belirtirseniz temel sınıflar kullanılmalıdır. Değer, taban sınıfından devralma yerine iç uygulaması için büyük/küçük harfe temsilci kesinlikle düşünülmesi gereken framework'ün Implementers belirtirseniz bunlar kaçınılmalıdır.  
  
 **✓ DÜŞÜNÜN** yapmayı temel, Özet üye içermeyen olsa bile soyut sınıflar. Bu kullanıcılar için açık bir şekilde iletişim kurar, sınıfı yalnızca devralınan için tasarlanmıştır.  
  
 **✓ DÜŞÜNÜN** mainline senaryo türlerinden ayrı bir ad alanı taban sınıfları yerleştirmekten. Tanımı, temel sınıflar gelişmiş Genişletilebilirlik senaryoları için tasarlanmıştır ve bu nedenle kullanıcıların çoğunluğunun ilginç değildir.  
  
 **KAÇININ x** sınıfı için ortak API'ler kullanımda amaçlanıyorsa bir "Temel" soneki temel sınıflarının adlandırma.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
