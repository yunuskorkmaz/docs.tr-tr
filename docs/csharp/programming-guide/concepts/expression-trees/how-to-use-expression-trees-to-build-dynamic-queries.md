---
title: Çalışma zamanı durumuna göre sorgulama (C#)
description: Kodunuzun, bu yöntemlere geçirilen LINQ Yöntem çağrılarını veya ifade ağaçlarını değiştirerek çalışma zamanı durumuna göre dinamik olarak sorgulamak için kullanabileceği çeşitli teknikler açıklanmaktadır.
ms.date: 02/11/2021
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 5e015bbc69b61b783abd7eba9cfcf13c29d5c3be
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100581936"
---
# <a name="querying-based-on-runtime-state-c"></a>Çalışma zamanı durumuna göre sorgulama (C#)

Bir <xref:System.Linq.IQueryable> veri kaynağına karşı bir veya bir [IQueryable \<T> ](<xref:System.Linq.IQueryable%601>) tanımlayan kodu düşünün:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Initialize":::

Bu kodu her çalıştırdığınızda, aynı tam sorgu yürütülür. Bu, kodunuzun çalışma zamanında koşullara bağlı olarak farklı sorgular yürütmesini isteyebileceğiniz için genellikle çok yararlı değildir. Bu makalede, çalışma zamanı durumuna göre farklı bir sorguyu nasıl yürütebileceğinizi açıklar.

## <a name="iqueryable--iqueryablet-and-expression-trees"></a>IQueryable/IQueryable \<T> ve ifade ağaçları

Temelde <xref:System.Linq.IQueryable> iki bileşeni vardır:

* <xref:System.Linq.IQueryable.Expression>&mdash;bir ifade ağacı biçiminde geçerli sorgu bileşenlerinin dil ve veri kaynağı belirsiz temsili.
* <xref:System.Linq.IQueryable.Provider>&mdash;bir LINQ sağlayıcısı örneği, geçerli sorguyu bir değere veya bir değer kümesine nasıl bir şekilde bir değere veya değer kümesine nasıl bir şekilde bir değere göre nasıl bir

Dinamik sorgulama bağlamında, sağlayıcı genellikle aynı kalır; sorgunun ifade ağacı sorgudan sorguya farklı olacak.

İfade ağaçları sabittir; farklı bir ifade ağacı &mdash; ve bu nedenle farklı bir sorgu istiyorsanız &mdash; , var olan ifade ağacını yeni birine ve bu nedenle de yeni bir sorguya çevirmeniz gerekir <xref:System.Linq.IQueryable> .

Aşağıdaki bölümlerde, çalışma zamanı durumuna yanıt olarak farklı sorgulama için özel teknikler açıklanır:

- Çalışma zamanı durumunu ifade ağacı içinden kullanın
- Ek LINQ yöntemlerini çağırın
- LINQ yöntemlerine geçirilen ifade ağacını farklılık gösterir
- Üzerinde Fabrika yöntemlerini kullanarak bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) ifadesi ağacı oluşturun<xref:System.Linq.Expressions.Expression>
- Bir ifade ağacına Yöntem çağrı düğümleri ekleme <xref:System.Linq.IQueryable>
- Dizeler oluşturun ve [dınamık LINQ kitaplığını](https://dynamic-linq.net/) kullanın

## <a name="use-runtime-state-from-within-the-expression-tree"></a>Çalışma zamanı durumunu ifade ağacı içinden kullanın

LINQ sağlayıcısı 'nın onu desteklediğine göre, dinamik olarak sorgu oluşturmanın en kolay yolu, aşağıdaki kod örneğinde olduğu gibi, doğrudan sorgudaki bir kapalı değişken aracılığıyla çalışma zamanı durumuna başvurmalıdır `length` :

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Runtime_state_from_within_expression_tree":::

İç ifade ağacı &mdash; ve bu nedenle sorgu &mdash; değiştirilmedi; sorgu yalnızca değeri değiştiği için farklı değerler döndürüyor `length` .

## <a name="call-additional-linq-methods"></a>Ek LINQ yöntemlerini çağırın

Genellikle, [YERLEŞIK LINQ yöntemleri](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) <xref:System.Linq.Queryable> iki adım gerçekleştirir:

* Yöntem çağrısını temsil eden içinde geçerli ifade ağacını sarın <xref:System.Linq.Expressions.MethodCallExpression> .
* Sarmalanan ifade ağacını sağlayıcıya geri geçirin; Örneğin, sağlayıcının yöntemi aracılığıyla bir değer döndürün <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> ya da yöntemi aracılığıyla çevrilmiş bir sorgu nesnesi döndürün <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> .

Yeni bir sorgu almak için özgün sorguyu bir [IQueryable \<T> ](xref:System.Linq.IQueryable%601)döndüren metodun sonucuyla değiştirebilirsiniz. Bu, aşağıdaki örnekte olduğu gibi, çalışma zamanı durumuna göre koşullu şekilde yapabilirsiniz:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a>LINQ yöntemlerine geçirilen ifade ağacını farklılık gösterir

Çalışma zamanı durumuna bağlı olarak LINQ yöntemlerine farklı ifadeler geçirebilirsiniz:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Varying_expressions":::

Ayrıca, [Linqkit](http://www.albahari.com/nutshell/linqkit.aspx)'In [predicatebuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx)gibi üçüncü taraf bir kitaplık kullanarak çeşitli alt ifadeler oluşturmak isteyebilirsiniz:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compose_expressions":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a>Fabrika yöntemlerini kullanarak ifade ağaçları ve sorgular oluşturun

Bu noktaya kadar olan tüm örneklerde, derleme zamanında öğe türü &mdash; `string` &mdash; ve bu nedenle sorgu türü bilinirdi &mdash; `IQueryable<string>` . Öğe türüne bağlı olarak herhangi bir öğe türünün sorgusuna bileşen eklemeniz veya farklı bileşenler eklemeniz gerekebilir. ' Deki fabrika yöntemlerini kullanarak baştan sona ifade ağaçları oluşturabilir <xref:System.Linq.Expressions.Expression?displayProperty=fullName> ve bu sayede çalışma zamanında ifadeyi belirli bir öğe türüne uyarlayabilirsiniz.

### <a name="constructing-an-expressiontdelegate"></a>[İfade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) oluşturma

LINQ metotlarından birine geçirilecek bir ifade oluşturduğunuzda, aslında bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601)örneği oluşturursunuz; burada,, `TDelegate` `Func<string, bool>` `Action` veya özel bir temsilci türü gibi bir temsilci türüdür.

[İfade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) <xref:System.Linq.Expressions.LambdaExpression>, aşağıdaki gibi bir bütün lambda ifadesini temsil eden öğesinden devralır:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Compiler_generated_expression_tree":::

<xref:System.Linq.Expressions.LambdaExpression>, İki bileşene sahiptir:

* &mdash; `(string x)` &mdash; özelliği tarafından temsil edilen bir parametre <xref:System.Linq.Expressions.LambdaExpression.Parameters> listesi
* &mdash; `x.StartsWith("a")` &mdash; özelliği tarafından temsil edilen bir gövde <xref:System.Linq.Expressions.LambdaExpression.Body> .

Bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) oluşturmak için temel adımlar aşağıdaki gibidir:

