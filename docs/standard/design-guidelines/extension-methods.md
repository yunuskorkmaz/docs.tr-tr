---
title: Uzantı Metotları
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 77c012d7838ae2fa1f62163bc58520db67c64ce5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289765"
---
# <a name="extension-methods"></a>Genişletme yöntemleri

Uzantı yöntemleri, statik yöntemlerin örnek yöntemi çağırma söz dizimi kullanılarak çağrılmasına izin veren bir dil özelliğidir. Bu yöntemler, yöntemin üzerinde çalışacağı örneği temsil eden en az bir parametre almalıdır.

 Bir genişletme yöntemini tanımlayan sınıf, "sponsor" sınıfı olarak adlandırılır ve olarak bildirilmelidir `static` . Uzantı yöntemlerini kullanmak için, sponsor sınıfı tanımlayan ad alanını içeri aktarmanız gerekir.

 ❌Özellikle sahip olmadığınız türler üzerinde uzantı yöntemlerinin aşırı kullanımını ÖNLEYIN.

 Bir türün kaynak kodunu yaptıysanız bunun yerine normal örnek yöntemleri kullanmayı düşünün. Kaynak koduna sahip değilseniz ve bir yöntem eklemek istiyorsanız, çok dikkatli olun. Uzantı yöntemlerinin serbest kullanımı, bu yöntemlere sahip olmak için tasarlanmamış türlerin karışıklık API 'Lerinin potansiyelini içerir.

 ✔️ Aşağıdaki senaryolardan birinde uzantı yöntemlerini kullanmayı göz önünde bulundurun:

- Bir arabirimin her uygulamasıyla ilgili yardımcı işlevsellik sağlamak için, Eğer işlevin çekirdek arabirim açısından yazılabilmesini sağlar. Bunun nedeni, somut uygulamaların arabirime atanamadığı bir şekilde yapılamaz. Örneğin, LINQ to Objects işleçleri tüm türler için uzantı yöntemleri olarak uygulanır <xref:System.Collections.Generic.IEnumerable%601> . Bu nedenle, herhangi bir `IEnumerable<>` uygulama otomatik olarak LINQ etkindir.

- Bir örnek yöntemi, bazı tür için bir bağımlılık tanıtacaksa, ancak böyle bir bağımlılık, bağımlılık yönetimi kurallarını kesintiye uğratır. Örneğin, öğesinden bir bağımlılığı <xref:System.String> <xref:System.Uri?displayProperty=nameWithType> muhtemelen istenmez ve bu nedenle `String.ToUri()` döndürülen örnek yöntemi `System.Uri` bir bağımlılık yönetimi perspektifinden yanlış tasarım olacaktır. Döndüren statik bir genişletme `Uri.ToUri(this string str)` yöntemi `System.Uri` çok daha iyi bir tasarım olacaktır.

 ❌Uzantı yöntemlerini tanımlamaktan KAÇıNıN <xref:System.Object?displayProperty=nameWithType> .

 Visual Basic kullanıcılar uzantı yöntemi sözdizimini kullanarak nesne başvuruları üzerinde bu yöntemleri çağıramayacak. Visual Basic, bir başvurunun bildirilmesi, `Object` onun üzerinde tüm Yöntem çağrılarını kapanmaya zorlar (Bu, çağrılan gerçek üyenin çalışma zamanında belirlendiği anlamına gelir). Uzantı yöntemlerine bağlama, derleme zamanında (erken bağlantı) belirlenir.

 Bu kılavuz, aynı bağlama davranışının bulunduğu veya uzantı yöntemlerinin desteklenmediği diğer diller için geçerlidir.

 ❌Arayüzlere veya bağımlılık yönetimine Yöntemler eklenmediği sürece uzantı yöntemlerini genişletilmiş türle aynı ad alanına yerleştirmeyin.

 ❌Farklı ad alanlarında bulunsa bile, aynı imzaya sahip iki veya daha fazla genişletme yöntemi tanımlamaktan KAÇıNıN.

 ✔️, tür bir arabirim ise ve uzantı yöntemlerinin çoğu durumda veya tüm durumlarda kullanılması amaçlanan uzantı yöntemlerini genişletilmiş türle tanımlamayı düşünün.

 ❌Genellikle diğer özelliklerle ilişkili ad alanlarında bir özelliği uygulayan uzantı yöntemlerini tanımlamayın. Bunun yerine, bunları ait oldukları özellikle ilişkili ad alanı içinde tanımlayın.

 ❌Uzantı yöntemlerine adanmış ad alanlarının genel olarak adlandırılmasını ÖNLEYIN (ör. "Uzantılar"). Bunun yerine açıklayıcı bir ad (örneğin, "yönlendirme") kullanın.

 *Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
