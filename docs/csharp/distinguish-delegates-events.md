---
title: Temsilciler ve olaylar
description: Temsilciler ve olaylar arasındaki farkı ve .NET Core 'un bu özelliklerinin her birini ne zaman kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 193a9b0fe0e0c36deb6552449c92135057412225
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414675"
---
# <a name="distinguishing-delegates-and-events"></a>Temsilcileri ve Olayları Ayırt Etme

[Önceki](modern-events.md)

.NET Core platformunda yeni olan geliştiriciler, temel olarak bir tasarıma ve tasarımına göre karar verirken çok daha fazla zaman harcamaya uğraşır `delegates` `events` . İki dil özelliği de benzer olduğundan, temsilci veya olay seçimi genellikle zordur. Olaylar, temsilciler için dil desteği kullanılarak bile oluşturulur.

Her ikisi de bir geç bağlama senaryosu sunar: yalnızca çalışma zamanında bilinen bir yöntemi çağırarak bir bileşenin iletişim kurduğu senaryolara olanak tanır. Her ikisi de tek ve birden çok abone yöntemini destekler. Bu şekilde, tekcast ve çok noktaya yayın desteği olarak adlandırılan bulabilirsiniz. Bunlar her ikisi de işleyicileri eklemek ve kaldırmak için benzer sözdizimini destekler. Son olarak, bir olayı oluşturup bir temsilciyi çağırmak, tam olarak aynı yöntem çağrısı söz dizimini kullanır. Her ikisi de `Invoke()` işleçle birlikte kullanmak için aynı yöntem söz dizimini destekler `?.` .

Bu benzerlikler sayesinde ne zaman kullanacağınızı belirlemek oldukça kolaydır.

## <a name="listening-to-events-is-optional"></a>Olayları dinlemek Isteğe bağlıdır

Hangi dil özelliğinin kullanılacağını belirlemede en önemli nokta, eklenen bir abone olmalıdır. Kodunuzun abone tarafından sağlanan kodu çağırması gerekiyorsa, geri çağırma uygulamanız gerektiğinde temsilcilere dayalı bir tasarım kullanmanız gerekir. Kodunuz herhangi bir abone çağrılmadan tüm işlerini tamamlayabiliyorsanız, olaylara dayalı bir tasarım kullanmanız gerekir.

Bu bölüm sırasında oluşturulan örnekleri göz önünde bulundurun. Kullanılarak oluşturduğunuz koda, `List.Sort()` öğeleri doğru bir şekilde sıralamak için bir karşılaştırıcı işlevi verilmelidir. Hangi öğelerin döneceğini belirlemek için temsilcilerle LINQ sorgularının sağlanması gerekir. Her ikisi de temsilcilerle oluşturulmuş bir tasarım kullandı.

Olayı göz önünde bulundurun `Progress` . Bir görevde ilerlemeyi raporlar.
Görev, herhangi bir dinleyici olup olmadığına bakılmaksızın devam etmeye devam eder.
`FileSearcher`Başka bir örnektir. Hiçbir olay abonesi ekli olmasa bile, aranan tüm dosyaları arayabilir ve bulur.
UX denetimleri, olayları dinleyen bir abone olmadığında bile hala düzgün çalışır. Bunlar her ikisi de olayları temel alan tasarımlar kullanır.

## <a name="return-values-require-delegates"></a>Dönüş değerleri temsilciler gerektiriyor

Temsilci yönteminiz için istediğiniz yöntem prototipi başka bir noktadır. Gördüğünüz gibi, olaylar için kullanılan temsilcilerin void dönüş türü vardır. Ayrıca, olay bağımsız değişkeni nesnesinin özelliklerini değiştirerek olayları olay kaynaklarına geri geçiren olay işleyicileri oluşturmak için ıoms olduğunu da gördünüz. Bu IBU deyimler çalışırken, bir yöntemden değer döndürürken doğal olarak değildir.

Bu iki buluşsal yöntemin her ikisi de mevcut olabilir: temsilci yönteminiz bir değer döndürürse, bu durum büyük olasılıkla algoritmayı bir şekilde etkiler.

## <a name="events-have-private-invocation"></a>Olayların özel çağrısı var

Bir olayın bulunduğu bir olay dışındaki sınıflar yalnızca olay dinleyicileri ekleyebilir ve kaldırabilir; Yalnızca olayı içeren sınıf olayı çağırabilir. Olaylar genellikle ortak sınıf üyeleridir.
Bir karşılaştırma yaparak, temsilciler genellikle parametre olarak geçirilir ve özel sınıf üyeleri olarak depolanır.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Olay dinleyicileri genellikle daha uzun ömürleri vardır

Bu olay dinleyicilerinin süreleri daha uzun bir süre daha zayıf. Ancak olay tabanlı tasarımların olay kaynağı uzun bir süre boyunca olayları oluştururken daha doğal olduğunu fark edebilirsiniz. Birçok sistemde, UX denetimleri için olay tabanlı tasarımın örneklerini görebilirsiniz. Bir olaya abone olduktan sonra olay kaynağı, programın kullanım ömrü boyunca olayları oluşturabilir.
(Artık ihtiyaç kalmadığında olayları abonelikten kaldırabilirsiniz.)

Bir temsilcinin bir yönteme bağımsız değişken olarak kullanıldığı birçok temsilci tabanlı tasarım ile, bu yöntem, bu yöntemin döndürdüğü süre dolduktan sonra kullanılmlarından farklıdır.

## <a name="evaluate-carefully"></a>Dikkatle değerlendirin

Yukarıdaki konular sabit ve hızlı kurallar değildir. Bunun yerine, belirli kullanımınız için en uygun seçeneği belirlemenize yardımcı olabilecek Kılavuzu temsil ederler. Benzer olduklarından, her ikisini de prototip yapabilir ve bununla birlikte çalışmak için ne kadar doğal olacağını düşünün. Bunlar her ikisi de geç bağlama senaryolarını de işler. Tasarımınızı en iyi şekilde iletişim kuran birini kullanın.
