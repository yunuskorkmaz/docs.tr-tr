---
title: Çalışma zamanı durumu temelinde sorgulama (Visual Basic)
description: Kodunuzun, bu yöntemlere geçirilen LINQ Yöntem çağrılarını veya ifade ağaçlarını değiştirerek çalışma zamanı durumuna göre dinamik olarak sorgulamak için kullanabileceği çeşitli teknikler açıklanmaktadır.
ms.date: 02/14/2021
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: c9f57950b2c26c0cca798ab632da90bf9f6c519a
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584865"
---
# <a name="querying-based-on-runtime-state-visual-basic"></a>Çalışma zamanı durumu temelinde sorgulama (Visual Basic)

Bir <xref:System.Linq.IQueryable> veri kaynağına karşı bir veya bir [IQueryable (Of T)](<xref:System.Linq.IQueryable%601>) tanımlayan kodu düşünün:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Initialize":::

Bu kodu her çalıştırdığınızda, aynı tam sorgu yürütülür. Bu, kodunuzun çalışma zamanında koşullara bağlı olarak farklı sorgular yürütmesini isteyebileceğiniz için genellikle çok yararlı değildir. Bu makalede, çalışma zamanı durumuna göre farklı bir sorguyu nasıl yürütebileceğinizi açıklar.

## <a name="iqueryable--iqueryableof-t-and-expression-trees"></a>IQueryable/IQueryable (Of T) ve ifade ağaçları

Temelde <xref:System.Linq.IQueryable> iki bileşeni vardır:

* <xref:System.Linq.IQueryable.Expression>&mdash;bir ifade ağacı biçiminde geçerli sorgu bileşenlerinin dil ve veri kaynağı belirsiz temsili.
* <xref:System.Linq.IQueryable.Provider>&mdash;bir LINQ sağlayıcısı örneği, geçerli sorguyu bir değere veya bir değer kümesine nasıl bir şekilde bir değere veya değer kümesine nasıl bir şekilde bir değere göre nasıl bir

Dinamik sorgulama bağlamında, sağlayıcı genellikle aynı kalır; sorgunun ifade ağacı sorgudan sorguya farklı olacak.

İfade ağaçları sabittir; farklı bir ifade ağacı &mdash; ve bu nedenle farklı bir sorgu istiyorsanız &mdash; , var olan ifade ağacını yeni birine ve bu nedenle de yeni bir sorguya çevirmeniz gerekir <xref:System.Linq.IQueryable> .

Aşağıdaki bölümlerde, çalışma zamanı durumuna yanıt olarak farklı sorgulama için özel teknikler açıklanır:

