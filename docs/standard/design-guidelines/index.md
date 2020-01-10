---
title: Çerçeve Tasarım Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 623391de63891c1695a63482a424bb76a861deba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709315"
---
# <a name="framework-design-guidelines"></a>Çerçeve Tasarım Yönergeleri
Bu bölüm, .NET Framework genişleten ve etkileşime geçen kitaplıklar tasarlamak için yönergeler sağlar. Amaç, geliştirme için kullanılan programlama dilinden bağımsız bir Birleşik programlama modeli sunarak, kitaplık tasarımcılarının API tutarlılığını ve kullanım kolaylığını sağladığından yardım sağlamaktır. .NET Framework genişleten sınıfları ve bileşenleri geliştirirken bu tasarım kılavuzlarını izlemenizi öneririz. Tutarsız kitaplık tasarımı, geliştirici üretkenliğini ve etkilenmeden benimsemesini olumsuz etkiler.  
  
 Yönergeler `Do`, `Consider`, `Avoid`ve `Do not`koşullara önek olarak basit öneriler olarak düzenlenir. Bu yönergeler, sınıf kitaplığı tasarımcılarının farklı çözümler arasındaki dengeleri anlamalarına yardımcı olmak için tasarlanmıştır. İyi kitaplık tasarımının bu tasarım kılavuzlarını ihlal etmeniz gerektiği durumlar olabilir. Bu tür durumlar nadir olmalıdır ve kararınız için açık ve ilgi çekici bir nedeniniz olması önemlidir.  
  
 Bu yönergeler kitap *çerçevesi tasarım yönergelerinden alınmıştır: kurallar, deyimler ve yeniden kullanılabilir .NET kitaplıkları, 2. sürüm*, Vazysztof Cwalina ve atacan Abkms tarafından yapılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Derleme derlemeleri, ad alanları, türler ve sınıf kitaplıkları içindeki Üyeler için yönergeler sağlar.  
  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanmak için yönergeler sağlar.  
  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 Özellikleri, yöntemleri, oluşturucuları, alanları, olayları, işleçleri ve parametreleri tasarlamak ve kullanmak için yönergeler sağlar.  
  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Olaylar, sanal üyeler ve geri çağırmalar kullanılarak altsınıflama gibi genişletilebilirlik mekanizmalarını açıklar ve çerçeve gereksinimlerinizi en iyi şekilde karşılayan mekanizmaların nasıl seçileceğini açıklar.  
  
 [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)  
 Özel durumları tasarlamak, oluşturmak ve yakalamak için tasarım yönergeleri açıklar.  
  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Diziler, öznitelikler ve Koleksiyonlar gibi ortak türleri kullanma, serileştirme destekleme ve eşitlik işleçlerini aşırı yükleme için yönergeleri açıklar.  
  
 [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Bağımlılık özelliklerini seçme ve uygulama için yönergeler sağlar.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel bakış](../../../docs/framework/get-started/overview.md)
- [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
