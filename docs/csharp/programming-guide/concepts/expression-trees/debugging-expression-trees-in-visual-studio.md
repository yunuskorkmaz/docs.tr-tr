---
title: Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 308b377af00a3d12523f8f8d469c50808f216030
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632159"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz. İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir. Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).  
  
 Daha iyi ifade ağaçları içeriğini temsil etmek için `DebugView` özelliği, Visual Studio görselleştiriciler kullanır. Daha fazla bilgi için [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>İfade ağacı bir görselleştiriciyi açmak için  
  
1.  Yanında görünen Büyüteç simgesine tıklayarak `DebugView` özelliğine bir ifade ağacında **DataTips**, **izleme** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.  
  
     Görselleştiriciler listesi görüntülenir.  
  
2.  Kullanmak istediğiniz Görselleştirici'a tıklayın.  
  
 Aşağıdaki bölümlerde açıklandığı gibi her ifade türü görselleştiricisi içinde görüntülenir.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> Değişken adlarının başında bir "$" simgesi ile görüntülenir.  
  
 Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.  
  
 C# sabit değer olarak standart sonekleri olan sayısal türleri için sonek değerine eklenir. Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.  
  
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
 Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifadenin türü nesne farklıdır, türü görüntülenen `DebugInfo` açılı ayraçlar özelliğinde (\< ve >). Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleri ile birlikte görüntülenir.  
  
 Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesne.  
  
 `.Label` Belirteci etiketi başlangıcını gösterir. `.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.  
  
 Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>İşaretli işleçleri  
 İşaretli işleçler, işlecin önüne "#" sembolü ile görüntülenir. Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.  
  
### <a name="examples"></a>Örnekler  
  
|İfade|`DebugView` Özelliği|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)
- [Özel Görselleştirici Oluşturma](/visualstudio/debugger/create-custom-visualizers-of-data)
