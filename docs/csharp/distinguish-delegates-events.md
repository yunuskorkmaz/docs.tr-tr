---
title: Temsilcileri ve Olayları Ayırt Etme
description: Temsilciler ve olaylar arasındaki farkı ve .NET Core 'un bu özelliklerinin her birini ne zaman kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: ff90af1d2b1a92f06eed58228f8e8ca5ff6b93ca
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037315"
---
# <a name="distinguishing-delegates-and-events"></a>Temsilcileri ve Olayları Ayırt Etme

[Öncekini](modern-events.md)

.NET Core platformunda yeni olan geliştiriciler, `events`dayalı bir tasarıma `delegates` ve tasarımı temel alan bir tasarım arasında karar verirken çok daha fazla zaman harcamaya uğraşır. Bu zor bir kavramdır, çünkü iki dil özelliği çok benzerdir. Olaylar, temsilciler için dil desteği kullanılarak bile oluşturulur. 

Her ikisi de bir geç bağlama senaryosu sunar: yalnızca çalışma zamanında bilinen bir yöntemi çağırarak bir bileşenin iletişim kurduğu senaryolara olanak tanır. Her ikisi de tek ve birden çok abone yöntemini destekler. Bu şekilde, tekcast ve çok noktaya yayın desteği olarak adlandırılan bulabilirsiniz. Bunlar her ikisi de işleyicileri eklemek ve kaldırmak için benzer sözdizimini destekler. Son olarak, bir olayı oluşturup bir temsilciyi çağırmak, tam olarak aynı yöntem çağrısı söz dizimini kullanır. Her ikisi de `?.` işleci ile kullanmak için aynı `Invoke()` yöntemi sözdizimini destekler.

Bu benzerlikler sayesinde ne zaman kullanacağınızı belirlemek oldukça kolaydır.

## <a name="listening-to-events-is-optional"></a>Olayları dinlemek Isteğe bağlıdır

Hangi dil özelliğinin kullanılacağını belirlemede en önemli nokta, eklenen bir abone olmalıdır. Kodunuzun abone tarafından sağlanan kodu çağırması gerekiyorsa, temsilcileri temel alan bir tasarım kullanmanız gerekir. Kodunuz herhangi bir abone çağrılmadan tüm işlerini tamamlayabiliyorsanız, olaylara dayalı bir tasarım kullanmanız gerekir. 

Bu bölüm sırasında oluşturulan örnekleri göz önünde bulundurun. `List.Sort()` kullanarak oluşturduğunuz koda, öğeleri doğru bir şekilde sıralamak için bir karşılaştırıcı işlevi verilmelidir. Hangi öğelerin döneceğini belirlemek için temsilcilerle LINQ sorgularının sağlanması gerekir. Her ikisi de temsilcilerle oluşturulmuş bir tasarım kullandı.

`Progress` olayını göz önünde bulundurun. Bir görevde ilerlemeyi raporlar.
Görev, herhangi bir dinleyici olup olmadığına bakılmaksızın devam etmeye devam eder.
`FileSearcher` başka bir örnektir. Hiçbir olay abonesi ekli olmasa bile, aranan tüm dosyaları arayabilir ve bulur.
UX denetimleri, olayları dinleyen bir abone olmadığında bile hala düzgün çalışır. Bunlar her ikisi de olayları temel alan tasarımlar kullanır.

## <a name="return-values-require-delegates"></a>Dönüş değerleri temsilciler gerektiriyor

Temsilci yönteminiz için istediğiniz yöntem prototipi başka bir noktadır. Gördüğünüz gibi, olaylar için kullanılan temsilcilerin void dönüş türü vardır. Ayrıca, olay bağımsız değişkeni nesnesinin özelliklerini değiştirerek olayları olay kaynaklarına geri geçiren olay işleyicileri oluşturmak için ıoms olduğunu da gördünüz. Bu IBU deyimler çalışırken, bir yöntemden değer döndürürken doğal olarak değildir.

Bu iki buluşsal yöntemin her ikisi de mevcut olabilir: temsilci yönteminiz bir değer döndürürse, bu durum büyük olasılıkla algoritmayı bir şekilde etkiler.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Olay dinleyicileri genellikle daha uzun ömürleri vardır 

Bu biraz daha zayıf bir gerekçe. Ancak olay tabanlı tasarımların olay kaynağı uzun bir süre boyunca olayları oluştururken daha doğal olduğunu fark edebilirsiniz. Birçok sistemde UX denetimleri için bunun örneklerini görebilirsiniz. Bir olaya abone olduktan sonra olay kaynağı, programın kullanım ömrü boyunca olayları oluşturabilir.
(Artık ihtiyaç kalmadığında olayları abonelikten kaldırabilirsiniz.)

Bir temsilcinin bir yönteme bağımsız değişken olarak kullanıldığı birçok temsilci tabanlı tasarım ile, bu yöntem, bu yöntemin döndürdüğü süre dolduktan sonra kullanılmlarından farklıdır.

## <a name="evaluate-carefully"></a>Dikkatle değerlendirin

Yukarıdaki konular sabit ve hızlı kurallar değildir. Bunun yerine, belirli kullanımınız için en uygun seçeneği belirlemenize yardımcı olabilecek Kılavuzu temsil ederler. Benzer olduklarından, her ikisini de prototip yapabilir ve bununla birlikte çalışmak için ne kadar doğal olacağını düşünün. Bunlar her ikisi de geç bağlama senaryolarını de işler. Tasarımınızı en iyi şekilde iletişim kuran birini kullanın.
