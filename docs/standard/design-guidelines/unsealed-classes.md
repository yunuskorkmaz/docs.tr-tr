---
title: Mühürsüz sınıflar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef0f1c4c9b2d1928d6f96d62ab12df9786756498
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891383"
---
# <a name="unsealed-classes"></a>Mühürsüz sınıflar
Sealed sınıfları devralınamayacağını ve bunlar genişletilebilirlik engeller. Buna karşılık, öğesinden devralınan sınıflar mühürsüz sınıflar olarak adlandırılır.  
  
 **✓ CONSIDER** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.  
  
 Geliştiriciler genellikle özel oluşturucular, yeni bir yöntem veya yöntem aşırı yüklemeleri gibi kullanışlı üye eklemek için korumasız sınıflardan devralmasına izin istiyor. Örneğin, `System.Messaging.MessageQueue` korumasız ve bu nedenle, kullanıcıların belirli bir kuyruk yolu, varsayılan özel kuyruklar oluşturmak veya belirli senaryolar için API kolaylaştırmak özel yöntemler için sağlar.  
  
 Varsayılan olarak çoğu programlama dilinden sınıfları korumasız ve çerçeveleri de çoğu sınıf için önerilen varsayılan de budur. Mühürlenmemiş türler tarafından gösterilen genişletilebilirlik BİLDİRİMİNİZE çok değer veriyoruz framework kullanıcılar tarafından ve oldukça Hesaplı korumasız türleriyle ilişkili nispeten düşük test maliyetlerini nedeniyle sağlamak.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)
