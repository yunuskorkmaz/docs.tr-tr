---
title: 'Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme'
ms.date: 08/28/2020
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 7d38a45263135fa10dc53dc0d09b8129838e78e6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117785"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (Visual Basic)

Arabirime uzantı yöntemleri ekleyerek LINQ sorguları için kullandığınız yöntemlerin kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> . Örneğin, standart ortalama veya en yüksek işlemlere ek olarak, bir dizi değerden tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturursunuz. Ayrıca, bir dizi değer için özel bir filtre veya belirli bir veri dönüştürmesi olarak çalışacak bir yöntem oluşturun ve yeni bir dizi döndürür. Bu tür yöntemlere örnekler, <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Skip%2A> ve ' dir <xref:System.Linq.Enumerable.Reverse%2A> .

<xref:System.Collections.Generic.IEnumerable%601>Arabirimi genişlettiğinizde, özel yöntemlerinizi herhangi bir sıralanabilir koleksiyona uygulayabilirsiniz. Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../language-features/procedures/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Toplama yöntemi ekleme

Toplama yöntemi bir değer kümesinden tek bir değeri hesaplar. LINQ, ve dahil olmak üzere birkaç toplama yöntemi sağlar <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> . Arayüze bir genişletme yöntemi ekleyerek kendi toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .

Aşağıdaki kod örneği, `Median` bir tür sayı dizisi için ortanca hesaplamak üzere çağrılan bir genişletme yönteminin nasıl oluşturulacağını göstermektedir `double` .

:::code language="vb" source="./snippets/LinqExtension.vb" :::

Bu genişletme yöntemini, herhangi bir sıralanabilir koleksiyon için, arabirimden diğer toplama yöntemlerini çağırdığınız şekilde çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .

> [!NOTE]
> Visual Basic, `Aggregate` veya yan tümcesi için bir yöntem çağrısı veya standart sorgu söz dizimini kullanabilirsiniz `Group By` . Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).

Aşağıdaki kod örneği, `Median` bir dizi türü için yönteminin nasıl kullanılacağını gösterir `double` .

:::code language="vb" source="./snippets/Program.vb" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli türleri kabul etmek için bir toplama yöntemini aşırı yükleme

Toplama yönteminizi çeşitli türlerde dizileri kabul edecek şekilde aşırı yükleyebilirsiniz. Standart yaklaşım, her tür için bir aşırı yükleme oluşturmaktır. Başka bir yaklaşım ise genel bir tür alacak ve bir temsilciyi kullanarak belirli bir türe dönüştürecek bir aşırı yükleme oluşturmaktır. Her iki yaklaşımı de birleştirebilirsiniz.

#### <a name="to-create-an-overload-for-each-type"></a>Her tür için bir aşırı yükleme oluşturmak için

Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz. Aşağıdaki kod örneği, türü için yönteminin bir aşırı yüklemesini gösterir `Median` `integer` .

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="IntOverload":::

Artık `Median` `integer` `double` , aşağıdaki kodda gösterildiği gibi, hem hem de türleri için aşırı yüklemeleri çağırabilirsiniz:

:::code language="vb" source="./snippets/Program.vb" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a>Genel aşırı yükleme oluşturmak için

Ayrıca, genel nesne dizisini kabul eden bir aşırı yükleme de oluşturabilirsiniz. Bu aşırı yükleme bir temsilciyi parametre olarak alır ve bir genel türdeki nesne dizisini belirli bir türe dönüştürmek için kullanır.

Aşağıdaki kod, `Median` <xref:System.Func%602> bir parametresi olarak temsilciyi alan yönteminin bir aşırı yüklemesini gösterir. Bu temsilci, genel türde bir nesne alır `T` ve türünde bir nesne döndürür `double` .

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="GenericOverload":::

Artık `Median` herhangi bir türdeki nesne dizisi için yöntemini çağırabilirsiniz. Türün kendi yöntem aşırı yüklemesi yoksa, bir temsilci parametresi geçirmeniz gerekir. Visual Basic, bu amaçla bir lambda ifadesi kullanabilirsiniz. Ayrıca, `Aggregate` `Group By` Yöntem çağrısı yerine OR yan tümcesini kullanırsanız, bu yan tümce kapsamındaki herhangi bir değer veya ifade geçirebilirsiniz.

Aşağıdaki örnek kod, `Median` bir tamsayılar dizisi ve dizeler dizisi için yönteminin nasıl çağrılacağını gösterir. Dizeler için, dizideki dizelerin uzunluklarının ortancası hesaplanır. Örnek, <xref:System.Func%602> her durumda temsilci parametresinin yönteme nasıl geçirileceğini gösterir `Median` .

:::code language="vb" source="./snippets/Program.vb" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-collection"></a>Koleksiyon döndüren bir yöntem ekleme

<xref:System.Collections.Generic.IEnumerable%601>Arabirimi bir değer dizisi döndüren özel bir sorgu yöntemiyle genişletebilirsiniz. Bu durumda, yöntemin türünde bir koleksiyon döndürmesi gerekir <xref:System.Collections.Generic.IEnumerable%601> . Bu tür yöntemler, bir değerler dizisine filtre veya veri dönüştürmeleri uygulamak için kullanılabilir.

Aşağıdaki örnek, `AlternateElements` ilk öğeden başlayarak bir koleksiyondaki her öğeyi döndüren adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="SequenceElement":::

Aşağıdaki kodda gösterildiği gibi, herhangi bir sayılabilir koleksiyon için bu genişletme yöntemini, arabirimden diğer yöntemleri çağırdığınız gibi çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> :

:::code language="vb" source="./snippets/Program.vb" ID="SequenceUsage":::

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Uzantı Metotları](../../language-features/procedures/extension-methods.md)
