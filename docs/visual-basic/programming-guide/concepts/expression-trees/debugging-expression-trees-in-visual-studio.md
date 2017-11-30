---
title: "Visual Studio (Visual Basic) ifade ağaçlarında hata ayıklama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff1bee9c3c3fdeafab24368d2c7e8376d4ff7b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 <xref:System.Linq.Expressions.ParameterExpression>değişken adları başında "$" simgesiyle görüntülenir.  
  
 Bir parametre bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `$var1` veya `$var2`.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     `DebugView`özelliği  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     `DebugView`özelliği  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerleri temsil eden nesneler ve `null`, sabit değeri görüntülenir.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView`özelliği  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView`özelliği  
  
     10D  
  
## <a name="blockexpression"></a>BlockExpression  
 Varsa türü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifade türü farklıdır nesne, türü görüntülenir `DebugInfo` köşeli özelliğinde (\< ve >). Aksi takdirde türünü <xref:System.Linq.Expressions.BlockExpression> nesnesi görüntülenmez.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     `DebugView`özelliği  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     `DebugView`özelliği  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression>nesneler kendi temsilci türleri ile birlikte görüntülenir.  
  
 Lambda ifadesi bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Lambda1` veya `#Lambda2`.  
  
### <a name="examples"></a>Örnekler  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     `DebugView`özelliği  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     `DebugView`özelliği  
  
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
  
     `DebugView`özelliği  
  
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
  
     `DebugView`özelliği  
  
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
  
     `DebugView`özelliği  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     `DebugView`özelliği  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)  
 [Özel Görselleştiriciler oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
