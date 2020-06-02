---
title: Çerçeve Tasarım Yönergeleri
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 5a4edca70844a2b2a3972381b34efe85664f353d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276042"
---
# <a name="framework-design-guidelines"></a>Çerçeve Tasarım Yönergeleri
Bu bölüm, .NET Framework genişleten ve etkileşime geçen kitaplıklar tasarlamak için yönergeler sağlar. Amaç, geliştirme için kullanılan programlama dilinden bağımsız bir Birleşik programlama modeli sunarak, kitaplık tasarımcılarının API tutarlılığını ve kullanım kolaylığını sağladığından yardım sağlamaktır. .NET Framework genişleten sınıfları ve bileşenleri geliştirirken bu tasarım kılavuzlarını izlemenizi öneririz. Tutarsız kitaplık tasarımı, geliştirici üretkenliğini ve etkilenmeden benimsemesini olumsuz etkiler.  
  
 Yönergeler,, ve koşulları ön eki olan basit öneriler olarak `Do` düzenlenir `Consider` `Avoid` `Do not` . Bu yönergeler, sınıf kitaplığı tasarımcılarının farklı çözümler arasındaki dengeleri anlamalarına yardımcı olmak için tasarlanmıştır. İyi kitaplık tasarımının bu tasarım kılavuzlarını ihlal etmeniz gerektiği durumlar olabilir. Bu tür durumlar nadir olmalıdır ve kararınız için açık ve ilgi çekici bir nedeniniz olması önemlidir.  
  
 Bu yönergeler kitap *çerçevesi tasarım yönergelerinden alınmıştır: kurallar, deyimler ve yeniden kullanılabilir .NET kitaplıkları, 2. sürüm*, Vazysztof Cwalina ve atacan Abkms tarafından yapılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Adlandırma yönergeleri](naming-guidelines.md)  
 Derleme derlemeleri, ad alanları, türler ve sınıf kitaplıkları içindeki Üyeler için yönergeler sağlar.  
  
 [Tür tasarım yönergeleri](type.md)  
 Statik ve soyut sınıflar, arabirimler, numaralandırmalar, yapılar ve diğer türleri kullanmak için yönergeler sağlar.  
  
 [Üye tasarımı yönergeleri](member.md)  
 Özellikleri, yöntemleri, oluşturucuları, alanları, olayları, işleçleri ve parametreleri tasarlamak ve kullanmak için yönergeler sağlar.  
  
 [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)  
 Olaylar, sanal üyeler ve geri çağırmalar kullanılarak altsınıflama gibi genişletilebilirlik mekanizmalarını açıklar ve çerçeve gereksinimlerinizi en iyi şekilde karşılayan mekanizmaların nasıl seçileceğini açıklar.  
  
 [Özel Durumlar için Tasarım Yönergeleri](exceptions.md)  
 Özel durumları tasarlamak, oluşturmak ve yakalamak için tasarım yönergeleri açıklar.  
  
 [Kullanım yönergeleri](usage-guidelines.md)  
 Diziler, öznitelikler ve Koleksiyonlar gibi ortak türleri kullanma, serileştirme destekleme ve eşitlik işleçlerini aşırı yükleme için yönergeleri açıklar.  
  
 [Ortak tasarım desenleri](common-design-patterns.md)  
 Bağımlılık özelliklerini seçme ve uygulama için yönergeler sağlar.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Bakış](../../framework/get-started/overview.md)
- [Geliştirme Kılavuzu](../../framework/development-guide.md)
