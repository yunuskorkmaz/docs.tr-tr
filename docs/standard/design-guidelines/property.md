---
title: Özellik Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 5d5cdbfdb38c7aebaca6cbcdeb63959ac12884e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709133"
---
# <a name="property-design"></a>Özellik Tasarımı
Özellikler teknik açıdan yöntemlere çok benzer olsa da, bunlar kullanım senaryolarında oldukça farklıdır. Akıllı alanlar olarak görülenmelidir. Alanların çağırma söz dizimi ve yöntemlerin esnekliği vardır.  
  
 **✓ DO** çağıran özelliğin değerini değiştirmek açmaması gereken, yalnızca get özellikleri oluşturun.  
  
 Özelliğin türü kesilebilir bir başvuru türü ise, özellik salt al olsa bile Özellik değerinin değiştirilebileceğini aklınızda bulundurun.  
  
 **X DO NOT** alıcı daha geniş erişilebilirlik sahip ayarlayıcı yalnızca küme özellikleri veya özellikleri sağlar.  
  
 Örneğin, özellikleri ortak bir ayarlayıcı ve korumalı bir alıcı ile birlikte kullanmayın.  
  
 Özellik alıcısı sağlanmadıysa, işlevi bir yöntem olarak uygulayın. Yöntem adını `Set` ile başlatmayı ve özelliği adlandırdıklarınızı takip etmeyi düşünün. Örneğin <xref:System.AppDomain>, `CachePath`adlı salt ayarlı bir özelliği olması yerine `SetCachePath` adlı bir yönteme sahiptir.  
  
 **✓ DO** tüm özellikleri, varsayılan bir güvenlik açığı veya çok verimsiz kodu yol açmamasını sağlamak için duyarlı varsayılan değerler sağlayın.  
  
 **✓ DO** bu nesne bir geçici geçersiz durumda sonuçları olsa bile herhangi bir sırada ayarlanacak özellikler izin verir.  
  
 İki veya daha fazla özelliğin, bir özelliğin bazı değerlerinin aynı nesne üzerindeki diğer özelliklerin değerleri verildiğinde geçersiz olabileceği bir nokta ile ilişkili olması yaygındır. Bu gibi durumlarda, ilişkili özellikler gerçekten nesne tarafından birlikte kullanıldığından, geçersiz durumdan kaynaklanan özel durumlar ertelenmelidir.  
  
 **✓ DO** özellik set yordamı bir özel durum oluşturursa önceki değeri korumak.  
  
 **X AVOID** özellik alıcıları özel durumları atma.  
  
 Özellik alıcıları basit işlemler olmalıdır ve herhangi bir önkoşullara sahip olmamalıdır. Alıcı bir özel durum oluştur, büyük olasılıkla bir yöntem olarak yeniden tasarlanması gerekir. Bu kuralın, bağımsız değişkenlerin doğrulanması sonucunda özel durumlar beklediğimiz Dizin oluşturucular için uygulanmadığından emin olun.  
  
### <a name="indexed-property-design"></a>Dizinli özellik tasarımı  
 Dizinli bir özellik, parametrelere sahip olabilecek ve dizi dizine benzer özel söz dizimi ile çağrılabilen özel bir özelliktir.  
  
 Dizinli özellikler genellikle Dizin oluşturucular olarak adlandırılır. Dizin oluşturucular yalnızca bir mantıksal koleksiyondaki öğelere erişim sağlayan API 'lerde kullanılmalıdır. Örneğin, bir dize bir karakter koleksiyonudur ve <xref:System.String?displayProperty=nameWithType> üzerindeki Dizin Oluşturucu, karakterlerine erişmek için eklenmiştir.  
  
 **✓ CONSIDER** iç dizisinde depolanan verilere erişim sağlamak için dizin oluşturucular kullanma.  
  
 **✓ CONSIDER** öğe koleksiyonunu temsil eden türlerinde dizin oluşturucular sağlama.  
  
 **X AVOID** dizin oluşturulmuş özellikleri birden fazla parametresiyle kullanarak.  
  
 Tasarım birden çok parametre gerektiriyorsa, özelliğin bir mantıksal koleksiyona bir erişimciyi temsil edip etmediğini yeniden düşünün. Yoksa, bunun yerine yöntemleri kullanın. Yöntem adını `Get` veya `Set`başlatmayı düşünün.  
  
 **X AVOID** dışında parametre türleri oluşturucularla <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, veya enum.  
  
 Tasarımda diğer parametre türleri gerekiyorsa, API 'nin mantıksal bir koleksiyona bir erişimciyi temsil edip etmediğini kesin olarak yeniden değerlendirin. Değilse, bir yöntemi kullanın. Yöntem adını `Get` veya `Set`başlatmayı düşünün.  
  
 **✓ DO** adını kullanın `Item` için tabii daha iyi bir adı olmadıkça özellikleri dizine (örn., bkz: <xref:System.String.Chars%2A> özellikte `System.String`).  
  
 ' C#De, Dizin oluşturucular varsayılan olarak adlandırılmış öğedir. Bu adı özelleştirmek için <xref:System.Runtime.CompilerServices.IndexerNameAttribute> kullanılabilir.  
  
 **X DO NOT** hem bir dizin oluşturucu hem de anlam olarak eşdeğerdir yöntemleri sağlar.  
  
 **X DO NOT** aşırı yüklenmiş dizin oluşturucular bir türde birden fazla ailesi sağlayın.  
  
 Bu, C# derleyici tarafından zorlanır.  
  
 **X DO NOT** kullanım varsayılan olmayan dizin oluşturulmuş özellikleri.  
  
 Bu, C# derleyici tarafından zorlanır.  
  
### <a name="property-change-notification-events"></a>Özellik değişiklik bildirimi olayları  
 Bazen bir özellik değerindeki değişiklikleri kullanıcıya bildiren bir olay sağlamak yararlı olur. Örneğin, `System.Windows.Forms.Control`, `Text` özelliğinin değeri değiştirildikten sonra `TextChanged` olayını harekete geçirir.  
  
 **✓ CONSIDER** değişiklik üst düzey API'leri (genellikle Tasarımcı bileşenleri) özellik değerlerinde değişiklik yapıldığında bildirim olayları oluşturma.  
  
 Bir kullanıcının bir nesnenin özelliğinin ne zaman değiştiğini bilmesini sağlamak için iyi bir senaryo varsa, nesne özellik için bir değişiklik bildirimi olayı tetiklemelidir.  
  
 Bununla birlikte, temel türler veya Koleksiyonlar gibi alt düzey API 'Ler için bu tür olayları yükseltme yüküyle ilgili ek yükün olması düşüktür. Örneğin, <xref:System.Collections.Generic.List%601>, listeye yeni bir öğe eklendiğinde ve `Count` özelliği değiştiğinde bu tür olayları yükseltemez.  
  
 **✓ CONSIDER** değişiklik bir özelliğin değerini dış zorlar değiştiğinde bildirim olayları oluşturma.  
  
 Bir özellik değeri, bazı dış zorlanarak (nesne üzerinde Yöntemler çağırma dışında bir şekilde) değişirse, olay oluşturma, geliştiricinin değerin değiştiğini ve değiştiğini gösterir. İyi bir örnek, metin kutusu denetiminin `Text` özelliğidir. Kullanıcı bir `TextBox`metin yazdığında, özellik değeri otomatik olarak değişir.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
