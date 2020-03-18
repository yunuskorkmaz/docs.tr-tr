---
title: grup yan tümcesi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713466"
---
# <a name="group-clause-c-reference"></a>group tümcesi (C# Başvurusu)

Yan `group` tümce, <xref:System.Linq.IGrouping%602> grup için anahtar değeriyle eşleşen sıfır veya daha fazla öğe içeren bir nesne dizisi döndürür. Örneğin, her dizedeki ilk harfe göre bir dize dizisini gruplandırmayapabilirsiniz. Bu durumda, ilk harf anahtardır ve bir tür [char](../builtin-types/char.md)vardır `Key` ve her <xref:System.Linq.IGrouping%602> nesnenin özelliğinde depolanır. Derleyici anahtarın türünü çıkartıyor.

Bir sorgu ifadesini aşağıdaki `group` örnekte gösterildiği gibi bir yan tümceyle sonlandırmak için:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Her grupta ek sorgu işlemleri gerçekleştirmek istiyorsanız, [bağlamsal](into.md) anahtar sözcüğü kullanarak geçici bir tanımlayıcı belirtebilirsiniz. Kullandığınızda, `into`sorguya devam etmeli ve sonunda aşağıdaki alıntıda `select` gösterildiği `group` gibi bir deyim veya başka bir yan tümceyle sonlandırmanız gerekir:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Bu makalenin Örnek `group` bölümünde, `into` ile ve olmadan kullanımı daha eksiksiz örnekler verilmiştir.

## <a name="enumerating-the-results-of-a-group-query"></a>Grup sorgusunun sonuçlarını derecelendirme

Sorgu <xref:System.Linq.IGrouping%602> `group` tarafından üretilen nesneler aslında bir liste listesi olduğundan, her gruptaki öğelere erişmek için iç içe geçen bir [döngü](foreach-in.md) kullanmanız gerekir. Dış döngü grup anahtarları üzerinde yineler ve iç döngü grubun kendisindeki her öğenin üzerinde yineler. Bir grubun anahtarı olabilir, ancak öğe yoktur. Önceki kod `foreach` örneklerinde sorguyu yürüten döngü aşağıda verilmiştir:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Anahtar türleri

Grup anahtarları, dize, yerleşik sayısal tür veya kullanıcı tanımlı adlandırılmış tür veya anonim tür gibi herhangi bir tür olabilir.

### <a name="grouping-by-string"></a>Dize göre gruplandırma

Önceki kod örnekleri `char`nde bir . Bunun yerine bir dize tuşu kolayca belirtilmiş olabilir, örneğin soyadının tamamı:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Bool'a göre gruplandırma

Aşağıdaki örnek, sonuçları iki gruba ayırmak için bir anahtar için bool değerinin kullanımını gösterir. Değerin `group` yan tümcedeki bir alt ifade yle üretildiğini unutmayın.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Sayısal aralıkla gruplandırma

Sonraki örnek, yüzdelik aralığını temsil eden sayısal grup anahtarları oluşturmak için bir ifade kullanır. Bir yöntem arama sonucunu depolamak için uygun bir konum olarak izin verme nin kullanımına dikkat edin, böylece metodu yan tümcede iki kez çağırmak zorunda kalmamalısınız. [let](let-clause.md) `group` Sorgu ifadelerinde yöntemlerin güvenli bir şekilde nasıl kullanılacağı hakkında daha fazla bilgi için sorgu [ifadelerinde özel durumları ele'ye](../../linq/handle-exceptions-in-query-expressions.md)bakın.

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Bileşik tuşlara göre gruplandırma

Öğeleri birden fazla anahtara göre gruplandırmak istediğinizde bileşik anahtar kullanın. Anahtar öğesini tutmak için anonim bir tür veya adlandırılmış bir tür kullanarak bileşik bir anahtar oluşturursunuz. Aşağıdaki örnekte, bir sınıfın `Person` adlandırılmış `surname` üyelerle `city`birlikte bildirildiğini varsayalım ve . Yan `group` tümce, her bir ad ve aynı şehre sahip kişiler için ayrı bir grup oluşturulmasına neden olur.

```csharp
group person by new {name = person.surname, city = person.city};
```

Sorgu değişkenini başka bir yönteme geçirmeniz gerekiyorsa, adlandırılmış bir tür kullanın. Tuşlar için otomatik olarak uygulanan özellikleri kullanarak özel bir <xref:System.Object.Equals%2A> sınıf <xref:System.Object.GetHashCode%2A> oluşturun ve ardından bu ve yöntemleri geçersiz kılın. Ayrıca bir yapı kullanabilirsiniz, bu durumda kesinlikle bu yöntemleri geçersiz kılmak zorunda değildir. Daha fazla bilgi için, [otomatik olarak uygulanan özelliklere sahip hafif bir sınıfın nasıl uygulanacağını](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [dizin ağacında yinelenen dosyaları nasıl sorgulayabilirsiniz'a](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)bakın. İkinci makalede, adlandırılmış bir türe sahip bileşik anahtarın nasıl kullanılacağını gösteren bir kod örneği vardır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, gruplara ek sorgu mantığı uygulanmadığında kaynak verileri gruplara sıralamak için standart deseni gösterir. Buna devamı olmayan bir gruplama denir. Dizeleri bir dizi elemanları ilk harfe göre gruplanır. Sorgunun sonucu, tür <xref:System.Linq.IGrouping%602> `Key` `char` ve gruplandırmadaki her öğeyi içeren bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyon içeren bir türdür.

Bir `group` yan tümcenin sonucu diziler dizisidir. Bu nedenle, döndürülen her grup içindeki tek `foreach` tek öğelere erişmek için, aşağıdaki örnekte gösterildiği gibi, grup anahtarlarını yineleyen döngü içinde iç içe bir döngü kullanın.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Örnek

Bu örnek, '' ile bir *devamı* kullanarak, bunları oluşturduktan `into`sonra gruplar üzerinde ek mantık gerçekleştirmek için nasıl gösterir. Daha fazla bilgi için [bkz.](into.md) Aşağıdaki örnek, yalnızca anahtar değeri sesli harf olan kişileri seçmek için her grubu sorgular.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `group` yan tümceler <xref:System.Linq.Enumerable.GroupBy%2A> yönteme yapılan çağrılara çevrilir.

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
