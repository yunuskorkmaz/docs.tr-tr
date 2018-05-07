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
ms.openlocfilehash: 2674986013afccf0a61267e49ca186d2ccb380e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="group-clause-c-reference"></a>group tümcesi (C# Başvurusu)
`group` Yan tümcesi bir dizi döndürür <xref:System.Linq.IGrouping%602> grubu için anahtar değeri ile eşleşen sıfır veya daha fazla öğe içeren nesne. Örneğin, bir dizi dize her dizedeki ilk harfi göre gruplandırabilirsiniz. Bu durumda, ilk harfi anahtarı ve bir türe sahip [char](../../../csharp/language-reference/keywords/char.md)ve depolanan `Key` her özellik <xref:System.Linq.IGrouping%602> nesnesi. Derleyici anahtar türü oluşturur.  
  
 Bir sorgu ifadesi ile sona erdirebilirsiniz bir `group` yan tümcesi, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 Her Grup ek sorgu işlemleri gerçekleştirmek istiyorsanız, kullanarak geçici bir tanımlayıcı belirtebilirsiniz [içine](../../../csharp/language-reference/keywords/into.md) bağlamsal anahtar sözcüğü. Kullandığınızda `into`, sorguyla devam etmek ve sonunda biriyle sona bir `select` deyimi veya başka bir `group` aşağıdaki alıntı gösterildiği gibi yan tümcesi:  
  
 [!code-csharp[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 Daha da kullanımını örnekleri'nı tamamlamak `group` olan ve olmayan `into` Bu konu örnek bölümünde verilmiştir.  
  
## <a name="enumerating-the-results-of-a-group-query"></a>Bir grup sorgunun sonuçlarını numaralandırma  
 Çünkü <xref:System.Linq.IGrouping%602> nesneleri tarafından üretilen bir `group` sorgu temelde listelerinin listesini, bir iç içe kullanmalısınız [foreach](../../../csharp/language-reference/keywords/foreach-in.md) her grup içindeki öğeler erişmek için döngü. Grup anahtarlar üzerinden dış döngüsü yineler ve gruptaki her öğe üzerinden iç döngüsü yineler. Bir grup, bir anahtar, ancak hiçbir öğe olabilir. Aşağıdaki `foreach` önceki kod örneklerinde Sorguyu yürüten döngü:  
  
 [!code-csharp[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## <a name="key-types"></a>Anahtar türü  
 Gibi bir dize, yerleşik bir sayısal tür veya kullanıcı tanımlı tür veya anonim tür adlı Grup anahtarları herhangi bir türü olabilir.  
  
### <a name="grouping-by-string"></a>Dizeye göre gruplandırma  
 Kullanılan önceki kod örnekleri bir `char`. Bir dize anahtarı kolayca bunun yerine, örneğin tam son adı belirtilmiş:  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### <a name="grouping-by-bool"></a>Bool göre gruplandırma  
 Aşağıdaki örnekte, iki gruba sonuçları bölmek bir anahtar için bool değeri kullanımını göstermektedir. Bir alt ifadesinde değeri oluşturduğu Not `group` yan tümcesi.  
  
 [!code-csharp[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### <a name="grouping-by-numeric-range"></a>Sayısal aralığına göre gruplandırma  
 Sonraki örnek yüzdebirlik aralığı temsil eden sayısal Grup anahtarları oluşturmak için bir ifade kullanır. Kullanımına dikkat edin [izin](../../../csharp/language-reference/keywords/let-clause.md) böylece iki kez yöntemi çağırma gerekmez bir yöntem depolamak için uygun bir konuma sonucu, çağrı `group` yan tümcesi. Ayrıca, Not `group` "sıfıra" özel durumu önlemek için kodu Öğrenci sıfır ortalama yok emin olmak için denetlemesini yan tümcesi. Güvenli bir şekilde sorgu ifadelerinde yöntemleri kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Sorgu ifadelerinde özel durumları işlemek](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).  
  
 [!code-csharp[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### <a name="grouping-by-composite-keys"></a>Bileşik anahtarlara göre gruplandırma  
 Grup öğeleri birden fazla anahtar göre istediğinizde bir bileşik anahtarı kullanın. Anahtar öğesi tutmak için anonim bir tür veya bir adlandırılmış türü kullanarak bileşik bir anahtar oluşturun. Aşağıdaki örnekte, varsayımında bir sınıf `Person` adlı üyeleriyle bildirilen `surname` ve `city`. `group` Yan tümcesi aynı Soyadı ve aynı Şehir sahip kişiyi her kümesi oluşturulması farklı bir grup neden olur.  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 Başka bir yönteme sorgu değişkeni başarılı olursa bir adlandırılmış türü kullanın. Otomatik uygulanan özellikler için anahtarlar kullanarak özel bir sınıf oluşturun ve daha sonra geçersiz <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemleri. Bir yapı; bu durumda kesinlikle bu yöntemleri geçersiz kılmak elinizde de kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: Auto-Implemented özelliklerle hafif bir sınıf uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) ve [nasıl yapılır: bir dizin ağacında yinelenen dosyalar için sorgu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). İkinci konu bir bileşik anahtarı adlandırılmış bir türü ile kullanmak nasıl gösteren kod örneği vardır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hiçbir ek sorgu mantığı gruplarına uygulandığında gruplar halinde kaynak verileri sıralama için standart deseni gösterir. Bu, bir devamlılık olmadan bir gruplandırma çağrılır. Dize dizisi öğeleri kendi ilk harfi göre gruplandırılır. Sorgunun sonucu olan bir <xref:System.Linq.IGrouping%602> içeren ortak bir türü `Key` türündeki özelliği `char` ve bir <xref:System.Collections.Generic.IEnumerable%601> gruplandırma her öğe içeren koleksiyon.  
  
 Sonucunu bir `group` yan tümcesi olan sıraları dizisidir. Bu nedenle, döndürülen her grup içindeki ayrı ayrı öğeler erişmek için bir iç içe kullanın `foreach` döngünün Grup anahtarları aşağıdaki örnekte gösterildiği gibi döngü içinde.  
  
 [!code-csharp[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, kullanarak oluşturduktan sonra ek mantık gruplarında gerçekleştirmek nasıl gösterir bir *devamlılık* ile `into`. Daha fazla bilgi için bkz: [içine](../../../csharp/language-reference/keywords/into.md). Aşağıdaki örnekte, yalnızca sesli bir anahtar değeri olan seçmek için her grubu sorgular.  
  
 [!code-csharp[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme zamanında `group` yan tümceleri çevrilen çağrıları içine <xref:System.Linq.Enumerable.GroupBy%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.IGrouping%602>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.Enumerable.ThenBy%2A>  
 <xref:System.Linq.Enumerable.ThenByDescending%2A>  
 [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Nasıl yapılır: iç içe geçmiş grup oluşturma](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [Nasıl yapılır: sorgu sonuçlarını gruplandırma](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [Nasıl yapılır: gruplandırma işleminde alt sorgu gerçekleştirme](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
