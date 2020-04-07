---
title: Delegeler ve olaylar
description: Temsilciler ve olaylar arasındaki farkı ve .NET Core'un bu özelliklerinin her birini ne zaman kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 51d982c9b5b16a5fc28ede5f0318bc100bb33b68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805759"
---
# <a name="distinguishing-delegates-and-events"></a>Temsilcileri ve Olayları Ayırt Etme

[Önceki](modern-events.md)

.NET Core platformuna yeni gelen geliştiriciler, bir tasarıma `delegates` dayalı ve temelli bir tasarım arasında karar verirken genellikle mücadele ederler. `events` İki dil özelliği benzer olduğundan, temsilci veya olay seçimi genellikle zordur. Etkinlikler, temsilciler için dil desteği kullanılarak bile oluşturulur.

Her ikisi de geç bağlama senaryosu sunar: bileşenin yalnızca çalışma zamanında bilinen bir yöntemi çağırarak iletişim kurduğu senaryoları etkinleştirir. Her ikisi de tek ve birden çok abone yöntemini destekler. Bunu tek döküm ve çok noktaya yayın desteği olarak adlandırabilirsiniz. Her ikisi de işleyicileri eklemek ve kaldırmak için benzer sözdizimini destekler. Son olarak, bir olay yükselterek ve bir temsilci arama tam olarak aynı yöntem sözdizimi arayın kullanın. Hatta her ikisi `Invoke()` de `?.` işleç ile kullanmak için aynı yöntem sözdizimini destekler.

Tüm bu benzerlikler ile, hangi kullanmak için ne zaman belirlemekte sorun olması kolaydır.

## <a name="listening-to-events-is-optional"></a>Olayları Dinlemek İsteğe Bağlıdır

Hangi dil özelliğinin kullanılacağını belirlemede en önemli husus, bağlı bir abonenin olup olmaması gerektiğidir. Kodunuz abone tarafından sağlanan kodu aramanız gerekiyorsa, temsilcilere dayalı bir tasarım kullanmanız gerekir. Kodunuz tüm çalışmasını herhangi bir abone çağırmadan tamamlayabiliyorsa, olaylara dayalı bir tasarım kullanmalısınız.

Bu bölümde oluşturulmuş örnekleri göz önünde bulundurun. Öğeleri düzgün bir `List.Sort()` şekilde sıralamak için, kullanarak oluşturduğun koda bir karşılayıcı işlevi verilmelidir. Hangi öğelerin döndürüleceğini belirlemek için LINQ sorguları temsilcilerle birlikte sağlanmalıdır. Her ikisi de delegelerle oluşturulmuş bir tasarım kullandı.

Olayı `Progress` göz önünde bulundurun. Bir görevde ilerleme yi tirenleri bildirir.
Herhangi bir dinleyici olup olmadığı görev devam ediyor.
Başka `FileSearcher` bir örnektir. Yine de arama ve hiçbir olay aboneleri ekli bile, aranan tüm dosyaları bulmak.
Olayları dinleyen abone ler olmasa bile UX denetimleri hala doğru çalışır. Her ikisi de olaylara dayalı tasarımlar kullanır.

## <a name="return-values-require-delegates"></a>İade Değerleri Temsilciler Gerektirir

Başka bir husus, temsilci yönteminiz için isteyeceğiniz yöntem prototipidir. Gördüğünüz gibi, olaylar için kullanılan temsilcilerin hepsinin geçersiz bir dönüş türü vardır. Ayrıca, olay bağımsız değişken nesnesinin özelliklerini değiştirerek bilgileri olay kaynaklarına geri aktaran olay işleyicileri oluşturmak için deyimler olduğunu da gördünüz. Bu deyimler işe yarasa da, bir yöntemden değer döndürmek kadar doğal değildir.

Bu iki buluşçistin her ikisinin de genellikle mevcut olabileceğine dikkat edin: Temsilci yönteminiz bir değer döndürürse, algoritmayı bir şekilde etkileme olasılığı yüksektir.

## <a name="events-have-private-invocation"></a>Etkinlikler Özel Çağrı var

Bir olayın bulunduğu sınıf dışındaki sınıflar yalnızca olay dinleyicileri ekleyebilir ve kaldırabilir; yalnızca olayı içeren sınıf olayı çağırabilir. Olaylar genellikle ortak sınıf üyeleridir.
Buna karşılık, temsilciler genellikle parametre olarak geçirilir ve hiç depolanırsa özel sınıf üyesi olarak depolanır.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Etkinlik Dinleyicilerinin Genellikle Daha Uzun Ömürleri Var

Bu olay dinleyiciler daha uzun ömürleri var biraz daha zayıf bir gerekçedir. Ancak, olay kaynağı uzun bir süre boyunca olayları yükseltecek zaman olay tabanlı tasarımlar daha doğal olduğunu görebilirsiniz. Birçok sistemde UX denetimleri için olay tabanlı tasarım örneklerini görebilirsiniz. Bir etkinliğe abone olduktan sonra, etkinlik kaynağı programın ömrü boyunca olayları yükseltebilir.
(Artık ihtiyacınız olmadığında etkinliklerden aboneliğinizi kaldırabilirsiniz.)

Bir temsilcinin bir yönteme bağımsız değişken olarak kullanıldığı ve bu yöntem döndürüldikten sonra temsilcinin kullanılmadığı birçok temsilci tabanlı tasarımla karşılamayın.

## <a name="evaluate-carefully"></a>Dikkatle Değerlendirin

Yukarıdaki hususlar sert ve hızlı kurallar değildir. Bunun yerine, belirli kullanımınız için hangi seçeneğin en iyi olduğuna karar vermenize yardımcı olabilecek bir kılavuztemsil ederler. Benzer oldukları için, hatta her ikisini de prototip ve çalışmak için daha doğal olacağını düşünebilirsiniz. Her ikisi de geç bağlama senaryoları iyi ele. Tasarımınızı en iyi şekilde ileten tasarımıkullanın.
