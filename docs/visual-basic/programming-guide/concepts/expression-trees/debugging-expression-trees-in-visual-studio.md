---
title: Visual Studio (Visual Basic) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 2addba2654067eaaf6c621c927e0992308879ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644244"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio (Visual Basic) ifade ağaçlarında hata ayıklama
Uygulamalarınızda hata ayıklamak zaman ifade ağaçları içeriği ve yapısı analiz edebilirsiniz. İfade ağaç yapısı hızlı bir genel bakış almak için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir. Hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio'da hata ayıklamayı](/visualstudio/debugger/debugging-in-visual-studio).  
  
 İfade ağaçları içeriğini daha iyi göstermek için `DebugView` özelliği Visual Studio görselleştiriciler kullanır. Daha fazla bilgi için bkz: [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Bir ifade ağacına için Görselleştirici açmak için  
  
1.  Yanında Büyüteç simgesini tıklatın `DebugView` bir ifade ağacına özelliğinin **DataTips**, **izleme** penceresinde **otomobiller** penceresinde veya **Yereller** penceresi.  
  
     Görselleştiriciler listesi görüntülenir.  
  
2.  Kullanmak istediğiniz Görselleştirici'ı tıklatın.  
  
 Aşağıdaki bölümlerde açıklandığı gibi her bir ifade türü Görselleştirici görüntülenir.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> değişken adları başında "$" simgesiyle görüntülenir.  
  
 Bir parametre bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `$var1` veya `$var2`.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     `DebugView` Özelliği  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     `DebugView` Özelliği  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerleri temsil eden nesneler ve `null`, sabit değeri görüntülenir.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` Özelliği  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` Özelliği  
  
     10D  
  
## <a name="blockexpression"></a>BlockExpression  
 Varsa türü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifade türü farklıdır nesne, türü görüntülenir `DebugInfo` köşeli özelliğinde (\< ve >). Aksi takdirde türünü <xref:System.Linq.Expressions.BlockExpression> nesnesi görüntülenmez.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     `DebugView` Özelliği  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     `DebugView` Özelliği  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> nesneler kendi temsilci türleri ile birlikte görüntülenir.  
  
 Lambda ifadesi bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Lambda1` veya `#Lambda2`.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     `DebugView` Özelliği  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     `DebugView` Özelliği  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 İçin varsayılan bir değer belirtirseniz, <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesnesi.  
  
 `.Label` Belirteci etiketi başlangıcını gösterir. `.LabelTarget` Belirteci atlamak için hedef hedef gösterir.  
  
 Bir etiket bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Label1` veya `#Label2`.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
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
  
-   `Expression`  
  
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
  
## <a name="checked-operators"></a>Checked işleçleri  
 Checked işleçleri işleci önünde "#" simgesiyle gösterilir. Örneğin, denetlenen Toplama işleci olarak görüntülenir `#+`.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     `DebugView` Özelliği  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     `DebugView` Özelliği  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)  
 [Özel Görselleştiriciler oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
