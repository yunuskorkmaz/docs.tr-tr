---
title: Çerçeve Tasarım Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: c20430f9cdcd71cc2e178d38aeed48f9fa4e75c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026386"
---
# <a name="framework-design-guidelines"></a>Çerçeve Tasarım Yönergeleri
Bu bölüm, genişleten ve .NET Framework ile etkileşim kitaplıklar tasarlama için yönergeler sağlar. Bağımsız geliştirme için kullanılan programlama dili olan birleşik bir programlama modeli sağlayarak API tutarlığı ve kullanım kolaylığı sağlamak kitaplığı tasarımcıları yardımcı olmaktır. Sınıfları ve genişleten .NET Framework bileşenleri geliştirirken bu tasarım ilkelerine uyun öneririz. Tutarsız kitaplığı tasarım olumsuz geliştirici üretkenliğinizi etkiler ve benimseme gerçekleştirilmesini önler.  
  
 Kılavuzları basit önerileri şartlarını önek olarak düzenlenir `Do`, `Consider`, `Avoid`, ve `Do not`. Bu yönergeleri, sınıf kitaplığı tasarımcıları farklı çözümler gereksinimlerimi karşılamama anlamanıza yardımcı olmak için tasarlanmıştır. Bu tasarım yönergeleri ihlal iyi kitaplığı tasarım burada gerektirir durumlar olabilir. Bu gibi durumlarda nadiren olmalıdır ve kararınız için NET ve ilgi çekici bir neden olması önemlidir.  
  
 Bu yönergeleri defterinden adlı çalışmasından *çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler*, Krzysztof Cwalina ve Brad Abrams.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Derlemeler, ad alanları, türler ve üyeler sınıf kitaplıkları olarak adlandırmak için yönergeler sağlar.  
  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanma yönergeleri sağlar.  
  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 Tasarlama ve özellikleri, yöntemleri, Oluşturucular, alanlar, olaylar, işleçler ve parametreleri kullanma için yönergeler sağlar.  
  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Genişletilebilirlik mekanizması sınıflara, olayları ve sanal üyeleri geri çağırmalar gibi açıklanır ve seçin, framework'ün gereksinimlerini en iyi mekanizmalarını açıklar.  
  
 [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)  
 Tasarlama, oluşturma ve çalýþýrçalýþma yakalama özel durumlar için tasarım yönergeleri açıklar.  
  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Ortak bir türleri dizilerini, öznitelikleri ve koleksiyonları gibi kullanarak, serileştirme destekleme ve eşitlik işleçleri aşırı yükleme yönergeleri açıklar.  
  
 [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Seçme ve bağımlılık özellikleri uygulamak için yönergeler sağlar.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel bakış](../../../docs/framework/get-started/overview.md)
- [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
