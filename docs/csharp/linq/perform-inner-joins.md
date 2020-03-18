---
title: İç birleştirmeleri gerçekleştirin (C#'da LINQ)
description: C#'da LINQ'u kullanarak iç birleştirmeleri nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: a3e8e9bd97ec630797bc48a3302b27ed45d9103e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659845"
---
# <a name="perform-inner-joins"></a>İç birleşimler gerçekleştirme

İlişkisel veritabanı terimlerinde, *iç birleştirme,* ilk koleksiyonun her öğesinin ikinci koleksiyondaki her eşleşen öğe için bir kez göründüğü bir sonuç kümesi üretir. İlk koleksiyondaki bir öğeeşleşen öğe yoksa, sonuç kümesinde görünmez. C#'daki <xref:System.Linq.Enumerable.Join%2A> `join` yan tümceyle çağrılan yöntem, bir iç birleştirme uygular.

Bu makalede, bir iç birleştirme dört varyasyonları gerçekleştirmek için nasıl gösterir:

- Basit bir anahtara dayalı olarak iki veri kaynağındaki öğeleri ilişkilendiren basit bir iç birleştirme.

- *Bileşik* anahtara dayalı iki veri kaynağındaki öğeleri ilişkilendiren bir iç birleştirme. Birden fazla değerden oluşan bir anahtar olan bileşik anahtar, birden fazla özelliği temel alan öğeleri ilişkilendirmenizi sağlar.

- Birbirini izleyen birleştirme işlemlerinin birbirine eklendiği *birden çok birleştirme.*

- Grup birleşimi kullanılarak uygulanan bir iç birleştirme.

## <a name="example---simple-key-join"></a>Örnek - Basit tuş birleştirme

Aşağıdaki örnek, kullanıcı tanımlı iki türnesneleri içeren iki `Person` koleksiyon `Pet`oluşturur ve. Sorgu c# `join` tümcesini nesneleri `Person` nesneleri `Pet` olan `Owner` nesnelerle `Person`eşleştirmek için kullanır. C# yan `select` tümcesi, elde edilen nesnelerin nasıl görüneceğini tanımlar. Bu örnekte ortaya çıkan nesneler, sahibinin adı ve evcil hayvanın adını oluşturan anonim türleridir.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

"Huff" `Person` olan `LastName` nesnenin sonuç kümesinde görünmediğini, çünkü `Pet` buna `Pet.Owner` `Person`eşit olan bir nesne olmadığını unutmayın.

## <a name="example---composite-key-join"></a>Örnek - Kompozit tuşu birleştirme

Öğeleri tek bir özelliğe dayalı ilişkilendirmek yerine, birden çok özelliğe dayalı öğeleri karşılaştırmak için bileşik bir anahtar kullanabilirsiniz. Bunu yapmak için, karşılaştırmak istediğiniz özelliklerden oluşan anonim bir türü döndürmek için her koleksiyon için anahtar seçici işlevini belirtin. Özellikleri etiketlerseniz, her anahtarın anonim türünde aynı etikete sahip olmaları gerekir. Özellikler de aynı sırada görünmelidir.

Aşağıdaki örnekte, hangi `Employee` çalışanların da öğrenci `Student` olduğunu belirlemek için nesnelerin listesi ve nesnelerin listesi kullanır. Bu tür her `FirstName` ikisi `LastName` de bir <xref:System.String>ve türü bir özelliği vardır. Her listenin öğelerinden birleştirme anahtarlarını oluşturan işlevler, her `FirstName` öğenin ve `LastName` özelliklerinden oluşan anonim bir tür döndürür. Birleştirme işlemi, eşitlik için bu bileşik anahtarları karşılaştırır ve hem ad hem de soyadının eşleştiği her listeden nesne çiftleri döndürür.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Örnek - Çoklu birleştirme

Birden çok birleştirme işlemi gerçekleştirmek için birbirinin yanına eklenebilir. C#'daki her `join` yan tümce, belirli bir veri kaynağını önceki birleştirme nin sonuçlarıyla ilişkilendirer.

Aşağıdaki örnekte üç koleksiyon oluşturulur: `Person` nesnelerin listesi, `Cat` nesnelerin listesi ve `Dog` nesnelerin listesi.

C#'daki ilk `join` tümce, eşleşen `Person` bir `Cat.Owner`nesneye göre kişilerle kedilerle eşleşir. Nesneyi ve `Person` `Cat.Name`.

`join` C#'daki ikinci tümce, ilk olarak verilen köpekler `Dog` listesindeki nesnelerle birlikte döndürülen anonim türleri, türün `Owner` `Person`özelliğinden ve hayvanadının ilk harfinden oluşan bileşik anahtara dayalı olarak ilişkilendirer. Her eşleşen çiftin `Cat.Name` özelliklerini ve özelliklerini `Dog.Name` içeren bir dizi anonim türü döndürür. Bu bir iç birleştirme olduğundan, yalnızca ikinci veri kaynağında eşleşme sayılsa ilk veri kaynağındaki nesneler döndürülür.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Örnek - Gruplanmış birleştirme kullanarak iç birleştirme

Aşağıdaki örnek, bir grup birleştirme kullanarak bir iç birleştirme nasıl uygulanacağını gösterir.

In, `query1` `Person` nesnelerin listesi `Pet` `Person` grup eşleşen `Pet.Owner` özelliğine dayalı nesneler listesine katıldı. Grup birleştirme, her grubun bir `Person` nesne ve eşleşen `Pet` nesnelerden oluşan bir diziden oluştuğu ara gruplardan oluşan bir koleksiyon oluşturur.

Sorguya ikinci `from` bir yan tümce eklenerek, bu dizi dizisi daha uzun bir dizide birleştirilir (veya düzleştirilmiştir). Son sıranın öğelerinin türü yan tümcetarafından `select` belirtilir. Bu örnekte, bu tür, her eşleşen `Person.FirstName` `Pet.Name` çift için ve özellikleri nden oluşan anonim bir türüdür.

Bunun `query1` sonucu, bir iç birleştirme gerçekleştirmek için `join` `into` yan tümcesi kullanılarak elde edilen sonuç kümesine eşdeğerdir. `query2` Değişken bu eşdeğer sorguyu gösterir.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Gruplanmış birleşimler gerçekleştirme](perform-grouped-joins.md)
- [Sol dış birleşimler gerçekleştirme](perform-left-outer-joins.md)
- [Anonim türleri](../programming-guide/classes-and-structs/anonymous-types.md)