* <xref:System.Linq.Expressions.ParameterExpression>Lambda ifadesindeki her bir parametre (varsa) için nesneleri, <xref:System.Linq.Expressions.Expression.Parameter%2A> Factory yöntemini kullanarak tanımlayın.

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_parameter":::

* <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.ParameterExpression> Tanımladığınız öğeleri ve ' deki fabrika yöntemlerini kullanarak, gövdesinin gövdesini oluşturun <xref:System.Linq.Expressions.Expression> . Örneğin, temsil eden bir ifade şöyle `x.StartsWith("a")` oluşturulabilir:

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_body":::

* Parametreleri ve gövdesi, uygun fabrika yöntemi aşırı yüklemesini kullanarak, derleme zamanı türü belirlenmiş bir [ifadede \<TDelegate> ](xref:System.Linq.Expressions.Expression%601)sarın <xref:System.Linq.Expressions.Expression.Lambda%2A> :

    :::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_method_expression_tree_lambda":::

Aşağıdaki bölümlerde, bir LINQ yöntemine geçirilecek bir [ifade \<TDelegate> ](xref:System.Linq.Expressions.Expression%601) oluşturmak isteyebileceğiniz ve Fabrika yöntemlerini kullanarak nasıl yapılacağını gösteren bir örnek sağlayan bir senaryo açıklanır.

