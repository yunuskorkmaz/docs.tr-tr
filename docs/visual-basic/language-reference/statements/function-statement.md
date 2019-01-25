---
title: Function Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
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
ms.openlocfilehash: 5018aebb0401ce5a1c46ecf04a7c65ca676271e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565910"
---
# <a name="function-statement-visual-basic"></a>Function Deyimi (Visual Basic)
Adı, parametreleri ve kodu tanımlayan bildirir bir `Function` yordamı.  
  
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
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)

    - [Private Protected](../../language-reference/modifiers/private-protected.md)  
  
     Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     İsteğe bağlı. Aşağıdakilerden biri olabilir:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     İsteğe bağlı. Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     İsteğe bağlı. Bkz: [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     İsteğe bağlı. Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Gerekli. Yordamın adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     İsteğe bağlı. Genel bir yordam için tür parametreleri listesi. Bkz: [türü listesinde](type-list.md).  
  
-   `parameterlist`  
  
     İsteğe bağlı. Bu yordamı parametrelerini temsil eden yerel değişken adlarının listesi. Bkz: [parametre listesi](parameter-list.md).  
  
-   `returntype`  
  
     Gerekli if `Option Strict` olduğu `On`. Bu yordam tarafından döndürülen değerin veri türü.  
  
-   `Implements`  
  
     İsteğe bağlı. Bu yordam bir veya daha fazla uyguladığını belirtir `Function` yordamları, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim içinde tanımlanmış her biri. Bkz: [uygulayan deyimi](implements-statement.md).  
  
-   `implementslist`  
  
     Gerekli if `Implements` sağlanır. Listesi `Function` uygulanmakta olan yordamlar.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `interface.definedname`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`interface`|Gerekli. Bu yordam tarafından uygulanan arabirimin adını sınıf veya yapı içeren.|  
    |`definedname`|Gerekli. Ad tarafından yordamı tanımlanan `interface`.|  
  
-   `Handles`  
  
     İsteğe bağlı. Bu yordam, bir veya daha fazla belirli olayları işleyebileceğini belirtir. Bkz: [işler](handles-clause.md).  
  
-   `eventlist`  
  
     Gerekli if `Handles` sağlanır. Bu yordamı işleme olayların listesi.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:  
  
     `eventvariable.event`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`eventvariable`|Gerekli. Nesne değişkeni sınıfın veya olayı yükselten yapı veri türü ile bildirilmiş.|  
    |`event`|Gerekli. Bu yordamı işleme olayın adı.|  
  
-   `statements`  
  
     İsteğe bağlı. Bu yordamda yürütülecek deyimler bloğunu.  
  
-   `End Function`  
  
     Bu yordamın tanımını sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm yürütülebilir kod yordam içinde olmalıdır. Her yordamı sırayla bir sınıf, yapı veya içeren sınıf, yapı veya modül Belirtilen modül içinde bildirilir.  
  
 Çağrıldığı koda bir değer döndürmek için kullanmak bir `Function` yordamı; Aksi durumda, bir `Sub` yordamı.  
  
## <a name="defining-a-function"></a>Bir işlevi tanımlama  
 Tanımlayabileceğiniz bir `Function` yordamı yalnızca Modül düzeyinde. Bu nedenle, bir işlev bildirimi bağlamı bir sınıf, yapı, modül veya bir arabirim olmalıdır ve bir kaynak dosyası, bir ad alanı, bir yordam veya bir bloğu olamaz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
 `Function` yordamları varsayılan genel erişim için. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz.  
  
 A `Function` yordamı yordamın döndürdüğü değerin veri türü bildirebilirsiniz. Herhangi bir veri türü veya bir sabit listesi, bir yapı, bir sınıf veya arabirim adını belirtebilirsiniz. Belirtmezseniz `returntype` parametresi yordamın döndürdüğü `Object`.  
  
 Bu yordamı kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıfı veya yapısına sahip olması gerekir bir `Implements` deyim indisinin hemen ardından kendi `Class` veya `Structure` deyimi. `Implements` Deyimi, belirtilen her bir arabirime içermelidir `implementslist`. Ancak, bir arabirim tarafından tanımlayan adı `Function` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).  
  
