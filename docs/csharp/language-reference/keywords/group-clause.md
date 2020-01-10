---
title: Group yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713466"
---
# <a name="group-clause-c-reference"></a>group tümcesi (C# Başvurusu)

`group` yan tümcesi, grup için anahtar değeriyle eşleşen sıfır veya daha fazla öğe içeren bir <xref:System.Linq.IGrouping%602> nesneleri dizisi döndürür. Örneğin, her bir dizedeki ilk harfe göre bir dizi dizeyi gruplandırabilirsiniz. Bu durumda, ilk harf anahtardır ve bir tür [char](../builtin-types/char.md)içerir ve her <xref:System.Linq.IGrouping%602> nesnesinin `Key` özelliğinde saklanır. Derleyici, anahtarın türünü haller.

Aşağıdaki örnekte gösterildiği gibi, bir sorgu ifadesini `group` yan tümcesiyle sona erdirmek isteyebilirsiniz:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Her grupta ek sorgu işlemleri gerçekleştirmek [istiyorsanız, ' ın bağlamsal anahtar](into.md) sözcüğünü kullanarak geçici bir tanımlayıcı belirtebilirsiniz. `into`kullandığınızda, sorguyla devam etmeniz ve sonunda aşağıdaki alıntıda gösterildiği gibi bir `select` deyimi veya başka bir `group` yan tümcesiyle sona erdirmek gerekir:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Bu makalenin örnek bölümünde `into` ve olmadan `group` kullanımı için daha kapsamlı örnekler verilmiştir.

## <a name="enumerating-the-results-of-a-group-query"></a>Bir grup sorgusunun sonuçlarını numaralandırma

Bir `group` sorgusu tarafından oluşturulan <xref:System.Linq.IGrouping%602> nesneleri temelde bir liste listesi olduğundan, her bir gruptaki öğelere erişmek için iç içe geçmiş bir [foreach](foreach-in.md) döngüsü kullanmanız gerekir. Dış döngü grup anahtarlarının üzerinde yinelenir ve iç döngü gruptaki her öğe için yinelenir. Bir grupta anahtar olabilir ancak öğe yok. Aşağıda, önceki kod örneklerinde sorguyu yürüten `foreach` döngüsü verilmiştir:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Anahtar türleri

Grup anahtarları dize, yerleşik bir sayısal tür veya Kullanıcı tanımlı adlandırılmış tür veya anonim tür gibi herhangi bir tür olabilir.

### <a name="grouping-by-string"></a>Dizeye göre gruplandırma

Önceki kod örnekleri bir `char`kullandı. Bunun yerine bir dize anahtarı kolayca belirtilmelidir, örneğin, son soyadı adı:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Bool ile gruplandırma

Aşağıdaki örnek, sonuçları iki gruba bölmek için bir anahtar için bool değer kullanımını gösterir. Değerin `group` yan tümcesindeki bir alt ifade tarafından üretildiğini unutmayın.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Sayısal aralığa göre gruplandırma

Sonraki örnek, bir yüzdebirlik aralığını temsil eden sayısal grup anahtarları oluşturmak için bir ifade kullanır. Yöntem çağrı sonucunu depolamak için uygun bir konum olarak [izin ver](let-clause.md) öğesinin kullanımını unutmayın. bu sayede yöntemi `group` yan tümcesinde iki kez çağırmak zorunda kalmazsınız. Sorgu ifadelerinde yöntemleri güvenle kullanma hakkında daha fazla bilgi için bkz. [sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Bileşik anahtarlara göre gruplandırma

Öğeleri birden fazla anahtara göre gruplandırmak istediğinizde bileşik anahtar kullanın. Anahtar öğesini tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak bileşik anahtar oluşturursunuz. Aşağıdaki örnekte, bir sınıf `Person` `surname` ve `city`adlı üyelerle bildirildiği varsayılır. `group` yan tümcesi, aynı soyadı ve aynı şehirde bulunan her kişi kümesi için ayrı bir grubun oluşturulmasına neden olur.

```csharp
group person by new {name = person.surname, city = person.city};
```

Sorgu değişkenini başka bir yönteme geçirmeniz gerekiyorsa adlandırılmış bir tür kullanın. Anahtarlar için otomatik uygulanan özellikler kullanarak özel bir sınıf oluşturun ve ardından <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemlerini geçersiz kılın. Ayrıca, bu yöntemleri kesin bir şekilde geçersiz kılmak zorunda değilsiniz bir yapı da kullanabilirsiniz. Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [bir dizin ağacındaki yinelenen dosyaları sorgulama](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). İkinci makalede, adlandırılmış tür ile bileşik anahtarın nasıl kullanılacağını gösteren bir kod örneği bulunur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, gruplara ek sorgu mantığı uygulanırken kaynak verileri gruplara sıralamak için standart düzeni gösterir. Bu, devamlılık olmadan gruplandırma olarak adlandırılır. Dizeler dizisindeki öğeler, ilk harfine göre gruplandırılır. Sorgunun sonucu, `char` türünde ortak bir `Key` özelliği ve gruplandırmadaki her öğeyi içeren bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu içeren <xref:System.Linq.IGrouping%602> türüdür.

`group` yan tümcesinin sonucu bir dizi dizidir. Bu nedenle, döndürülen her grup içindeki ayrı öğelere erişmek için, aşağıdaki örnekte gösterildiği gibi, döngü içinde, bir iç içe `foreach` döngüsünü kullanın.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Örnek

Bu örnek, `into`ile devam eden bir *devamlılığın* kullanıldığı gruplar üzerinde ek mantığın nasıl gerçekleştirileceğini gösterir. Daha fazla bilgi için bkz [..](into.md) Aşağıdaki örnek, her bir grubu yalnızca anahtar değerini bir sesli harf olarak seçmek üzere sorgular.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `group` yan tümceleri <xref:System.Linq.Enumerable.GroupBy%2A> yöntemine yapılan çağrılara çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [Sorgu Anahtar Sözcükleri](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [İç içe geçmiş grup oluşturma](../../linq/create-a-nested-group.md)
- [Sorgu sonuçlarını gruplandırma](../../linq/group-query-results.md)
- [Gruplandırma işleminde alt sorgu gerçekleştirme](../../linq/perform-a-subquery-on-a-grouping-operation.md)
