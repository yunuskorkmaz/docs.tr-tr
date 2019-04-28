---
title: Temsilcileri ve olayları ayırt etme
description: Temsilciler ve olaylar ve .NET Core, bu özelliklerin her birini kullanmak ne zaman arasındaki farkı öğrenin.
ms.date: 06/20/2016
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 2f9c26519d93314f4991829191723df5426b23b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646650"
---
# <a name="distinguishing-delegates-and-events"></a>Temsilcileri ve olayları ayırt etme

[Önceki](modern-events.md)

Genellikle .NET Core platformu için yeni olan geliştiriciler, temel bir tasarım arasında karar olduğunda uğraşır `delegates` ve temel bir tasarım `events`. İki dil özellikleri oldukça benzerdir zor bir kavram olmasıdır. Olaylar, temsilciler için dil desteği kullanılarak bile oluşturulur. 

Her ikisi de geç bağlama senaryo sunar: bir bileşen iletişim kuran burada yalnızca çalışma zamanında bilinen bir yöntem çağırarak senaryoları tanırlar. Her ikisi de tek ve birden çok abone yöntemleri destekler. Bu singlecast olarak adlandırılır ve çok noktaya yayın desteği bulabilirsiniz. Her ikisi de benzer bir söz dizimi ekleme ve kaldırma işleyicileri için destek. Son olarak, bir olayı tetiklenmeden ve temsilci çağırma tam olarak aynı yöntem çağrı sözdizimini kullanın. Her ikisi de bile aynı destekleyen `Invoke()` yöntem sözdizimi ile kullanılmak üzere `?.` işleci.

Bu benzerlikler ile hangisi ne zaman kullanılmalıdır belirleme konusunda sorun yaşıyorsanız kolaydır.

## <a name="listening-to-events-is-optional"></a>İsteğe bağlı olduğunda olayları dinleme

Ekli bir abonesi olmalıdır desteklemediğini kullanmak için hangi dil özelliği belirlemede en önemli husustur. Kodunuzu abone tarafından sağlanan kod çağırmanız gerekir, temsilciler üzerinde temel bir tasarım kullanmanız gerekir. Tüm iş herhangi aboneleri çağırmaya gerek kalmadan kodunuzu tamamlayabilirsiniz etkinliklere göre bir tasarım kullanmanız gerekir. 

Bu bölümde sırasında oluşturulan örneklere bakın. Yerleşik kullanarak kod `List.Sort()` öğeleri doğru sıralamak için bir karşılaştırıcı işlevi verilmelidir. LINQ sorguları ile temsilciler döndürmek için hangi öğelere belirleyebilmesi sağlanmalıdır. Her ikisi de temsilci ile oluşturulmuş bir tasarım kullanılır.

Göz önünde bulundurun `Progress` olay. Bu görevde ilerlemeyi raporlar.
Görev var olup olmadığını tüm dinleyiciler devam etmek devam eder.
`FileSearcher` Başka bir örnektir. Yine de arama ve hatta bağlı hiçbir olay aboneliği olan Aranan tüm dosyaları bulur.
Olayları dinleme abone olduğunda bile UX denetimleri yine de düzgün çalışır. Her ikisi de etkinliklere göre tasarımları kullanın.

## <a name="return-values-require-delegates"></a>Dönüş değerleri temsilciler gerektirir

Temsilci yönteminizi istersiniz yöntemi prototip başka bir husustur. Gördüğünüz gibi tüm olaylar için kullanılan temsilci bir dönüş türü void olacak. Ayrıca, olay bağımsız değişkeni nesnesinin özelliklerini değiştirme aracılığıyla geri olay kaynakları için bilgi geçirmek olay işleyicilerini oluşturma deyimleri olduğunu gördünüz. Bu deyimleri çalışırken, bu doğal olarak bir yöntemi bir değer döndüren olarak değiller.

Bu iki buluşsal yöntemler genellikle her ikisi de mevcut olabileceğine dikkat edin: Bir temsilci yöntemi bir değer döndürüyorsa, algoritma bir şekilde büyük olasılıkla etkiler.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Olay dinleyicilerini genellikle daha uzun ömre sahip 

Biraz daha zayıf bir gerekçe budur. Ancak, uzun bir süre olayları olay kaynağı oluşturma, olay tabanlı tasarımları daha doğal olduğunu fark edebilirsiniz. Örnekler için UX denetimleri birçok sistemlerinde görebilirsiniz. Olay kaynağı, bir olaya abone olduktan sonra programın ömrü boyunca olayları neden olabilir.
(Artık ihtiyacınız olduğunda olayları abonelikten çıkabilirsiniz.)

Bir temsilci yöntemi için bağımsız değişken olarak kullanıldığı, çok sayıda temsilci tabanlı tasarımlar ile karşıtlık ve bu yöntemin dönüşünün ardından temsilci kullanılmaz.

## <a name="evaluate-carefully"></a>Dikkatlice değerlendirin

Yukarıdaki konuları sabit ve hızlı kurallar değildir. Bunun yerine, hangi belirli kullanımınız için en iyi seçimdir karar vermenize yardımcı olabilecek bir kılavuz gösterir. Benzer olduklarından, her iki prototip bile ve hangi çalışmak için daha doğal olacaktır göz önünde bulundurun. Her ikisi de geç bağlama senaryoları da işler. Tasarımınızı iletişim kuran bir en iyi kullanın.
