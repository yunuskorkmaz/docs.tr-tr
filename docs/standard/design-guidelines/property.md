---
title: Özellik Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 8b6570b1b7c292729b78f2fe52f24f73319efe6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743662"
---
# <a name="property-design"></a>Özellik Tasarımı
Özellikler teknik açıdan yöntemlere çok benzer olsa da, bunlar kullanım senaryolarında oldukça farklıdır. Akıllı alanlar olarak görülenmelidir. Alanların çağırma söz dizimi ve yöntemlerin esnekliği vardır.

 çağıranın özelliğin değerini değiştirememelidir ✔️ salt-al özellikleri oluşturun.

 Özelliğin türü kesilebilir bir başvuru türü ise, özellik salt al olsa bile Özellik değerinin değiştirilebileceğini aklınızda bulundurun.

 ❌, ayarlayıcıdan daha geniş erişilebilirliği olan, salt ayarlı özellikler veya özellikler sağlamaz.

 Örneğin, özellikleri ortak bir ayarlayıcı ve korumalı bir alıcı ile birlikte kullanmayın.

 Özellik alıcısı sağlanmadıysa, işlevi bir yöntem olarak uygulayın. Yöntem adını `Set` ile başlatmayı ve özelliği adlandırdıklarınızı takip etmeyi düşünün. Örneğin <xref:System.AppDomain>, `CachePath`adlı salt ayarlı bir özelliği olması yerine `SetCachePath` adlı bir yönteme sahiptir.

 ✔️ Tüm özellikler için, varsayılan değerlerin bir güvenlik deliğe veya daha fazla verimsiz bir koda neden olmamasını sağlamak için, tüm özellikler için hazır varsayılan değerler sağlar.

 ✔️, nesnenin geçici olarak geçersiz bir durumuna neden olsa da, özelliklerin herhangi bir sırada ayarlanmasına izin verir.

 İki veya daha fazla özelliğin, bir özelliğin bazı değerlerinin aynı nesne üzerindeki diğer özelliklerin değerleri verildiğinde geçersiz olabileceği bir nokta ile ilişkili olması yaygındır. Bu gibi durumlarda, ilişkili özellikler gerçekten nesne tarafından birlikte kullanıldığından, geçersiz durumdan kaynaklanan özel durumlar ertelenmelidir.

 bir özellik ayarlayıcısı özel durum oluşturursa, önceki değeri koruma ✔️.

 ❌ özelliğinden özel durumlar oluşturmaktan kaçının.

 Özellik alıcıları basit işlemler olmalıdır ve herhangi bir önkoşullara sahip olmamalıdır. Alıcı bir özel durum oluştur, büyük olasılıkla bir yöntem olarak yeniden tasarlanması gerekir. Bu kuralın, bağımsız değişkenlerin doğrulanması sonucunda özel durumlar beklediğimiz Dizin oluşturucular için uygulanmadığından emin olun.

### <a name="indexed-property-design"></a>Dizinli özellik tasarımı
 Dizinli bir özellik, parametrelere sahip olabilecek ve dizi dizine benzer özel söz dizimi ile çağrılabilen özel bir özelliktir.

 Dizinli özellikler genellikle Dizin oluşturucular olarak adlandırılır. Dizin oluşturucular yalnızca bir mantıksal koleksiyondaki öğelere erişim sağlayan API 'lerde kullanılmalıdır. Örneğin, bir dize bir karakter koleksiyonudur ve <xref:System.String?displayProperty=nameWithType> üzerindeki Dizin Oluşturucu, karakterlerine erişmek için eklenmiştir.

 ✔️, iç dizide depolanan verilere erişim sağlamak için Dizin oluşturucular kullanmayı düşünün.

 ✔️ öğe koleksiyonlarını temsil eden türlerde Dizin oluşturucular sağlamayı düşünün.

 ❌ birden fazla parametreli dizinli Özellikler kullanmaktan KAÇıNıN.

 Tasarım birden çok parametre gerektiriyorsa, özelliğin bir mantıksal koleksiyona bir erişimciyi temsil edip etmediğini yeniden düşünün. Yoksa, bunun yerine yöntemleri kullanın. Yöntem adını `Get` veya `Set`başlatmayı düşünün.

 ❌ <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>veya enum dışında parametre türlerine sahip dizin oluşturuculardan KAÇıNıN.

 Tasarımda diğer parametre türleri gerekiyorsa, API 'nin mantıksal bir koleksiyona bir erişimciyi temsil edip etmediğini kesin olarak yeniden değerlendirin. Değilse, bir yöntemi kullanın. Yöntem adını `Get` veya `Set`başlatmayı düşünün.

 ✔️, açıkça daha iyi bir ad olmadıkça, dizinli özellikler için `Item` adı kullanın (ör. `System.String`<xref:System.String.Chars%2A> özelliğine bakın).

 ' C#De, Dizin oluşturucular varsayılan olarak adlandırılmış öğedir. Bu adı özelleştirmek için <xref:System.Runtime.CompilerServices.IndexerNameAttribute> kullanılabilir.

 ❌, hem bir Dizin Oluşturucu hem de anlamsal olarak eşdeğer yöntemler sağlamaz.

 ❌, tek bir türde çok sayıda aşırı yüklenmiş dizin grubu sağlamaz.

 Bu, C# derleyici tarafından zorlanır.

 ❌ varsayılan olmayan dizinli özellikleri kullanmaz.

 Bu, C# derleyici tarafından zorlanır.

### <a name="property-change-notification-events"></a>Özellik değişiklik bildirimi olayları
 Bazen bir özellik değerindeki değişiklikleri kullanıcıya bildiren bir olay sağlamak yararlı olur. Örneğin, `System.Windows.Forms.Control`, `Text` özelliğinin değeri değiştirildikten sonra `TextChanged` olayını harekete geçirir.

 ✔️, üst düzey API 'lerde (genellikle Tasarımcı bileşenleri) özellik değerleri değiştirildiğinde değişiklik bildirimi olaylarını yükseltmeyi göz önünde bulundurun.

 Bir kullanıcının bir nesnenin özelliğinin ne zaman değiştiğini bilmesini sağlamak için iyi bir senaryo varsa, nesne özellik için bir değişiklik bildirimi olayı tetiklemelidir.

 Bununla birlikte, temel türler veya Koleksiyonlar gibi alt düzey API 'Ler için bu tür olayları yükseltme yüküyle ilgili ek yükün olması düşüktür. Örneğin, <xref:System.Collections.Generic.List%601>, listeye yeni bir öğe eklendiğinde ve `Count` özelliği değiştiğinde bu tür olayları yükseltemez.

 ✔️, bir özelliğin değeri dış güçlerle değiştirildiğinde değişiklik bildirimi olaylarını yükseltmeyi göz önünde bulundurun.

 Bir özellik değeri, bazı dış zorlanarak (nesne üzerinde Yöntemler çağırma dışında bir şekilde) değişirse, olay oluşturma, geliştiricinin değerin değiştiğini ve değiştiğini gösterir. İyi bir örnek, metin kutusu denetiminin `Text` özelliğidir. Kullanıcı bir `TextBox`metin yazdığında, özellik değeri otomatik olarak değişir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
