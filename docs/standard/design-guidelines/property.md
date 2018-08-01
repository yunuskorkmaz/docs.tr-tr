---
title: Özellik Tasarım
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a4aec965753fe8f89b8bd89469f8dc5739a6a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577115"
---
# <a name="property-design"></a>Özellik Tasarım
Özellikler teknik olarak yöntemlere çok benzer olmakla birlikte, bunların kullanım senaryoları açısından oldukça farklı. Akıllı alanlar olarak görülmelidir. Alanları arama söz dizimi ve yöntemleri esnekliğini sahiptirler.  
  
 **✓ DO** çağıran özelliğin değerini değiştirmek açmaması gereken, yalnızca get özellikleri oluşturun.  
  
 Olması durumunda türünü unutmayın özelliği kesilebilir başvuru türü, özellik değeri yalnızca get olsa bile özellik değiştirilebilir.  
  
 **X DO NOT** alıcı daha geniş erişilebilirlik sahip ayarlayıcı yalnızca küme özellikleri veya özellikleri sağlar.  
  
 Örneğin, özellikler, ortak bir Ayarlayıcısı ve korumalı bir alıcı ile kullanmayın.  
  
 Özellik alıcısı sağlanamaz, bunun yerine işlevi bir yöntem olarak uygular. Yöntem adı ile başlayan göz önünde bulundurun `Set` ve ne özelliği adlı ile izleyin. Örneğin, <xref:System.AppDomain> sahip olarak adlandırılan bir yöntem `SetCachePath` adlı yalnızca kümesi özelliğine sahip yerine `CachePath`.  
  
 **✓ DO** tüm özellikleri, varsayılan bir güvenlik açığı veya çok verimsiz kodu yol açmamasını sağlamak için duyarlı varsayılan değerler sağlayın.  
  
 **✓ DO** bu nesne bir geçici geçersiz durumda sonuçları olsa bile herhangi bir sırada ayarlanacak özellikler izin verir.  
  
 Diğer özelliklerin değerlerine aynı nesne üzerinde verilen burada bir özelliğin bazı değerler geçersiz olabilir bir noktasına birbiriyle ilişkili olarak iki veya daha fazla özellik yaygındır. Birbiriyle ilişkili özellikler gerçekte birlikte nesne tarafından kullanılan kadar bu gibi durumlarda, özel durumlar geçersiz durumdan kaynaklanan Ertelenen.  
  
 **✓ DO** özellik set yordamı bir özel durum oluşturursa önceki değeri korumak.  
  
 **X AVOID** özellik alıcıları özel durumları atma.  
  
 Özellik alıcıları basit işlemler olmalıdır ve tüm önkoşullara sahip olmamalıdır. Bir alıcı bir özel durum, bir yöntem için büyük olasılıkla tasarlanması gerekir. Bu kural dizin oluşturucular, bağımsız değişkenler doğrulama sonucu olarak özel durumlar burada bekliyoruz uygulanmaz dikkat edin.  
  
### <a name="indexed-property-design"></a>Dizin oluşturulmuş özellik Tasarım  
 Dizinli bir özelliği, parametreleri ve bir dizi dizin oluşturma için benzer özel bir sözdizimi ile çağrılabilir özel bir özelliğidir.  
  
 Dizinli Özellikler, yaygın olarak dizin oluşturucular da adlandırılır. Dizin Oluşturucular, mantıksal bir koleksiyondaki öğelerin erişim sağlayan API'lerde kullanılmalıdır. Örneğin, bir dizeyi karakter ve oluşturucuda koleksiyonudur <xref:System.String?displayProperty=nameWithType> kendi karakter erişmek için eklendi.  
  
 **✓ CONSIDER** iç dizisinde depolanan verilere erişim sağlamak için dizin oluşturucular kullanma.  
  
 **✓ CONSIDER** öğe koleksiyonunu temsil eden türlerinde dizin oluşturucular sağlama.  
  
 **X AVOID** dizin oluşturulmuş özellikleri birden fazla parametresiyle kullanarak.  
  
 Tasarım birden çok parametre gerektiriyorsa, özellik, bir erişimci gerçekten mantıksal bir koleksiyonu temsil eder. olup olmadığını alan. Yoksa, bunun yerine yöntemlerini kullanın. Yöntem adı ile başlayan göz önünde bulundurun `Get` veya `Set`.  
  
 **X AVOID** dışında parametre türleri oluşturucularla <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, veya enum.  
  
 Tasarım diğer türleri parametre gerektiriyorsa, API, erişimci gerçekten mantıksal bir koleksiyonu temsil eder. olup olmadığını kesinlikle yeniden. Yoksa, bir yöntem kullanın. Yöntem adı ile başlayan göz önünde bulundurun `Get` veya `Set`.  
  
 **✓ DO** adını kullanın `Item` için tabii daha iyi bir adı olmadıkça özellikleri dizine (örn., bkz: <xref:System.String.Chars%2A> özellikte `System.String`).  
  
 C# ' ta dizin oluşturucular öğesi adlı varsayılan olarak gelir. <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Bu adını özelleştirmek için kullanılabilir.  
  
 **X DO NOT** hem bir dizin oluşturucu hem de anlam olarak eşdeğerdir yöntemleri sağlar.  
  
 **X DO NOT** aşırı yüklenmiş dizin oluşturucular bir türde birden fazla ailesi sağlayın.  
  
 Bu, C# Derleyici tarafından zorlanır.  
  
 **X DO NOT** kullanım varsayılan olmayan dizin oluşturulmuş özellikleri.  
  
 Bu, C# Derleyici tarafından zorlanır.  
  
### <a name="property-change-notification-events"></a>Özellik değişikliği bildirim olayı  
 Bazen bir özellik değeri değişiklikleri kullanıcı bildiren bir olay sağlamak yararlıdır. Örneğin, `System.Windows.Forms.Control` başlatır bir `TextChanged` olayından sonra değerini kendi `Text` özelliği değişti.  
  
 **✓ CONSIDER** değişiklik üst düzey API'leri (genellikle Tasarımcı bileşenleri) özellik değerlerinde değişiklik yapıldığında bildirim olayları oluşturma.  
  
 Bir kullanıcının ne zaman bir nesnenin bir özelliğini değiştirme bilmek iyi bir senaryo ise, nesnenin bir özellik için bir değişiklik bildirimi olayı tetiklemelidir.  
  
 Ancak, temel türleri veya koleksiyon gibi alt düzey API'ler için bu gibi olaylar yükseltmek için ek yükü değerinde olması olası değil. Örneğin, <xref:System.Collections.Generic.List%601> listesine yeni bir öğe eklendiğinde bu gibi olaylar oluşturmaz ve `Count` özellik değişikliği.  
  
 **✓ CONSIDER** değişiklik bir özelliğin değerini dış zorlar değiştiğinde bildirim olayları oluşturma.  
  
 Bazı dış yürürlükte (nesne üzerinde yöntemleri çağırarak bir yol dışında) aracılığıyla bir özellik değeri değişiklikleri olursa olayları belirtmek için geliştirici değeri değişen ve değişti. İyi bir örnektir `Text` metin kutusu denetiminin özelliği. Ne zaman kullanıcı türleri metinde bir `TextBox`, özellik değeri otomatik olarak değiştirir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
