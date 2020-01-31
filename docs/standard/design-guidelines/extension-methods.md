---
title: Genişletme Yöntemleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 13f92470b23d138e0d30bed947ff1932f2605d28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741616"
---
# <a name="extension-methods"></a>Genişletme Yöntemleri
Uzantı yöntemleri, statik yöntemlerin örnek yöntemi çağırma sözdizimi kullanılarak çağrılmasına izin veren bir dil özelliğidir. Bu yöntemler, yöntemin üzerinde çalışacağı örneği temsil eden en az bir parametre almalıdır.

 Bu tür uzantı yöntemlerini tanımlayan sınıf "sponsor" sınıfı olarak adlandırılır ve statik olarak bildirilmelidir. Uzantı yöntemlerini kullanmak için, bir tane sponsor sınıfı tanımlayan ad alanını içeri aktarmanız gerekir.

 ❌, özellikle sahip olmadığınız türler üzerinde uzantı yöntemlerini tanımlamayı frivolously ÖNLEYIN.

 Bir türün kaynak kodunu yaptıysanız bunun yerine normal örnek yöntemleri kullanmayı düşünün. Sahip değilseniz ve bir yöntem eklemek istiyorsanız, çok dikkatli olun. Uzantı yöntemlerinin serbest kullanımı, bu yöntemlere sahip olmak için tasarlanmamış türlerin karışıklık API 'Lerinin potansiyelini içerir.

 ✔️ Aşağıdaki senaryolardan birinde uzantı yöntemlerini kullanmayı göz önünde bulundurun:

- Bir arabirimin her uygulamasıyla ilgili yardımcı işlevsellik sağlamak için, Eğer işlevin çekirdek arabirim açısından yazılabilmesini sağlar. Bunun nedeni, somut uygulamaların arabirime atanamadığı bir şekilde yapılamaz. Örneğin, `LINQ to Objects` işleçleri tüm <xref:System.Collections.Generic.IEnumerable%601> türleri için uzantı yöntemleri olarak uygulanır. Bu nedenle, tüm `IEnumerable<>` uygulamaları otomatik olarak LINQ etkindir.

- Bir örnek yöntemi, bazı tür için bir bağımlılık tanıtacaksa, ancak böyle bir bağımlılık, bağımlılık yönetimi kurallarını kesintiye uğratır. Örneğin, <xref:System.String> <xref:System.Uri?displayProperty=nameWithType> bir bağımlılığı muhtemelen istenmez ve bu nedenle `System.Uri` döndüren `String.ToUri()` örnek yöntemi bir bağımlılık yönetimi perspektifinden yanlış tasarım olacaktır. `Uri.ToUri(this string str)` bir statik genişletme yöntemi, `System.Uri` döndürmek çok daha iyi bir tasarım olacaktır.

 ❌ <xref:System.Object?displayProperty=nameWithType>uzantı yöntemleri tanımlamaktan KAÇıNıN.

 Visual Basic kullanıcılar uzantı yöntemi sözdizimini kullanarak nesne başvuruları üzerinde bu yöntemleri çağıramayacak. Visual Basic, nesne olarak bir başvuru bildirmek, bu tür yöntemlerin çağrılmasını desteklemez, çünkü bu, Visual Basic içinde, bir başvurunun tüm yöntem etkinleştirmeleri geç bağlı (çalışma zamanında belirlenir), genişletme yöntemlerine bağlamalar şurada belirlenir: derleme zamanı (erken bağlantılı).

 Kılavuz, aynı bağlama davranışının bulunduğu ya da uzantı yöntemlerinin desteklenmediği diğer dillere uygulanacağını unutmayın.

 ❌, arayüzlere veya bağımlılık yönetimine Yöntemler eklemek için olmadığı sürece, genişletme yöntemlerini genişletilmiş türle aynı ad alanına yerleştirmeyin.

 farklı ad alanlarında olsalar bile, aynı imzaya sahip iki veya daha fazla genişletme yöntemi tanımlamaktan KAÇıNıN. ❌

 ✔️, tür bir arabirim ise ve uzantı yöntemlerinin çoğu durumda veya tüm durumlarda kullanılması amaçlanan uzantı yöntemlerini genişletilmiş türle tanımlamayı düşünün.

 ❌, normal olarak diğer özelliklerle ilişkili ad alanlarında özellik uygulayan uzantı yöntemlerini tanımlamaz. Bunun yerine, bunları ait oldukları özellikle ilişkili ad alanı içinde tanımlayın.

 ❌ uzantı yöntemlerine adanmış ad alanlarının genel olarak adlandırılmasını ÖNLEYIN (ör. "Uzantılar"). Bunun yerine açıklayıcı bir ad (örneğin, "yönlendirme") kullanın.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