### <a name="scenario"></a>Senaryo

Birden çok varlık türü olduğunu varsayalım:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Entities":::

Bu varlık türlerinin herhangi biri için, yalnızca kendi alanlarından birinde belirli bir metne sahip olan varlıkları filtrelemek ve döndürmek istersiniz `string` . İçin, `Person` `FirstName` ve özelliklerini aramak istersiniz `LastName` :

```csharp
string term = /* ... */;
var personsQry = new List<Person>()
    .AsQueryable()
    .Where(x => x.FirstName.Contains(term) || x.LastName.Contains(term));
```

Ancak `Car` , için yalnızca özelliğini aramak istersiniz `Model` :

```csharp
string term = /* ... */;
var carsQry = new List<Car>()
    .AsQueryable()
    .Where(x => x.Model.Contains(term));
```

İçin bir özel işlev ve diğeri için yazabilirken `IQueryable<Person>` `IQueryable<Car>` , aşağıdaki işlev bu filtrelemeyi, belirli öğe türünden bağımsız olarak varolan herhangi bir sorguya ekler.

### <a name="example"></a>Örnek

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate":::

`TextFilter`İşlev bir [IQueryable \<T> ](xref:System.Linq.IQueryable%601) (ve yalnızca bir) alıp döndürdüğünden <xref:System.Linq.IQueryable> , metin filtresinden sonra, derleme zamanı türü belirtilmiş sorgu öğeleri ekleyebilirsiniz.

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a>İfade ağacına Yöntem çağrı düğümleri ekleyin <xref:System.Linq.IQueryable>

Bir <xref:System.Linq.IQueryable> [IQueryable \<T> ](xref:System.Linq.IQueryable%601)yerıne sahipseniz, genel LINQ yöntemlerini doğrudan çağrılamaz. Diğer bir seçenek de, yukarıdaki gibi iç ifade ağacını derlemek ve ifade ağacına geçiş yaparken uygun LINQ metodunu çağırmak için yansıma kullanmaktır.

LINQ yönteminin işlevini, LINQ yöntemine yapılan çağrıyı temsil eden ' de tüm ağacı sarmalayarak da çoğaltabilirsiniz <xref:System.Linq.Expressions.MethodCallExpression> .

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Factory_methods_lambdaexpression":::

Bu durumda, bir derleme zamanı `T` genel yer tutucusu olmadığından, <xref:System.Linq.Expressions.Expression.Lambda%2A> derleme zamanı türü bilgileri gerektirmeyen ve bir <xref:System.Linq.Expressions.LambdaExpression> Ifade yerine bir [ \<TDelegate> ifadesi](xref:System.Linq.Expressions.Expression%601)üreten aşırı yüklemeyi kullanacaksınız.

## <a name="the-dynamic-linq-library"></a>Dinamik LINQ kitaplığı

Fabrika yöntemlerini kullanarak ifade ağaçları oluşturmak nispeten karmaşıktır; dizeleri oluşturmak daha kolaydır. [Dınamık LINQ kitaplığı](https://dynamic-linq.net/) , IÇINDEKI <xref:System.Linq.IQueryable> standart LINQ yöntemlerine karşılık gelen <xref:System.Linq.Queryable> ve ifade ağaçları yerine [özel bir sözdiziminde](https://dynamic-linq.net/expression-language) dizeleri kabul eden bir genişletme yöntemleri kümesi sunar. Kitaplık, dizeden uygun ifade ağacını oluşturur ve elde edilen çevrilen sonuçları döndürebilir <xref:System.Linq.IQueryable> .

Örneğin, önceki örnek aşağıdaki şekilde yeniden yazılabilir:

:::code language="csharp" source="../../../../../samples/snippets/csharp/programming-guide/dynamic-linq-expression-trees/Program.cs" id="Dynamic_linq":::

## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](./index.md)
- [İfade ağaçlarını yürütme (C#)](./how-to-execute-expression-trees.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
