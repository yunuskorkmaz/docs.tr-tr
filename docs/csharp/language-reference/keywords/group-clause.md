---
title: group tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 8e3ddea3ba733cb9ba32e510b050a58407a7a477
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404521"
---
# <a name="group-clause-c-reference"></a>group tümcesi (C# Başvurusu)

`group` Yan tümcesi bir dizi döndürür <xref:System.Linq.IGrouping%602> grubu için anahtar değerle eşleşen sıfır veya daha fazla öğe içeren nesne. Örneğin, bir dizi dize her bir dizenin ilk harfini göre gruplandırabilirsiniz. Bu durumda, ilk harfi anahtarı ve bir türe sahip [char](char.md)ve depolanan `Key` her özellik <xref:System.Linq.IGrouping%602> nesne. Derleyicinin anahtar türünü çıkarsar.

Bir sorgu ifadesi ile sona erdirebilirsiniz bir `group` yan tümcesi, aşağıdaki örnekte gösterildiği gibi:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Her grupta ek sorgu işlemleri gerçekleştirmek istiyorsanız, kullanarak geçici bir tanımlayıcı belirtebilirsiniz [içine](into.md) bağlamsal anahtar sözcük. Kullanırken `into`, devam edip sonunda ile son bir `select` deyimi veya başka bir `group` aşağıdaki alıntıda gösterildiği yan tümcesi:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Daha da kullanımı örnekleri'ni tamamlamak `group` olmadan `into` bu makalede örnek bölümünde sağlanır.

## <a name="enumerating-the-results-of-a-group-query"></a>Bir grup sorgunun sonuçlarını numaralandırma

Çünkü <xref:System.Linq.IGrouping%602> nesneleri tarafından üretilen bir `group` sorgu temelde listelerinin bir listesini, iç içe bir kullanmalısınız [foreach](foreach-in.md) döngü her gruptaki öğeleri erişmek için. Dış döngü Grup anahtarları yinelenir ve iç döngü gruptaki her öğe üzerinde yinelenir. Bir grubu, bir anahtar vardır, ancak hiçbir öğe olabilir. Aşağıdaki `foreach` önceki kod örneklerinde Sorguyu yürüten döngü:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Anahtar türü

Gibi bir dize, bir yerleşik sayısal tür veya kullanıcı tanımlı tür veya anonim tür adlı Grup anahtarları herhangi bir tür olabilir.

### <a name="grouping-by-string"></a>Dizeye göre gruplandırma

Yukarıdaki kod örnekleri kullanılan bir `char`. Bir dize anahtarı kolayca bunun yerine, örneğin tam son adı belirtilmedi:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Bool göre gruplandırma

Aşağıdaki örnek, sonuçları iki gruplara bölmek bir anahtar için bir bool değeri kullanımını gösterir. Bir alt ifadenin, değerini oluşturduğu Not `group` yan tümcesi.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Sayısal Aralık göre gruplandırma

Sonraki örnek, bir dilim aralığı temsil eden sayısal Grup anahtarları oluşturmak için bir ifade kullanır. Kullanımına dikkat edin [izin](let-clause.md) yöntemini iki kez çağırmak zorunda kalmazsınız bir yöntem depolamak için uygun bir konum arama sonucu, `group` yan tümcesi. Ayrıca unutmayın `group` "sıfıra" özel durumdan kaçınmak için kod Öğrenci sıfır ortalama sahip olmadığından emin olmak için kontrol eder, yan tümcesi. Güvenli bir şekilde sorgu ifadelerinde yöntemleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Sorgu ifadelerinde özel durumları işlemek](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Bileşik anahtarlara göre gruplandırma

Birden fazla anahtar göre grup öğeleri için istediğiniz zaman bir bileşik anahtarı kullanın. Bileşik anahtar, anahtar öğesi tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak oluşturun. Aşağıdaki örnekte, varsayımında bir sınıf `Person` adlı üye ile bildirilmiş `surname` ve `city`. `group` Yan tümcesi kişilerin son aynı ada ve aynı şehirdeki her bir kümesi için oluşturulacak farklı bir grup neden olur.

```csharp
group person by new {name = person.surname, city = person.city};
```

Sorgu değişkeni başka yönteme geçirin, adlandırılmış bir tür kullanın. Otomatik uygulanan özellikler anahtarlarını kullanarak özel bir sınıf oluşturun ve daha sonra geçersiz <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemleri. Bu durumda, kesin olarak bu yöntemleri geçersiz kılmanız gerekmez, bir yapı de kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir basit sınıf Implemented Properties ile uygulama](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [nasıl yapılır: bir dizin ağacındaki yinelenen dosyalar için sorgu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Sonraki makalede, türü adlandırılmış bir bileşik anahtarı kullanmayı gösteren bir kod örneği bulunur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hiçbir ek sorgu mantıksal gruplara uygulandığında gruplar halinde kaynak verileri sıralama için standart deseni gösterir. Bu, bir devamlılık olmadan bir gruplandırma olarak adlandırılır. Dizelerden oluşan bir dizi öğeleri, ilk harfi göre gruplandırılır. Sorgu sonucu bir <xref:System.Linq.IGrouping%602> içeren genel bir tür `Key` türünün özelliği `char` ve <xref:System.Collections.Generic.IEnumerable%601> gruplandırma her öğe içeren koleksiyon.

Sonucu bir `group` yan tümcesi ise sıralarının. Bu nedenle, döndürülen her grup içindeki tek tek öğelerine erişmek için bir iç içe kullanın `foreach` Grup anahtarları, aşağıdaki örnekte gösterildiği gibi yinelenen döngü içinde döngü.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Örnek

Bu örnek gösterir kullanarak bunları oluşturduktan sonra ek mantık gruplarında gerçekleştirmek nasıl bir *devamlılık* ile `into`. Daha fazla bilgi için [içine](into.md). Aşağıdaki örnek, her grup, yalnızca anahtar değeri olan bir sesli seçmek için sorgular.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında `group` yan tümceleri çevrilmiş çağrıları içine <xref:System.Linq.Enumerable.GroupBy%2A> yöntemi.

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.Linq.IGrouping%602>  
<xref:System.Linq.Enumerable.GroupBy%2A>  
<xref:System.Linq.Enumerable.ThenBy%2A>  
<xref:System.Linq.Enumerable.ThenByDescending%2A>  
[Sorgu Anahtar Sözcükleri](query-keywords.md)  
[Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)  
[İç içe geçmiş grup oluşturma](../../linq/create-a-nested-group.md)  
[Sorgu sonuçlarını gruplandırma](../../linq/group-query-results.md)  
[Gruplandırma işleminde alt sorgu gerçekleştirme](../../linq/perform-a-subquery-on-a-grouping-operation.md)