- Çalışma zamanı durumunu ifade ağacı içinden kullanın
- Ek LINQ yöntemlerini çağırın
- LINQ yöntemlerine geçirilen ifade ağacını farklılık gösterir
- Üzerinde Fabrika yöntemlerini kullanarak bir [ifade (Of TDelegate)](xref:System.Linq.Expressions.Expression%601) ifade ağacı oluşturun <xref:System.Linq.Expressions.Expression>
- Bir ifade ağacına Yöntem çağrı düğümleri ekleme <xref:System.Linq.IQueryable>
- Dizeler oluşturun ve [dınamık LINQ kitaplığını](https://dynamic-linq.net/) kullanın

## <a name="use-runtime-state-from-within-the-expression-tree"></a>Çalışma zamanı durumunu ifade ağacı içinden kullanın

LINQ sağlayıcısı 'nın onu desteklediğine göre, dinamik olarak sorgu oluşturmanın en kolay yolu, aşağıdaki kod örneğinde olduğu gibi, doğrudan sorgudaki bir kapalı değişken aracılığıyla çalışma zamanı durumuna başvurmalıdır `length` :

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Runtime_state_from_within_expression_tree":::

İç ifade ağacı &mdash; ve bu nedenle sorgu &mdash; değiştirilmedi; sorgu yalnızca değeri değiştiği için farklı değerler döndürüyor `length` .

## <a name="call-additional-linq-methods"></a>Ek LINQ yöntemlerini çağırın

Genellikle, [YERLEŞIK LINQ yöntemleri](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) <xref:System.Linq.Queryable> iki adım gerçekleştirir:

* Yöntem çağrısını temsil eden içinde geçerli ifade ağacını sarın <xref:System.Linq.Expressions.MethodCallExpression> .
* Sarmalanan ifade ağacını sağlayıcıya geri geçirin; Örneğin, sağlayıcının yöntemi aracılığıyla bir değer döndürün <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> ya da yöntemi aracılığıyla çevrilmiş bir sorgu nesnesi döndürün <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> .

Yeni bir sorgu almak için bir [IQueryable (Of T)](xref:System.Linq.IQueryable%601)-döndüren yönteminin sonucuyla birlikte özgün sorguyu değiştirebilirsiniz. Bu, aşağıdaki örnekte olduğu gibi, çalışma zamanı durumuna göre koşullu şekilde yapabilirsiniz:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a>LINQ yöntemlerine geçirilen ifade ağacını farklılık gösterir

Çalışma zamanı durumuna bağlı olarak LINQ yöntemlerine farklı ifadeler geçirebilirsiniz:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Varying_expressions":::

Ayrıca, [Linqkit](http://www.albahari.com/nutshell/linqkit.aspx)'In [predicatebuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx)gibi üçüncü taraf bir kitaplık kullanarak çeşitli alt ifadeler oluşturmak isteyebilirsiniz:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Compose_expression":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a>Fabrika yöntemlerini kullanarak ifade ağaçları ve sorgular oluşturun

Bu noktaya kadar olan tüm örneklerde, derleme zamanında öğe türü &mdash; `String` &mdash; ve bu nedenle sorgu türü bilinirdi &mdash; `IQueryable(Of String)` . Herhangi bir öğe türünün sorgusuna bileşen eklemeniz veya öğe türüne bağlı olarak farklı bileşenler eklemeniz gerekebilir. ' Deki fabrika yöntemlerini kullanarak baştan sona ifade ağaçları oluşturabilir <xref:System.Linq.Expressions.Expression?displayProperty=fullName> ve bu sayede çalışma zamanında ifadeyi belirli bir öğe türüne uyarlayabilirsiniz.

### <a name="constructing-an-expressionof-tdelegate"></a>Ifade oluşturma [(TDelegate 'in)](xref:System.Linq.Expressions.Expression%601)

LINQ metotlarından birine geçirilecek bir ifade oluşturduğunuzda, aslında bir [ifade örneği (TDelegate)](xref:System.Linq.Expressions.Expression%601)oluşturursunuz; burada,, `TDelegate` `Func(Of String, Boolean)` `Action` veya özel bir temsilci türü gibi bir temsilci türüdür.

[İfade (Of TDelegate))](xref:System.Linq.Expressions.Expression%601) <xref:System.Linq.Expressions.LambdaExpression>, aşağıdaki gibi bir bütün lambda ifadesini temsil eden öğesinden devralır:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Compiler_generated":::

<xref:System.Linq.Expressions.LambdaExpression>, İki bileşene sahiptir:

* &mdash; `(x As String)` &mdash; özelliği tarafından temsil edilen bir parametre <xref:System.Linq.Expressions.LambdaExpression.Parameters> listesi
* &mdash; `x.StartsWith("a")` &mdash; özelliği tarafından temsil edilen bir gövde <xref:System.Linq.Expressions.LambdaExpression.Body> .

Bir [ifade (TDelegate)](xref:System.Linq.Expressions.Expression%601) oluşturma içindeki temel adımlar aşağıdaki gibidir:

* <xref:System.Linq.Expressions.ParameterExpression>Lambda ifadesindeki her bir parametre (varsa) için nesneleri, <xref:System.Linq.Expressions.Expression.Parameter%2A> Factory yöntemini kullanarak tanımlayın.

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_parameter":::

* <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.ParameterExpression> Tanımladığınız öğeleri ve ' deki fabrika yöntemlerini kullanarak, gövdesinin gövdesini oluşturun <xref:System.Linq.Expressions.Expression> . Örneğin, temsil eden bir ifade şöyle `x.StartsWith("a")` oluşturulabilir:

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_body":::

* Parametreleri ve gövdesini, uygun fabrika yöntemi aşırı yüklemesini kullanarak, derleme zamanı türü belirtilmiş bir [ifadede (TDelegate)](xref:System.Linq.Expressions.Expression%601)sarın <xref:System.Linq.Expressions.Expression.Lambda%2A> :

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_lambda":::

Aşağıdaki bölümlerde, bir LINQ yöntemine geçirilecek bir [ifade (TDelegate)](xref:System.Linq.Expressions.Expression%601) oluşturmak isteyebileceğiniz ve Fabrika yöntemlerini kullanarak nasıl yapılacağını gösteren bir örnek sağlayan bir senaryo açıklanır.

### <a name="scenario"></a>Senaryo

Birden çok varlık türü olduğunu varsayalım:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Entities.vb":::

Bu varlık türlerinin herhangi biri için, yalnızca kendi alanlarından birinde belirli bir metne sahip olan varlıkları filtrelemek ve döndürmek istersiniz `string` . İçin, `Person` `FirstName` ve özelliklerini aramak istersiniz `LastName` :

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="PersonsQry":::

Ancak `Car` , için yalnızca özelliğini aramak istersiniz `Model` :

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="CarsQry":::

İçin bir özel işlev ve diğeri için yazabilirken `IQueryable(Of Person)` `IQueryable(Of Car)` , aşağıdaki işlev bu filtrelemeyi, belirli öğe türünden bağımsız olarak varolan herhangi bir sorguya ekler.

### <a name="example"></a>Örnek

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_expression_of_tdelegate":::

`TextFilter`İşlev bir [IQueryable (Of T)](xref:System.Linq.IQueryable%601) alıp döndürdüğünden (yalnızca bir <xref:System.Linq.IQueryable> ), metin filtresinden sonra, derleme zamanı türü belirtilmiş sorgu öğeleri ekleyebilirsiniz.

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a>İfade ağacına Yöntem çağrı düğümleri ekleyin <xref:System.Linq.IQueryable>

Bir <xref:System.Linq.IQueryable> [IQueryable (Of T)](xref:System.Linq.IQueryable%601)yerıne, genel LINQ yöntemleri doğrudan çağrılamaz. Diğer bir seçenek de, yukarıdaki gibi iç ifade ağacını derlemek ve ifade ağacına geçiş yaparken uygun LINQ metodunu çağırmak için yansıma kullanmaktır.

LINQ yönteminin işlevini, LINQ yöntemine yapılan çağrıyı temsil eden ' de tüm ağacı sarmalayarak da çoğaltabilirsiniz <xref:System.Linq.Expressions.MethodCallExpression> .

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_lambdaexpression":::

Bu durumda, bir derleme zamanı `T` genel yer tutucusu olmadığından, <xref:System.Linq.Expressions.Expression.Lambda%2A> derleme zamanı türü bilgileri gerektirmeyen ve bir <xref:System.Linq.Expressions.LambdaExpression> [Ifade (Of TDelegate)](xref:System.Linq.Expressions.Expression%601)yerine bir oluşturan aşırı yüklemeyi kullanacaksınız.

## <a name="the-dynamic-linq-library"></a>Dinamik LINQ kitaplığı

Fabrika yöntemlerini kullanarak ifade ağaçları oluşturmak nispeten karmaşıktır; dizeleri oluşturmak daha kolaydır. [Dınamık LINQ kitaplığı](https://dynamic-linq.net/) , IÇINDEKI <xref:System.Linq.IQueryable> standart LINQ yöntemlerine karşılık gelen <xref:System.Linq.Queryable> ve ifade ağaçları yerine [özel bir sözdiziminde](https://dynamic-linq.net/expression-language) dizeleri kabul eden bir genişletme yöntemleri kümesi sunar. Kitaplık, dizeden uygun ifade ağacını oluşturur ve elde edilen çevrilen sonuçları döndürebilir <xref:System.Linq.IQueryable> .

Örneğin, önceki örnek (ifade ağacı oluşturma dahil) şu şekilde yeniden yazılabilir:

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Dynamic_linq":::

## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](index.md)
- [Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)](how-to-execute-expression-trees.md)
