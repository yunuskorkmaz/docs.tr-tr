---
title: Özellik Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: e4ed4fd39a9ebd63b9d5dbff38dc15647d65934f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026327"
---
# <a name="property-design"></a>Özellik Tasarımı
Özellikleri teknik yöntemlere benzer olsa da, bunlar kendi kullanım senaryoları açısından oldukça farklıdır. Bunlar, akıllı alanları olarak başlatmasında gösterilmelidir. Alanları arama söz dizimi ve yöntemleri esnekliğini sahiptirler.  
  
 **✓ DO** çağıran özelliğin değerini değiştirmek açmaması gereken, yalnızca get özellikleri oluşturun.  
  
 Türü olmadığını aklınızda bulundurun özelliği kesilebilir başvuru türü, özellik değeri salt alma özelliği olsa bile değiştirilebilir.  
  
 **X DO NOT** alıcı daha geniş erişilebilirlik sahip ayarlayıcı yalnızca küme özellikleri veya özellikleri sağlar.  
  
 Örneğin, özellikler, genel bir Ayarlayıcısı ve korumalı bir alıcı ile kullanmayın.  
  
 Özellik Get yordamı sağlanan, bir yöntem işlevselliği bunun yerine uygulayın. Yöntem adı ile başlamayı düşünün `Set` ne özelliği adlı ile izleyin. Örneğin, <xref:System.AppDomain> adlı bir yöntem olan `SetCachePath` adlı yalnızca kümesi özelliği yerine `CachePath`.  
  
 **✓ DO** tüm özellikleri, varsayılan bir güvenlik açığı veya çok verimsiz kodu yol açmamasını sağlamak için duyarlı varsayılan değerler sağlayın.  
  
 **✓ DO** bu nesne bir geçici geçersiz durumda sonuçları olsa bile herhangi bir sırada ayarlanacak özellikler izin verir.  
  
 Aynı nesne üzerinde diğer özelliklerin değerlerine burada bazı özellik değerlerini geçersiz olabilir bir noktaya birbiriyle ilişkili iki veya daha fazla özelliklerini yaygındır. Birbiriyle ilişkili özellikleri gerçekten birlikte nesne tarafından kullanılan kadar bu gibi durumlarda, geçersiz durumdan kaynaklanan özel durumları ertelenebiliyorsa.  
  
 **✓ DO** özellik set yordamı bir özel durum oluşturursa önceki değeri korumak.  
  
 **X AVOID** özellik alıcıları özel durumları atma.  
  
 Özellik alıcılar basit işlemler olmalıdır ve tüm önkoşullara sahip olmamalıdır. Bir alıcı bir özel durum oluşturabilecek, bir yöntem için büyük olasılıkla tasarlanması gerekir. Bu kural, dizin oluşturucular, bağımsız değişkenleri doğrulamak sonucunda özel durumlar nerede bekliyoruz uygulanmaz dikkat edin.  
  
### <a name="indexed-property-design"></a>Dizinlenmiş özellik tasarımı  
 Dizini oluşturulmuş özelliğe parametrelerine sahip olabilir ve dizi dizini oluşturma için benzer bir özel sözdizimi ile çağrılabilen özel bir özelliktir.  
  
 Dizinli Özellikler, dizin oluşturucular yaygın olarak adlandırılır. Dizin oluşturucular mantıksal bir koleksiyondaki öğelerin erişim sağlayan API kullanılmalıdır. Örneğin, bir dizi karakter ve dizin oluşturucusunda bir dize olan <xref:System.String?displayProperty=nameWithType> kendi karakterlerin erişmek için eklendi.  
  
 **✓ CONSIDER** iç dizisinde depolanan verilere erişim sağlamak için dizin oluşturucular kullanma.  
  
 **✓ CONSIDER** öğe koleksiyonunu temsil eden türlerinde dizin oluşturucular sağlama.  
  
 **X AVOID** dizin oluşturulmuş özellikleri birden fazla parametresiyle kullanarak.  
  
 Tasarım birden çok parametre gerektiriyorsa, özelliğin gerçekten mantıksal bir koleksiyon için bir erişimci temsil edip etmediğini yeniden belirleyin. Kullanmıyorsa, bunun yerine yöntemlerini kullanın. Yöntem adı ile başlamayı düşünün `Get` veya `Set`.  
  
 **X AVOID** dışında parametre türleri oluşturucularla <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, veya enum.  
  
 Diğer parametre türleri tasarımı gerektiriyorsa, API, gerçekten erişimci mantıksal bir koleksiyonu temsil edip etmediğini kesinlikle yeniden değerlendir. Kullanmıyorsa, bir yöntem kullanın. Yöntem adı ile başlamayı düşünün `Get` veya `Set`.  
  
 **✓ DO** adını kullanın `Item` için tabii daha iyi bir adı olmadıkça özellikleri dizine (örn., bkz: <xref:System.String.Chars%2A> özellikte `System.String`).  
  
 C# ' ta adlı öğe varsayılan dizin oluşturucular özelliklere. <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Bu ad özelleştirmek için kullanılabilir.  
  
 **X DO NOT** hem bir dizin oluşturucu hem de anlam olarak eşdeğerdir yöntemleri sağlar.  
  
 **X DO NOT** aşırı yüklenmiş dizin oluşturucular bir türde birden fazla ailesi sağlayın.  
  
 Bu, C# Derleyici tarafından zorlanır.  
  
 **X DO NOT** kullanım varsayılan olmayan dizin oluşturulmuş özellikleri.  
  
 Bu, C# Derleyici tarafından zorlanır.  
  
### <a name="property-change-notification-events"></a>Özellik değişikliği bildirimi olayları  
 Bazı durumlarda kullanıcı bir özellik değeri değişiklikleri bildiren bir olay sağlamak kullanışlıdır. Örneğin, `System.Windows.Forms.Control` başlatır bir `TextChanged` olayından sonra değerini kendi `Text` özelliği değişti.  
  
 **✓ CONSIDER** değişiklik üst düzey API'leri (genellikle Tasarımcı bileşenleri) özellik değerlerinde değişiklik yapıldığında bildirim olayları oluşturma.  
  
 Bir nesnenin bir özelliğini ne zaman değişiyor bilmek, bir kullanıcı için iyi bir senaryo ise, nesne özelliği için bir değişikliği bildirim olayı harekete geçirmelidir.  
  
 Ancak, bu tür taban türler veya koleksiyonları gibi alt düzey API'ler için olay yükü değer olması beklenmez. Örneğin, <xref:System.Collections.Generic.List%601> yeni bir öğe listesine eklendiğinde bu tür olayların oluşturmaz ve `Count` özellik değişiklikleri.  
  
 **✓ CONSIDER** değişiklik bir özelliğin değerini dış zorlar değiştiğinde bildirim olayları oluşturma.  
  
 Bazı dış zorla (bir yolla nesne üzerinde yöntemleri çağırarak dışında) aracılığıyla bir özellik değeri değişirse yükseltmek olayları göstermek için geliştirici değer değişiyor ve değişti. İyi bir örnektir `Text` metin kutusu denetimi özelliği. Kullanıcının yazdığı metni ne zaman bir `TextBox`, özellik değeri otomatik olarak değiştirir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
