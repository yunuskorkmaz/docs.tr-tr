---
title: Function Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 667ab7ceb54e1f339fd645883ca2686c0cbb72b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-statement-visual-basic"></a>Function Deyimi (Visual Basic)
Ad, parametreleri ve tanımlama kodu bildiren bir `Function` yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `attributelist`  
  
     İsteğe bağlı. Bkz: [öznitelik listesi](attribute-list.md).  
  
-   `accessmodifier`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Özel](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     İsteğe bağlı. Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     İsteğe bağlı. Bkz: [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     İsteğe bağlı. Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Gerekli. Yordamın adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     İsteğe bağlı. Tür parametreleri genel bir yordam listesi. Bkz: [yazın listesi](type-list.md).  
  
-   `parameterlist`  
  
     İsteğe bağlı. Bu yordam parametreleri temsil eden yerel değişken adları listesi. Bkz: [parametre listesi](parameter-list.md).  
  
-   `returntype`  
  
     Gerekli olursa `Option Strict` olan `On`. Bu yordam tarafından döndürülen değerin veri türü.  
  
-   `Implements`  
  
     İsteğe bağlı. Bu yordam bir veya daha fazla uyguladığını gösteren `Function` yordamlar, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri. Bkz: [uygulayan deyimi](implements-statement.md).  
  
-   `implementslist`  
  
     Gerekli olursa `Implements` sağlanır. Listesi `Function` uygulanan yordamlar.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `interface.definedname`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`interface`|Gerekli. Bu yordam tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.|  
    |`definedname`|Gerekli. Adı olarak yordamı tanımlanmış `interface`.|  
  
-   `Handles`  
  
     İsteğe bağlı. Bu yordam bir veya daha fazla belirli olayları işleyebilirsiniz gösterir. Bkz: [işleme](handles-clause.md).  
  
-   `eventlist`  
  
     Gerekli olursa `Handles` sağlanır. Bu yordamı işleme olayların listesi.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `eventvariable.event`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`eventvariable`|Gerekli. Nesne değişkeni sınıf veya olayı oluşturan yapı, veri türü ile bildirilmedi.|  
    |`event`|Gerekli. Bu yordamı işleme olayın adı.|  
  
-   `statements`  
  
     İsteğe bağlı. Bu yordam içinde yürütülecek deyimleri bloğu.  
  
-   `End Function`  
  
     Bu yordamı tanımı sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm yürütülebilir kod yordam içinde olmalıdır. Her bir yordam bir sınıf, bir yapı veya için içeren sınıf, yapı veya modülü adlandırılan bir modül içinde sırayla bildirildi.  
  
 Çağrıyı yapan kod için bir değer döndürmek için kullanmak bir `Function` yordamı; Aksi takdirde kullanın bir `Sub` yordamı.  
  
## <a name="defining-a-function"></a>Bir işlev tanımlama  
 Tanımlayabileceğiniz bir `Function` yordamı yalnızca modülü düzeyinde. Bu nedenle, bir işlev bildirimi bağlamının bir sınıf, bir yapı, bir modül veya bir arabirim olmalıdır ve bir kaynak dosyası, bir ad alanı, bir yordam veya bir blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
 `Function`Genel erişim varsayılan yordamlar. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.  
  
 A `Function` yordamı yordamın döndürdüğü değerin veri türü bildirebilirsiniz. Herhangi bir veri türü veya numaralandırma, bir yapı, bir sınıf veya arabirim adını belirtebilirsiniz. Belirtmediyseniz `returntype` parametresi yordamın döndürdüğü `Object`.  
  
 Bu yordamı kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı de olmalıdır bir `Implements` hemen izleyen deyimi kendi `Class` veya `Structure` deyimi. `Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`. Ancak, bir arabirim tarafından tanımlayan ad `Function` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).  
  
> [!NOTE]
>  Lambda ifadeleri işlev ifadeleri satır içi tanımlamak için kullanabilirsiniz. Daha fazla bilgi için bkz: [işlev ifadesi](../../../visual-basic/language-reference/operators/function-expression.md) ve [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Bir işlevden döndürme  
 Zaman `Function` yordamı çağıran kodu döndürür, yürütme yordamı adlı deyimi aşağıdaki deyim ile devam eder.  
  
 Bir işlevden bir değer döndürmek için değer işlev adını atayın veya olmasını bir `Return` deyimi.  
  
 `Return` Deyimi aynı anda dönüş değeri atar ve aşağıdaki örnekte gösterildiği gibi işlev çıkar.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction` ve ardından `Exit Function` dönmek için deyimi.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function` Ve `Return` deyimleri neden bir hemen çıkın bir `Function` yordamı. Herhangi bir sayıda `Exit Function` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Function` ve `Return` deyimleri.  
  
 Kullanırsanız `Exit Function` değerine atama olmadan `name`, belirtilen veri türü için varsayılan değer yordamı döndürür `returntype`. Varsa `returntype` , yordam döndürür belirlenmezse `Nothing`, varsayılan değeri olduğu `Object`.  
  
## <a name="calling-a-function"></a>İşlev Çağırma  
 Çağırmanız bir `Function` bir ifadede parantez içinde bağımsız değişken listesi ve ardından yordam adı kullanarak yordamı. Herhangi bir bağımsız değişken yalnızca sağladığını olmayan parantez kullanmayabilirsiniz. Ancak, kodunuzun her zaman parantez eklerseniz, daha okunabilir durumdadır.  
  
 Çağırmanız bir `Function` herhangi bir kitaplığı çağrı aynı şekilde işlev gibi yordamı `Sqrt`, `Cos`, veya `ChrW`.  
  
 Bir işlev kullanarak da çağırabilirsiniz `Call` anahtar sözcüğü. Bu durumda, dönüş değeri göz ardı edilir. Kullanımı `Call` anahtar sözcüğü, çoğu durumda önerilmez. Daha fazla bilgi için bkz: [Call deyimi](call-statement.md).  
  
 Visual Basic bazen iç verimliliğini artırmak için aritmetik ifadeler yeniden düzenler. Bu nedenle, kullanmamanız bir `Function` işlevi aynı ifadedeki değişkenlerin değerini değiştiğinde aritmetik ifadelerde yordamı.  
  
## <a name="async-functions"></a>Zaman uyumsuz işlevleri  
 *Zaman uyumsuz* özelliği açık geri aramalar kullanarak veya birden çok işlevleri veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz işlevleri çağırmak sağlar.  
  
 Bir işlev ile işaretlerseniz [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) kullanabileceğiniz değiştiricisi, [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) işlevinde işleci. Ulaştığında denetlemek bir `Await` ifadesinde `Async` işlevi, Denetim çağırana döndürür ve awaited görevi tamamlanana kadar işlevi ediyor askıya alındı. Görev tamamlandığında yürütme işlevinde devam edebilirsiniz.  
  
> [!NOTE]
>  Bir `Async` yordamı ya da tamamlanmamış ilk awaited nesne karşılaştığında çağırana döndürür veya sonuna alır `Async` yordamı, hangisi oluşur ilk.  
  
 Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>. Örnek olarak bir `Async` dönüş türüne sahip işlevi <xref:System.Threading.Tasks.Task%601> aşağıda verilmiştir.  
  
 Bir `Async` işlevi herhangi bildiremez [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametreleri.  
  
 A [Sub deyimi](sub-statement.md) ile işaretlenebilir `Async` değiştiricisi. Burada bir değer döndürülemiyor bu olay işleyicileri için temel olarak kullanılır. Bir `Async``Sub` yordamı beklemenin olamaz ve çağıran bir `Async``Sub` yordam tarafından oluşturulan özel durumları yakalama olamaz `Sub` yordamı.  
  
 Hakkında daha fazla bilgi için `Async` İşlevler, bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [akış denetimi zaman uyumsuz programlarda](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Yineleyici işlevleri  
 Bir *yineleyici* işlevi bir liste veya dizi gibi bir koleksiyon üzerinden özel bir yineleme gerçekleştirir. Yineleyici işlevini kullanıyor [verim](yield-statement.md) her öğeye aynı anda geri dönmek için deyimi. Zaman bir [verim](yield-statement.md) deyimi ulaşıldığında geçerli kod konumda anımsanacak. Yürütme o konumdan yineleyici işlevi bir sonraki zamana yeniden başlatılır.  
  
 Yineleyici kullanarak istemci kodundan çağıran bir [For Each... Sonraki](for-each-next-statement.md) deyimi.  
  
 Bir yineleyici işlevinin dönüş türü olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Daha fazla bilgi için bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Function` ad, parametreleri ve gövdesini kodu bildirmek için deyimi bir `Function` yordamı. `ParamArray` Değiştiricisi değişken sayıda bağımsız değişken kabul etmek işlevi sağlar.  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örnekte bildirilen işlevi çağırır.  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `DelayAsync` olan bir `Async``Function` dönüş türüne sahip <xref:System.Threading.Tasks.Task%601>. `DelayAsync`sahip bir `Return` deyimi bir tamsayı döndürür. Bu nedenle işlev bildirimi `DelayAsync` dönüş türüne sahip olması `Task(Of Integer)`. Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` tamsayı üretir. Bu bu deyim içinde gösterilmiştir: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Yordamdır örneği bir `Async Sub` yordamı. Çünkü `DoSomethingAsync` olan bir `Async` işlevi, görev çağrısı için `DoSomethingAsync` aşağıdaki ifadeyi gösterdiği gibi beklemenin gerekir: `Await DoSomethingAsync()`. `startButton_Click``Sub` Yordamı tanımlı, ile `Async` değiştiricisi içerdiğinden bir `Await` ifade.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sub deyimi](sub-statement.md)  
 [İşlev yordamları](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Parametre listesi](parameter-list.md)  
 [Dim deyimi](dim-statement.md)  
 [Call deyimi](call-statement.md)  
 [,](of-clause.md)  
 [Parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Nasıl yapılır: genel bir sınıf kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Sorun giderme yordamları](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [İşlev ifadesi](../../../visual-basic/language-reference/operators/function-expression.md)
