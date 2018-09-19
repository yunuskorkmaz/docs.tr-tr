---
title: (C# üzerinde LINQ) iç birleştirmeler gerçekleştirme
description: C# içinde LINQ kullanarak iç birleştirmeler gerçekleştirme konusunda bilgi edinin.
ms.date: 12/1/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: 2f6aad30dc8278ce1bb88bacc19b27deaa0288c7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991416"
---
# <a name="perform-inner-joins"></a>İç birleştirmeler gerçekleştirme

İlişkisel veritabanı koşullarında bir *INNER JOIN* bir sonuç kümesi her hangi bir öğedeki ilk koleksiyonun ikinci koleksiyon eşleşen her öğe için bir kez görünür üretir. İlk koleksiyondaki bir öğe eşleşen bir öğe varsa, sonuç kümesinde görünmüyor. <xref:System.Linq.Enumerable.Join%2A> Tarafından çağrılan yöntem `join` yan tümcesinde C# ' ta, bir iç birleştirme uygular.

Bu makalede, dört çözümlenmeyebileceği iç birleşim gerçekleştirme gösterir:

- Basit bir anahtarına göre iki veri kaynağı öğelerinden karşılık gelen basit bir iç birleştirme.

- İki veri kaynaklarından alınan öğeleri karşılık gelen bir iç birleştirme temel alan bir *bileşik* anahtarı. Birden fazla değerini içeren bir anahtarı olan bir bileşik anahtarı birden fazla özelliğe dayalı öğeleri bağıntısını kurmanızı sağlar.

- A *birden fazla birleşim* hangi art arda gelen birleştirme işlemleri birbirine eklenir.

- Bir iç birleştirme group JOIN kullanılarak gerçekleştirilir.

## <a name="example---simple-key-join"></a>Örnek - basit anahtar birleştirme

Aşağıdaki örnek, iki tür, kullanıcı tanımlı nesneler içeren iki koleksiyonları oluşturur `Person` ve `Pet`. Sorgu kullanan `join` yan tümcesinde eşleştirmek için C# `Person` nesnelerini `Pet` ayarlanmış nesneleri `Owner` olan `Person`. `select` Yan tümcesinde C#, elde edilen nesnelerin nasıl görüneceğini tanımlar. Bu örnekte, sonuçta elde edilen sahibinin adı ve Evcil hayvanınızın adı oluşur anonim türler nesneleridir.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

Unutmayın `Person` nesnesi `LastName` "Huff" sonuç olduğundan kümesine görünmez olduğundan hiçbir `Pet` nesnesi `Pet.Owner` eşit `Person`.

## <a name="example---composite-key-join"></a>Örnek - bileşik anahtar birleştirme

Öğeleri yalnızca bir özelliğe dayalı bağıntı yerine birden fazla özelliğe göre öğeleri karşılaştırılacak bir bileşik anahtarı kullanabilirsiniz. Bunu yapmak için karşılaştırmak istediğiniz özellikleri içeren bir anonim tür dönmek her bir koleksiyon için anahtar Seçici işlevi belirtin. Özellikleri etiketi, aynı etiketi her anahtarın anonim türünde olmalıdır. Özellikleri de aynı sırada yer almalıdır.

Aşağıdaki örnek, bir listesini kullanır `Employee` nesneleri ve listesini `Student` hangi çalışanların da Öğrenciler olduğunu belirlemek için nesneleri. Bu tür hem de bir `FirstName` ve `LastName` türünün özelliği <xref:System.String>. Join anahtarlar her listenin öğeleri oluşturan işlevler içeren bir anonim bir tür döndürür `FirstName` ve `LastName` her öğenin özellikleri. Birleştirme işlemi, bu bileşik anahtarlar eşitliği karşılaştırır ve hem ad ve Soyadı eşleştiği her listeden çiftleri nesne döndürür.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Örnek - birden çok birleştirme

Herhangi bir sayıda birleştirme işlemleri birden fazla birleşim gerçekleştirmek için birbirlerine eklenmiş. Her `join` yan tümcesinde C# belirtilen veri kaynağı önceki birleştirme sonuçlarının ile ilişkilendirir.

Aşağıdaki örnek, üç koleksiyonu oluşturur: bir listesini `Person` nesneleri, listesini `Cat` nesneleri ve listesini `Dog` nesneleri.

İlk `join` yan tümcesinde C#, kişiler ve temel kediler eşleşen bir `Person` nesne eşleşen `Cat.Owner`. Bir dizi içeren bir anonim türleri döndürür `Person` nesne ve `Cat.Name`.

İkinci `join` yan tümcesinde C# ile ilk birleşimi tarafından döndürülen anonim türler karşılık gelen `Dog` köpekler, sağlanan listesi nesneleri içeren bir bileşik anahtarı tabanlı `Owner` türünün özelliği `Person`ilk Harf donatarak'ın adı. Bir dizi içeren bir anonim türleri döndürür `Cat.Name` ve `Dog.Name` eşleşen her çift özellikleri. Bu bir iç birleştirme olduğundan, yalnızca bir eşleşme ikinci veri kaynağına sahip ilk veri kaynağı nesnelerden döndürülür.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Örnek - kullanarak iç birleştirmesi birleştirme gruplandırılır.

Aşağıdaki örnek bir iç birleştirme group JOIN uygulamak gösterilmektedir.

İçinde `query1`, listesini `Person` nesneleri, Grup katılmış listesine `Pet` nesneleri temel alarak `Person` eşleşen `Pet.Owner` özelliği. Grup birleştirme olduğu her grubu oluşur Ara grubun bir koleksiyonunu oluşturur bir `Person` nesne ve sıralamadaki eşleşen `Pet` nesneleri.

İkinci ekleyerek `from` dizileri bu dizi sorgu yan tümcesinin birleştirilmiş (veya düzleştirilmiş) bir uzun dizi. Son sırasının öğelerin türü tarafından belirtilen `select` yan tümcesi. Bu örnekte, türü içeren bir anonim tür olduğunu `Person.FirstName` ve `Pet.Name` eşleşen her çift özellikleri.

Sonucu `query1` kullanılarak elde sonuç kümesi eşdeğerdir `join` yan tümcesi olmadan `into` iç birleşim gerçekleştirmek için yan tümcesi. `query2` Eşdeğer bu sorgu değişkeni gösterir.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [Gruplanmış birleşimler gerçekleştirme](perform-grouped-joins.md)  
- [Sol dış birleştirmeler gerçekleştirme](perform-left-outer-joins.md)  
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)  