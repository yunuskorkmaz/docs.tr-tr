---
title: "Framework tasarım yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a812207fb58e6c87c263966081060d02f8038963
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="framework-design-guidelines"></a>Framework tasarım yönergeleri
Bu bölüm, genişletme ve .NET Framework ile etkileşim kitaplıkları tasarlamak için yönergeler sağlar. Hedef kitaplığı tasarımcıları geliştirme için kullanılan programlama dili bağımsızdır birleşik bir programlama modeli sağlayarak API tutarlılık ve kullanım kolaylığı olun yardımcı olmaktır. Sınıfları ve .NET Framework genişleten bileşenleri geliştirirken, aşağıdaki tasarım yönergelere uymanızı öneririz. Tutarsız kitaplık tasarımı olumsuz Geliştirici üretkenliği etkiler ve benimseme zorlaştırır.  
  
 Yönergeler koşulları önekli basit öneriler olarak düzenlenir `Do`, `Consider`, `Avoid`, ve `Do not`. Bu yönergeleri sınıf kitaplığı tasarımcıları dengelemeler farklı çözümler arasında anlamanıza yardımcı olmak üzere tasarlanmıştır. Bu tasarım yönergeleri ihlal iyi kitaplık tasarımı burada gerektirir durumlar olabilir. Bu gibi durumlarda seyrek olmalıdır ve kararınızı NET ve ilgi çekici bir nedeni olması önemlidir.  
  
 Bu yönergeleri Defteri'nden adlı çalışmasından *Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri*, Krzysztof Cwalina ve Brad Abrams göre.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Adlandırma yönergeleri](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Derlemeler, ad alanlarını, türleri ve sınıf kitaplıkları üyelerinde adlandırmak için yönergeler sağlar.  
  
 [Türü tasarım yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanma yönergeleri sağlar.  
  
 [Üye tasarım yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 Tasarlama ve özellikleri, yöntemleri, Oluşturucular, alanlar, olaylar, işleçler ve parametreleri kullanma için yönergeler sağlar.  
  
 [Genişletilebilirlik için tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Olaylar, sanal üyeleri ve geri çağırmalar kullanarak sınıflara gibi genişletilebilirlik mekanizmaları açıklanır ve framework'ün gereksinimlerini en iyi karşılayan mekanizmaları seçin açıklanmaktadır.  
  
 [Özel durumlar için tasarım yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)  
 Tasarlama, atma ve çalýþýrçalýþma yakalama özel durumlar için tasarım yönergeleri açıklar.  
  
 [Kullanım yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Diziler, öznitelikleri ve koleksiyonları gibi ortak türlerini kullanarak, serileştirme destekleme ve eşitlik işleçleri aşırı yükleme yönergelerini açıklar.  
  
 [Ortak tasarım desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Seçme ve bağımlılık özellikleri ve dispose desen uygulamak için kılavuz bilgiler verilmektedir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../../../docs/framework/get-started/overview.md)  
 [.NET Framework için yol haritası](http://msdn.microsoft.com/en-us/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
