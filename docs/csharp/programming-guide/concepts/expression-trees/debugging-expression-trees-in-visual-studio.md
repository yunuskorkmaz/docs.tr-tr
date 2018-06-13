---
title: Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 0b3017f2800a2eb7332028b9cfe6ed9877222087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340076"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
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
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerleri temsil eden nesneler ve `null`, sabit değeri görüntülenir.  
  
 C# değişmez değerler olarak standart sonekleri sayısal türleri için sonek değerine eklenir. Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.  
  
|Tür|Son eki|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 Varsa türü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifade türü farklıdır nesne, türü görüntülenir `DebugInfo` köşeli özelliğinde (\< ve >). Aksi takdirde türünü <xref:System.Linq.Expressions.BlockExpression> nesnesi görüntülenmez.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> nesneler kendi temsilci türleri ile birlikte görüntülenir.  
  
 Lambda ifadesi bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Lambda1` veya `#Lambda2`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 İçin varsayılan bir değer belirtirseniz, <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesnesi.  
  
 `.Label` Belirteci etiketi başlangıcını gösterir. `.LabelTarget` Belirteci atlamak için hedef hedef gösterir.  
  
 Bir etiket bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Label1` veya `#Label2`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Checked işleçleri  
 Checked işleçleri işleci önünde "#" simgesiyle gösterilir. Örneğin, denetlenen Toplama işleci olarak görüntülenir `#+`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)  
 [Özel Görselleştiriciler oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
