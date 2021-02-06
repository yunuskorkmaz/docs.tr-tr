---
description: 'Daha fazla bilgi edinin: uzantı yöntemleri'
title: Uzantı Metotları
ms.date: 10/22/2008
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 2f71ec86252045687558bd61337164ac3afbcd20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642064"
---
# <a name="extension-methods"></a>Uzantı Metotları

Uzantı yöntemleri, statik yöntemlerin örnek yöntemi çağırma sözdizimi kullanılarak çağrılmasına izin veren bir dil özelliğidir. Bu yöntemler, yöntemin üzerinde çalışacağı örneği temsil eden en az bir parametre almalıdır.

 Bu tür uzantı yöntemlerini tanımlayan sınıf "sponsor" sınıfı olarak adlandırılır ve statik olarak bildirilmelidir. Uzantı yöntemlerini kullanmak için, bir tane sponsor sınıfı tanımlayan ad alanını içeri aktarmanız gerekir.

 ❌ Özellikle sahip olmadığınız türler üzerinde uzantı yöntemlerini tanımlamayı frivolously KAÇıNıN.

 Bir türün kaynak kodunu yaptıysanız bunun yerine normal örnek yöntemleri kullanmayı düşünün. Sahip değilseniz ve bir yöntem eklemek istiyorsanız, çok dikkatli olun. Uzantı yöntemlerinin serbest kullanımı, bu yöntemlere sahip olmak için tasarlanmamış türlerin karışıklık API 'Lerinin potansiyelini içerir.

 ✔️ Aşağıdaki senaryolardan birinde uzantı yöntemlerini kullanmayı göz önünde bulundurun:

- Bir arabirimin her uygulamasıyla ilgili yardımcı işlevsellik sağlamak için, Eğer işlevin çekirdek arabirim açısından yazılabilmesini sağlar. Bunun nedeni, somut uygulamaların arabirime atanamadığı bir şekilde yapılamaz. Örneğin, `LINQ to Objects` işleçler tüm türler için uzantı yöntemleri olarak uygulanır <xref:System.Collections.Generic.IEnumerable%601> . Bu nedenle, herhangi bir `IEnumerable<>` uygulama otomatik olarak LINQ etkindir.

- Bir örnek yöntemi, bazı tür için bir bağımlılık tanıtacaksa, ancak böyle bir bağımlılık, bağımlılık yönetimi kurallarını kesintiye uğratır. Örneğin, öğesinden bir bağımlılığı <xref:System.String> <xref:System.Uri?displayProperty=nameWithType> muhtemelen istenmez ve bu nedenle `String.ToUri()` döndürülen örnek yöntemi `System.Uri` bir bağımlılık yönetimi perspektifinden yanlış tasarım olacaktır. Döndüren statik bir genişletme `Uri.ToUri(this string str)` yöntemi `System.Uri` çok daha iyi bir tasarım olacaktır.

 ❌ Uzantı yöntemlerini tanımlamaktan KAÇıNıN <xref:System.Object?displayProperty=nameWithType> .

 VB kullanıcıları, uzantı yöntemi sözdizimini kullanarak nesne başvuruları üzerinde bu tür yöntemleri çağıramayacak. VB, nesne olarak bir başvuru bildirmek, bu tür yöntemlerin çağrılmasını desteklemez, çünkü VB 'de, nesne üzerinde tüm yöntem etkinleştirmeleri, geç bağlama olur (çağrılan gerçek üye çalışma zamanında belirlenir), genişletme yöntemlerine bağlamalar derleme zamanı (erken bağlantı) sırasında belirlenir.

 Kılavuz, aynı bağlama davranışının bulunduğu ya da uzantı yöntemlerinin desteklenmediği diğer dillere uygulanacağını unutmayın.

 ❌ Arayüzlere veya bağımlılık yönetimine Yöntemler eklenmediği sürece uzantı yöntemlerini genişletilmiş türle aynı ad alanına yerleştirmeyin.

 ❌ Farklı ad alanlarında bulunsa bile, aynı imzaya sahip iki veya daha fazla genişletme yöntemi tanımlamaktan KAÇıNıN.

 ✔️, tür bir arabirim ise ve uzantı yöntemlerinin çoğu durumda veya tüm durumlarda kullanılması amaçlanan uzantı yöntemlerini genişletilmiş türle tanımlamayı düşünün.

 ❌ Genellikle diğer özelliklerle ilişkili ad alanlarında bir özelliği uygulayan uzantı yöntemlerini tanımlamayın. Bunun yerine, bunları ait oldukları özellikle ilişkili ad alanı içinde tanımlayın.

 ❌ Uzantı yöntemlerine adanmış ad alanlarının genel olarak adlandırılmasını ÖNLEYIN (ör. "Uzantılar"). Bunun yerine açıklayıcı bir ad (örneğin, "yönlendirme") kullanın.

 *Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
