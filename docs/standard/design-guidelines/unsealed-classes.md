---
title: Mühürsüz Sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778801"
---
# <a name="unsealed-classes"></a>Mühürsüz Sınıflar
Sealed sınıfları devralınamayacağını ve bunlar genişletilebilirlik engeller. Buna karşılık, öğesinden devralınan sınıflar mühürsüz sınıflar olarak adlandırılır.  
  
 **✓ CONSIDER** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.  
  
 Geliştiriciler genellikle özel oluşturucular, yeni bir yöntem veya yöntem aşırı yüklemeleri gibi kullanışlı üye eklemek için korumasız sınıflardan devralmasına izin istiyor. Örneğin, `System.Messaging.MessageQueue` korumasız ve bu nedenle, kullanıcıların belirli bir kuyruk yolu, varsayılan özel kuyruklar oluşturmak veya belirli senaryolar için API kolaylaştırmak özel yöntemler için sağlar.  
  
 Varsayılan olarak çoğu programlama dilinden sınıfları korumasız ve çerçeveleri de çoğu sınıf için önerilen varsayılan de budur. Mühürlenmemiş türler tarafından gösterilen genişletilebilirlik BİLDİRİMİNİZE çok değer veriyoruz framework kullanıcılar tarafından ve oldukça Hesaplı korumasız türleriyle ilişkili nispeten düşük test maliyetlerini nedeniyle sağlamak.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)
