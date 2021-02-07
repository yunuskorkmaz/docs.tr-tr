---
description: 'Daha fazla bilgi edinin: Özellik tasarımı'
title: Özellik Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: b2f776a5fb651f8b2e61b750a556704fa6c8c366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731805"
---
# <a name="property-design"></a>Özellik Tasarımı

Özellikler teknik açıdan yöntemlere çok benzer olsa da, bunlar kullanım senaryolarında oldukça farklıdır. Akıllı alanlar olarak görülenmelidir. Alanların çağırma söz dizimi ve yöntemlerin esnekliği vardır.

 çağıranın özelliğin değerini değiştirememelidir ✔️ salt-al özellikleri oluşturun.

 Özelliğin türü kesilebilir bir başvuru türü ise, özellik salt al olsa bile Özellik değerinin değiştirilebileceğini aklınızda bulundurun.

 ❌ Ayarlayıcının, alıcı tarafından daha geniş erişilebilirliği olan salt ayarlı özelliklerini veya özelliklerini sağlamaktan.

 Örneğin, özellikleri ortak bir ayarlayıcı ve korumalı bir alıcı ile birlikte kullanmayın.

 Özellik alıcısı sağlanmadıysa, işlevi bir yöntem olarak uygulayın. Yöntem adını ile başlatmayı `Set` ve özelliği adlandırdıklarınız ile birlikte izlemenizi düşünün. Örneğin, <xref:System.AppDomain> `SetCachePath` yalnızca set-Only özelliği olmak yerine çağrılan bir yöntemi vardır `CachePath` .

 ✔️ Tüm özellikler için, varsayılan değerlerin bir güvenlik deliğe veya daha fazla verimsiz bir koda neden olmamasını sağlamak için, tüm özellikler için hazır varsayılan değerler sağlar.

 ✔️, nesnenin geçici olarak geçersiz bir durumuna neden olsa da, özelliklerin herhangi bir sırada ayarlanmasına izin verir.

 İki veya daha fazla özelliğin, bir özelliğin bazı değerlerinin aynı nesne üzerindeki diğer özelliklerin değerleri verildiğinde geçersiz olabileceği bir nokta ile ilişkili olması yaygındır. Bu gibi durumlarda, ilişkili özellikler gerçekten nesne tarafından birlikte kullanıldığından, geçersiz durumdan kaynaklanan özel durumlar ertelenmelidir.

 bir özellik ayarlayıcısı özel durum oluşturursa, önceki değeri koruma ✔️.

 ❌ Getters Özellikler 'den özel durumlar oluşturmaktan kaçının.

 Özellik alıcıları basit işlemler olmalıdır ve herhangi bir önkoşullara sahip olmamalıdır. Alıcı bir özel durum oluştur, büyük olasılıkla bir yöntem olarak yeniden tasarlanması gerekir. Bu kuralın, bağımsız değişkenlerin doğrulanması sonucunda özel durumlar beklediğimiz Dizin oluşturucular için uygulanmadığından emin olun.

### <a name="indexed-property-design"></a>Dizinli özellik tasarımı

 Dizinli bir özellik, parametrelere sahip olabilecek ve dizi dizine benzer özel söz dizimi ile çağrılabilen özel bir özelliktir.

 Dizinli özellikler genellikle Dizin oluşturucular olarak adlandırılır. Dizin oluşturucular yalnızca bir mantıksal koleksiyondaki öğelere erişim sağlayan API 'lerde kullanılmalıdır. Örneğin, bir dize bir karakter koleksiyonudur ve üzerindeki Dizin Oluşturucu, <xref:System.String?displayProperty=nameWithType> kendi karakterlerine erişmek için eklenmiştir.

 ✔️, iç dizide depolanan verilere erişim sağlamak için Dizin oluşturucular kullanmayı düşünün.

 ✔️ öğe koleksiyonlarını temsil eden türlerde Dizin oluşturucular sağlamayı düşünün.

 ❌ Birden fazla parametreli dizinli Özellikler kullanmaktan KAÇıNıN.

 Tasarım birden çok parametre gerektiriyorsa, özelliğin bir mantıksal koleksiyona bir erişimciyi temsil edip etmediğini yeniden düşünün. Yoksa, bunun yerine yöntemleri kullanın. Veya ile yöntem adını başlatmayı düşünün `Get` `Set` .

 ❌ ,,, <xref:System.Int32?displayProperty=nameWithType> <xref:System.Int64?displayProperty=nameWithType> <xref:System.String?displayProperty=nameWithType> Veya enum dışında parametre türlerine sahip dizin oluşturuculardan kaçının <xref:System.Object?displayProperty=nameWithType> .

 Tasarımda diğer parametre türleri gerekiyorsa, API 'nin mantıksal bir koleksiyona bir erişimciyi temsil edip etmediğini kesin olarak yeniden değerlendirin. Değilse, bir yöntemi kullanın. Veya ile yöntem adını başlatmayı düşünün `Get` `Set` .

 ✔️, `Item` açıkça daha iyi bir ad olmadıkça, dizinli özellikler için adı kullanın (ör., <xref:System.String.Chars%2A> özelliği üzerinde bkz. `System.String` ).

 C# ' de, Dizin oluşturucular varsayılan olarak adlandırılmış öğedir. <xref:System.Runtime.CompilerServices.IndexerNameAttribute>Bu adı özelleştirmek için kullanılabilir.

 ❌ Hem bir Dizin Oluşturucu hem de anlamsal olarak eşdeğer Yöntemler sağlamaın.

 ❌ Bir tür içinde birden fazla aşırı yüklenmiş Dizin Oluşturucu sağlamaktan biridir.

 Bu, C# derleyicisi tarafından zorlanır.

 ❌ Varsayılan olmayan dizinli özellikleri kullanmayın.

 Bu, C# derleyicisi tarafından zorlanır.

### <a name="property-change-notification-events"></a>Özellik değişiklik bildirimi olayları

 Bazen bir özellik değerindeki değişiklikleri kullanıcıya bildiren bir olay sağlamak yararlı olur. Örneğin, `System.Windows.Forms.Control` `TextChanged` özelliğinin değeri değiştirildikten sonra bir olay oluşturur `Text` .

 ✔️, üst düzey API 'lerde (genellikle Tasarımcı bileşenleri) özellik değerleri değiştirildiğinde değişiklik bildirimi olaylarını yükseltmeyi göz önünde bulundurun.

 Bir kullanıcının bir nesnenin özelliğinin ne zaman değiştiğini bilmesini sağlamak için iyi bir senaryo varsa, nesne özellik için bir değişiklik bildirimi olayı tetiklemelidir.

 Bununla birlikte, temel türler veya Koleksiyonlar gibi alt düzey API 'Ler için bu tür olayları yükseltme yüküyle ilgili ek yükün olması düşüktür. Örneğin, <xref:System.Collections.Generic.List%601> listeye yeni bir öğe eklendiğinde ve özelliği değiştiğinde bu tür olayları oluşturmaz `Count` .

 ✔️, bir özelliğin değeri dış güçlerle değiştirildiğinde değişiklik bildirimi olaylarını yükseltmeyi göz önünde bulundurun.

 Bir özellik değeri, bazı dış zorlanarak (nesne üzerinde Yöntemler çağırma dışında bir şekilde) değişirse, olay oluşturma, geliştiricinin değerin değiştiğini ve değiştiğini gösterir. `Text`Bir metin kutusu denetiminin özelliği iyi bir örnektir. Kullanıcı öğesine metin yazdığında `TextBox` , özellik değeri otomatik olarak değişir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
