---
title: Çerçeve Tasarım Yönergeleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c48b3cbaae4155a894ba77263505b2ca85238427
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="framework-design-guidelines"></a>Çerçeve Tasarım Yönergeleri
Bu bölüm, genişletme ve .NET Framework ile etkileşim kitaplıkları tasarlamak için yönergeler sağlar. Hedef kitaplığı tasarımcıları geliştirme için kullanılan programlama dili bağımsızdır birleşik bir programlama modeli sağlayarak API tutarlılık ve kullanım kolaylığı olun yardımcı olmaktır. Sınıfları ve .NET Framework genişleten bileşenleri geliştirirken, aşağıdaki tasarım yönergelere uymanızı öneririz. Tutarsız kitaplık tasarımı olumsuz Geliştirici üretkenliği etkiler ve benimseme zorlaştırır.  
  
 Yönergeler koşulları önekli basit öneriler olarak düzenlenir `Do`, `Consider`, `Avoid`, ve `Do not`. Bu yönergeleri sınıf kitaplığı tasarımcıları dengelemeler farklı çözümler arasında anlamanıza yardımcı olmak üzere tasarlanmıştır. Bu tasarım yönergeleri ihlal iyi kitaplık tasarımı burada gerektirir durumlar olabilir. Bu gibi durumlarda seyrek olmalıdır ve kararınızı NET ve ilgi çekici bir nedeni olması önemlidir.  
  
 Bu yönergeleri Defteri'nden adlı çalışmasından *Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri*, Krzysztof Cwalina ve Brad Abrams göre.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Derlemeler, ad alanlarını, türleri ve sınıf kitaplıkları üyelerinde adlandırmak için yönergeler sağlar.  
  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanma yönergeleri sağlar.  
  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 Tasarlama ve özellikleri, yöntemleri, Oluşturucular, alanlar, olaylar, işleçler ve parametreleri kullanma için yönergeler sağlar.  
  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Olaylar, sanal üyeleri ve geri çağırmalar kullanarak sınıflara gibi genişletilebilirlik mekanizmaları açıklanır ve framework'ün gereksinimlerini en iyi karşılayan mekanizmaları seçin açıklanmaktadır.  
  
 [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)  
 Tasarlama, atma ve çalýþýrçalýþma yakalama özel durumlar için tasarım yönergeleri açıklar.  
  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Diziler, öznitelikleri ve koleksiyonları gibi ortak türlerini kullanarak, serileştirme destekleme ve eşitlik işleçleri aşırı yükleme yönergelerini açıklar.  
  
 [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Seçme ve bağımlılık özellikleri ve dispose desen uygulamak için kılavuz bilgiler verilmektedir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../../../docs/framework/get-started/overview.md)  
 [.NET Framework için yol haritası](http://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