> [!NOTE]
>  Lambda ifadeleri, işlev ifadeleri satır içi tanımlamak için kullanabilirsiniz. Daha fazla bilgi için [işlev ifadesi](../../../visual-basic/language-reference/operators/function-expression.md) ve [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Bir işlevden döndürme  
 Zaman `Function` yordamı çağıran koda döndürür, yordamı çağıran deyim izleyen deyime ile yürütme devam eder.  
  
 Bir işlevden bir değer döndürmek için işlev adını değerini atayın veya olmasını bir `Return` deyimi.  
  
 `Return` Deyimi aynı anda dönüş değeri atar ve aşağıdaki örnekte gösterildiği gibi işlev çıkar.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction` ve ardından `Exit Function` döndürülecek deyimi.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function` Ve `Return` deyimleri neden hemen çıkılmadan bir `Function` yordamı. Herhangi bir sayıda `Exit Function` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Function` ve `Return` deyimleri.  
  
 Kullanırsanız `Exit Function` değerine atama olmadan `name`, belirtilen veri türü için varsayılan değer yordamın döndürdüğü `returntype`. Varsa `returntype` , yordam döndürür belirtilmemiş `Nothing`, varsayılan değeri olduğu `Object`.  
  
## <a name="calling-a-function"></a>İşlev Çağırma  
 Çağrısı bir `Function` yordamı kullanarak bir ifadede, parantez içindeki bağımsız değişken listesi tarafından izlenen yordam adı. Yalnızca, herhangi bir bağımsız değişken olmayan Eğer ayraçları atlayabilirsiniz. Ancak, kodunuz her zaman parantezler eklerseniz daha okunabilir olur.  
  
 Çağrısı bir `Function` kitaplık çağrısı aynı şekilde işlev gibi yordamı `Sqrt`, `Cos`, veya `ChrW`.  
  
 Kullanarak bir işlevi çağırabilir `Call` anahtar sözcüğü. Bu durumda, dönüş değeri yok sayılır. Kullanım `Call` anahtar sözcüğü, çoğu durumda önerilmez. Daha fazla bilgi için [Call deyimi](call-statement.md).  
  
 Visual Basic, aritmetik ifadeler iç verimliliğini artırmak için bazen yeniden düzenler. Bu nedenle, kullanmamalısınız bir `Function` işlevi aynı ifadede değişkenlerin değeri değiştiğinde bir aritmetik ifade yordamda.  
  
## <a name="async-functions"></a>Zaman uyumsuz işlevleri  
 *Zaman uyumsuz* özellik açık geri çağırmaları kullanarak veya kodunuzun birden çok işlevleri veya lambda ifadelerinde el ile bölme olmadan zaman uyumsuz işlevleri çağıran olanak tanır.  
  
 Bir işlev ile işaretlerseniz [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) kullanabileceğiniz değiştiricisi [Await](../../../visual-basic/language-reference/operators/await-operator.md) işlevindeki işleci. Ulaştığında denetlemek bir `Await` ifadesinde `Async` işlevi, Denetim çağırana döner ve awaited görevi tamamlanıncaya kadar işlevi ediyor askıya alınır. Görev tamamlandığında, işlevi yürütme sürdürebilirsiniz.  
  
> [!NOTE]
>  Bir `Async` yordam ya da henüz tamamlanmadı ilk beklenen nesne karşılaştığında çağırana döndürür veya sonuna alır `Async` yordamı, hangisi daha önce gerçekleşirse.  
  
 Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>. Örneği bir `Async` dönüş türü olan işlev <xref:System.Threading.Tasks.Task%601> aşağıda verilmiştir.  
  
 Bir `Async` işlevi herhangi bildiremez [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametreleri.  
  
 A [Sub deyimi](sub-statement.md) ile işaretlenebilir `Async` değiştiricisi. Burada bir değer döndürülemez bu olay işleyicileri için temel olarak kullanılır. Bir `Async` `Sub` yordamı beklenemez ve çağıran bir `Async` `Sub` yordamı tarafından oluşturulan özel durumları yakalamak olamaz `Sub` yordamı.  
  
 Hakkında daha fazla bilgi için `Async` işlevleri, [Async ve Await ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda akış kontrolü](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Yineleyici işlevleri  
 Bir *yineleyici* işlevi bir liste veya dizi gibi bir koleksiyon üzerinde özel yineleme gerçekleştirir. Bir yineleyici işlevi kullanır [Yield](yield-statement.md) her öğeyi bir defada döndürmek için deyimi. Olduğunda bir [Yield](yield-statement.md) deyimine ulaşıldığında, kodun geçerli konumu anımsanacak. Yürütme, yineleyici işlevinin bir sonraki zamana o konumdan başlatılır.  
  
 Bir yineleyici kullanarak istemci koddan çağırmak bir [her biri için... Sonraki](for-each-next-statement.md) deyimi.  
  
 Bir yineleyici işlevinin dönüş türü olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Daha fazla bilgi için [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Function` adı, parametreleri ve gövdesini kod bildirmek için deyimi bir `Function` yordamı. `ParamArray` Değiştirici, değişken sayıda bağımsız değişken kabul etmek işlevi etkinleştirir.  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örnekte bildirilen bir işlevi çağırır.  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `DelayAsync` olduğu bir `Async` `Function` dönüş türü olan <xref:System.Threading.Tasks.Task%601>. `DelayAsync` sahip bir `Return` deyimi bir tamsayı döndürür. Bu nedenle işlevi bildirimi `DelayAsync` dönüş türüne sahip olması `Task(Of Integer)`. Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` bir tamsayı üretir. Bu bu deyimi gösterilmektedir: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Yordamdır örneği bir `Async Sub` yordamı. Çünkü `DoSomethingAsync` olduğu bir `Async` işlevi, görev için yapılan çağrının `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi beklenmesini gerekir: `Await DoSomethingAsync()`. `startButton_Click` `Sub` Yordamı ile tanımlanmalıdır `Async` değiştiricisi olduğundan bir `Await` ifade.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sub Deyimi](sub-statement.md)
- [İşlev Yordamları](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Parametre Listesi](parameter-list.md)
- [Dim Deyimi](dim-statement.md)
- [Call Deyimi](call-statement.md)
- [,](of-clause.md)
- [Parametre Dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordam Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [İşlev İfadesi](../../../visual-basic/language-reference/operators/function-expression.md)
