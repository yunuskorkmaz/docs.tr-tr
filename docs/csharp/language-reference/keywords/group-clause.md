---
description: Group yan tümcesi-C# başvurusu
title: Group yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 5e642492b4b36bb0464baf16baa80c58c19ba9f1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138234"
---
# <a name="group-clause-c-reference"></a>group tümcesi (C# Başvurusu)

`group`Yan tümcesi, <xref:System.Linq.IGrouping%602> Grup için anahtar değeriyle eşleşen sıfır veya daha fazla öğe içeren bir nesne dizisi döndürür. Örneğin, her bir dizedeki ilk harfe göre bir dizi dizeyi gruplandırabilirsiniz. Bu durumda, ilk harf anahtardır ve bir tür [char](../builtin-types/char.md)içerir ve `Key` her nesnenin özelliğinde saklanır <xref:System.Linq.IGrouping%602> . Derleyici, anahtarın türünü haller.

`group`Aşağıdaki örnekte gösterildiği gibi bir sorgu ifadesini yan tümcesiyle sona erdirmek için:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Her grupta ek sorgu işlemleri gerçekleştirmek [istiyorsanız, ' ın bağlamsal anahtar](into.md) sözcüğünü kullanarak geçici bir tanımlayıcı belirtebilirsiniz. `into`' I kullandığınızda sorgu ile devam etmeniz ve sonunda `select` aşağıdaki alıntıda gösterildiği gibi bir deyimi ya da başka bir yan tümcesini sona erdirmek gerekir `group` :

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

`group`Bu makalenin örnek bölümünde ile ve olmadan kullanımı için daha kapsamlı örnekler verilmiştir `into` .

## <a name="enumerating-the-results-of-a-group-query"></a>Bir grup sorgusunun sonuçlarını numaralandırma

<xref:System.Linq.IGrouping%602>Bir sorgu tarafından üretilen nesneler `group` temelde bir liste listesi olduğundan, her bir gruptaki öğelere erişmek için iç içe geçmiş bir [foreach](foreach-in.md) döngüsü kullanmanız gerekir. Dış döngü grup anahtarlarının üzerinde yinelenir ve iç döngü gruptaki her öğe için yinelenir. Bir grupta anahtar olabilir ancak öğe yok. Aşağıda, `foreach` önceki kod örneklerinde sorguyu yürüten döngü verilmiştir:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Anahtar türleri

Grup anahtarları dize, yerleşik bir sayısal tür veya Kullanıcı tanımlı adlandırılmış tür veya anonim tür gibi herhangi bir tür olabilir.

### <a name="grouping-by-string"></a>Dizeye göre gruplandırma

Önceki kod örnekleri bir kullanır `char` . Bunun yerine bir dize anahtarı kolayca belirtilmelidir, örneğin, son soyadı adı:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Bool ile gruplandırma

Aşağıdaki örnek, sonuçları iki gruba bölmek için bir anahtar için bool değer kullanımını gösterir. Değerin yan tümce içindeki bir alt ifade tarafından üretildiğini unutmayın `group` .

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Sayısal aralığa göre gruplandırma

Sonraki örnek, bir yüzdebirlik aralığını temsil eden sayısal grup anahtarları oluşturmak için bir ifade kullanır. Bir yöntem çağrı sonucunu depolamak için uygun bir konum olarak [izin ver](let-clause.md) öğesinin kullanımını unutmayın. bu sayede yöntemi yan tümcesinde iki kez çağırmak zorunda kalmazsınız `group` . Sorgu ifadelerinde yöntemleri güvenle kullanma hakkında daha fazla bilgi için bkz. [sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Bileşik anahtarlara göre gruplandırma

Öğeleri birden fazla anahtara göre gruplandırmak istediğinizde bileşik anahtar kullanın. Anahtar öğesini tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak bileşik anahtar oluşturursunuz. Aşağıdaki örnekte, bir sınıfının `Person` ve adlı üyelerle bildirildiği varsayılır `surname` `city` . `group`Yan tümcesi, aynı soyadı ve aynı şehirde bulunan her kişi kümesi için ayrı bir grup oluşturulmasına neden olur.

```csharp
group person by new {name = person.surname, city = person.city};
```

Sorgu değişkenini başka bir yönteme geçirmeniz gerekiyorsa adlandırılmış bir tür kullanın. Anahtarlar için otomatik uygulanan özellikler kullanarak özel bir sınıf oluşturun ve ardından <xref:System.Object.Equals%2A> ve yöntemlerini geçersiz kılın <xref:System.Object.GetHashCode%2A> . Ayrıca, bu yöntemleri kesin bir şekilde geçersiz kılmak zorunda değilsiniz bir yapı da kullanabilirsiniz. Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [bir dizin ağacındaki yinelenen dosyaları sorgulama](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). İkinci makalede, adlandırılmış tür ile bileşik anahtarın nasıl kullanılacağını gösteren bir kod örneği bulunur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, gruplara ek sorgu mantığı uygulanırken kaynak verileri gruplara sıralamak için standart düzeni gösterir. Bu, devamlılık olmadan gruplandırma olarak adlandırılır. Dizeler dizisindeki öğeler, ilk harfine göre gruplandırılır. Sorgunun sonucu, <xref:System.Linq.IGrouping%602> türünde public bir `Key` özelliği `char` ve <xref:System.Collections.Generic.IEnumerable%601> gruplandırmadaki her öğeyi içeren bir koleksiyonu içeren bir türdür.

`group`Yan tümcesinin sonucu bir dizi dizidir. Bu nedenle, döndürülen her grup içindeki ayrı öğelere erişmek için, `foreach` Aşağıdaki örnekte gösterildiği gibi, döngü içinde grup anahtarlarını yineleyen iç içe bir döngü kullanın.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Örnek

Bu örnek, ile *devam* eden kullanarak gruplar üzerinde nasıl ek mantık gerçekleştirileceğini gösterir `into` . Daha fazla bilgi için bkz [..](into.md) Aşağıdaki örnek, her bir grubu yalnızca anahtar değerini bir sesli harf olarak seçmek üzere sorgular.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `group` yan tümceler yöntemine yapılan çağrılara çevrilir <xref:System.Linq.Enumerable.GroupBy%2A> .

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
