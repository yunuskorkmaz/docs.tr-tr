---
title: Temsilciler ve olaylar ayrım
description: Temsilciler ve olaylar ve ne zaman .NET Core, bu özelliklerin her biri kullanılacağı arasındaki fark hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 2f9c26519d93314f4991829191723df5426b23b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="distinguishing-delegates-and-events"></a>Temsilciler ve olaylar ayrım

[Önceki](modern-events.md)

Genellikle .NET Core platformuna yeni geliştiriciler güçlük arasında bir tasarıma karar temel `delegates` ve temel tasarım `events`. İki dil özellikleri çok benzer zor bir kavram olmasıdır. Olayları bile temsilciler için dil desteği kullanılarak oluşturulur. 

Her ikisi de geç bağlama senaryosu sunar: bir bileşeni iletişim kurar burada yalnızca çalışma zamanında bilinen bir yöntemini çağırarak senaryoları etkinleştirin. Her ikisi de tek ve birden çok abone yöntemleri destekler. Bu singlecast olarak da adlandırılır ve çok noktaya yayın desteği bulabilirsiniz. Her ikisi de benzer sözdizimi ekleme ve kaldırma işleyicileri için destek. Son olarak, bir olay oluşturma ve bir temsilci çağırma tam olarak aynı yöntemi çağrı sözdizimini kullanın. Her ikisi de bile aynı destek `Invoke()` yöntem sözdizimi ile kullanılmak üzere `?.` işleci.

Bu benzerlikler ile ne zaman hangi kullanılacağını belirleme güçlük kolaydır.

## <a name="listening-to-events-is-optional"></a>İsteğe bağlı olduğunda olayları dinleme

Ekli abone olmalıdır desteklemediğini kullanmak için hangi dil özelliği belirlemede en önemli noktadır. Kodunuzu abone tarafından sağlanan kod çağırmalısınız yetkililer dayalı bir tasarım kullanmanız gerekir. Kodunuzu, tüm aboneler çağırmadan tüm çalışmasını tamamlayabilir olaylara dayanarak bir tasarım kullanmanız gerekir. 

Bu bölümde sırasında oluşturulan örneklere bakın. Yerleşik kullanarak kod `List.Sort()` düzgün öğeleri sıralamak için bir karşılaştırıcı işlevi verilmelidir. LINQ sorgularını döndürmek için hangi öğelerin belirlemek için temsilciler ile sağlanmalıdır. Her ikisi de temsilciler ile yerleşik bir tasarım kullanılır.

Göz önünde bulundurun `Progress` olay. İlerleme görevde rapor.
Görev vardır olup olmadığına bakılmaksızın tüm dinleyiciler devam etmek devam eder.
`FileSearcher` Başka bir örnektir. Hala arama ve bile bağlı hiçbir olay aboneleri ile Aranan tüm dosyaları bulur.
Olayları dinleme abone olduğunda bile UX denetimleri hala düzgün çalışır. Her ikisi de olaylara dayanarak tasarımları kullanın.

## <a name="return-values-require-delegates"></a>Dönüş değerleri temsilciler gerektirir

Temsilci yönteminizi istersiniz yöntemi prototip başka bir konudur. Gördüğünüz gibi tüm olaylar için kullanılan temsilciler geçersiz bir dönüş türüne sahip. Ayrıca, bilgileri olay bağımsız değişkeni nesnenin özelliklerini değiştirme aracılığıyla geri olay kaynakları için kullandıkları olay işleyicileri oluşturmak için deyimleri olduğunu gördünüz. Bu deyimleri çalışırken, bu değer bir yöntemden döndürme olarak olarak doğal değiller.

Bu iki buluşsal yöntemler çoğunlukla her ikisi de olabilir, dikkat edin: temsilci yöntemi bir değer döndürürse, büyük olasılıkla algoritması şekilde etkiler.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Olay dinleyicileri genellikle uzun ömürleri vardır 

Biraz daha zayıf bir gerekçe budur. Ancak, uzun bir süre boyunca olaylar olay kaynağı oluşturma, olay tabanlı tasarımları daha doğal olduğunu fark edebilirsiniz. Bu örnek birçok sistemi UX denetimler için görebilirsiniz. Olay kaynağı, bir olaya abone olduktan sonra program ömrü boyunca olayları neden olabilir.
(Artık gereksinim duyduğunuzda olaylarından abonelikten çıkabilirsiniz.)

Burada bir yöntem bağımsız değişkeni olarak bir temsilci kullanıldığında, birçok temsilci tabanlı tasarımı ile karşıtlık ve bu yöntem döndükten sonra temsilci kullanılmaz.

## <a name="evaluate-carefully"></a>Dikkatlice değerlendirin

Yukarıdaki konuları sabit ve hızlı kuralları değildir. Bunun yerine, hangi belirli kullanımınız için en iyi seçimdir karar vermenize yardımcı olabilir Kılavuzu gösterir. Benzer oldukları için prototip hem bile ve bu çalışmak daha doğal olur göz önünde bulundurun. Her ikisi de geç bağlama senaryoları iyi işler. Tasarımınızın iletişim kuran bir en iyi kullanın.
