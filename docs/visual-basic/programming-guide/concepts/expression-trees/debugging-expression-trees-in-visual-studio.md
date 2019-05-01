---
title: Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: fb5905c3c1124dd64371216bddda0a17235abdce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787198"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama

Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz. İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir. Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).

Daha iyi ifade ağaçları içeriğini temsil etmek için `DebugView` özelliği, Visual Studio görselleştiriciler kullanır. Daha fazla bilgi için [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>İfade ağacı bir görselleştiriciyi açmak için

1. Yanında görünen Büyüteç simgesine tıklayarak `DebugView` özelliğine bir ifade ağacında **DataTips**, **izleme** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.

    Görselleştiriciler listesi görüntülenir.

2. Kullanmak istediğiniz Görselleştirici'a tıklayın.

Aşağıdaki bölümlerde açıklandığı gibi her ifade türü görselleştiricisi içinde görüntülenir.

## <a name="parameterexpressions"></a>ParameterExpressions

<xref:System.Linq.Expressions.ParameterExpression> Değişken adlarının başında bir "$" simgesi ile görüntülenir.

Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.

### <a name="examples"></a>Örnekler

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    `DebugView` Özelliği

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    `DebugView` Özelliği

    `$var1`

## <a name="constantexpressions"></a>ConstantExpressions
 İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.

### <a name="examples"></a>Örnekler

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` Özelliği

    10

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` Özelliği

    10D

## <a name="blockexpression"></a>BlockExpression

Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifadenin türü nesne farklıdır, türü görüntülenen `DebugInfo` açılı ayraçlar özelliğinde (\< ve >). Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.

### <a name="examples"></a>Örnekler

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    `DebugView` Özelliği

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    `DebugView` Özelliği

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleri ile birlikte görüntülenir.

Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.

### <a name="examples"></a>Örnekler

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    `DebugView` Özelliği

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    `DebugView` Özelliği

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a>LabelExpression

İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesne.

`.Label` Belirteci etiketi başlangıcını gösterir. `.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.

Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.

### <a name="examples"></a>Örnekler

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    `DebugView` Özelliği

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    `DebugView` Özelliği

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a>İşaretli işleçleri

İşaretli işleçler, işlecin önüne "#" sembolü ile görüntülenir. Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.

### <a name="examples"></a>Örnekler

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    `DebugView` Özelliği

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    `DebugView` Özelliği

    `#(System.Int32)10D`

## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
