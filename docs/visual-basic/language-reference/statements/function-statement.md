---
title: Function Deyimi
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
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345929"
---
# <a name="function-statement-visual-basic"></a>Function Deyimi (Visual Basic)

Bir `Function` yordamını tanımlayan adı, parametreleri ve kodu bildirir.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).

- `accessmodifier`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.

- `proceduremodifiers`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  İsteğe bağlı. Bkz. [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  İsteğe bağlı. Bkz. [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  İsteğe bağlı. Bkz. [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  Gerekli. Yordamın adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  İsteğe bağlı. Genel bir yordamın tür parametrelerinin listesi. Bkz. [tür listesi](type-list.md).

- `parameterlist`

  İsteğe bağlı. Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi. Bkz. [parametre listesi](parameter-list.md).

- `returntype`

  `Option Strict` `On`olması gerekir. Bu yordamın döndürdüğü değerin veri türü.

- `Implements`

  İsteğe bağlı. Bu yordamın, her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla `Function` yordamlarını uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).

- `implementslist`

  `Implements` sağlanırsa gereklidir. Uygulanan `Function` yordamlarının listesi.

  `implementedprocedure [ , implementedprocedure ... ]`

  Her `implementedprocedure` aşağıdaki söz dizimi ve bölümlere sahiptir:

  `interface.definedname`

  |Bölümüyle|Açıklama|
  |---|---|
  |`interface`|Gerekli. Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.|
  |`definedname`|Gerekli. Yordamın `interface`tanımladığı ad.|

- `Handles`

  İsteğe bağlı. Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir. Bkz. [işleyiciler](handles-clause.md).

- `eventlist`

  `Handles` sağlanırsa gereklidir. Bu yordamın işleyeceği olayların listesi.

  `eventspecifier [ , eventspecifier ... ]`

  Her `eventspecifier` aşağıdaki söz dizimi ve bölümlere sahiptir:

  `eventvariable.event`

  |Bölümüyle|Açıklama|
  |---|---|
  |`eventvariable`|Gerekli. Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.|
  |`event`|Gerekli. Bu yordamın işleyeceği olayın adı.|

- `statements`

  İsteğe bağlı. Bu yordamda yürütülecek deyim bloğu.

- `End Function`

  Bu yordamın tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

Tüm yürütülebilir kodların bir yordamın içinde olması gerekir. Her yordam, sırasıyla bir sınıf, yapı veya kapsayan sınıf, yapı veya modül olarak başvurulan bir modül içinde bildirilmiştir.

Çağırma koduna bir değer döndürmek için `Function` yordamı kullanın; Aksi takdirde, `Sub` prosedürü kullanın.

## <a name="defining-a-function"></a>Işlev tanımlama

Bir `Function` yordamını yalnızca modül düzeyinde tanımlayabilirsiniz. Bu nedenle, bir işlev için bildirim bağlamı bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

yordamları, genel erişim için varsayılan `Function`. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

`Function` yordam, yordamın döndürdüğü değerin veri türünü bildirebilirler. Herhangi bir veri türü veya bir numaralandırma, bir yapı, sınıf veya arabirim adı belirtebilirsiniz. `returntype` parametresini belirtmezseniz, yordam `Object`döndürür.

Bu yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Class` veya `Structure` bildirisini hemen izleyen bir `Implements` ifadesine de sahip olması gerekir. `Implements` deyimin `implementslist`belirtilen her arabirimi içermesi gerekir. Ancak, bir arabirimin `Function` tanımladığı adın (`definedname`) bu yordamın adıyla eşleşmesi gerekmez (`name`).

> [!NOTE]
> İşlev ifadelerini satır içi olarak tanımlamak için lambda ifadeleri kullanabilirsiniz. Daha fazla bilgi için bkz. [Işlev ifadesi](../../../visual-basic/language-reference/operators/function-expression.md) ve [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Bir Işlevden dönme

`Function` yordamı çağıran koda döndüğünde, yürütme yordamı çağıran deyimden sonraki deyimle devam eder.

Bir işlevden bir değer döndürmek için, değeri işlev adına atayabilir veya bir `Return` ifadesine dahil edebilirsiniz.

`Return` deyimin döndürdüğü değeri aynı anda atar ve aşağıdaki örnekte gösterildiği gibi işlevden çıkar.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

Aşağıdaki örnek, `myFunction` işlev adına döndürülen değeri atar ve sonra geri dönmek için `Exit Function` ifadesini kullanır.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

`Exit Function` ve `Return` deyimleri, bir `Function` yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Function` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Function` ve `Return` deyimlerini karıştırabilirsiniz.

`name`bir değer atamadan `Exit Function` kullanırsanız yordam, `returntype`belirtilen veri türü için varsayılan değeri döndürür. `returntype` belirtilmemişse, yordam, `Object`için varsayılan değer olan `Nothing`döndürür.

## <a name="calling-a-function"></a>İşlev Çağırma

Yordam adını, ardından parantez içindeki bağımsız değişken listesini kullanarak bir ifadede bir `Function` yordamını çağırabilirsiniz. Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz. Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.

Bir `Function` yordamını, `Sqrt`, `Cos`veya `ChrW`gibi herhangi bir kitaplık işlevini çağırdığınız şekilde çağırabilirsiniz.

Ayrıca, `Call` anahtar sözcüğünü kullanarak bir işlevi çağırabilirsiniz. Bu durumda, dönüş değeri yok sayılır. Çoğu durumda `Call` anahtar sözcüğünün kullanılması önerilmez. Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).

Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler. Bu nedenle, işlev aynı ifadedeki değişkenlerin değerini değiştirdiğinde bir aritmetik ifadede `Function` yordamı kullanmamalısınız.

## <a name="async-functions"></a>Zaman uyumsuz Işlevler

*Async* özelliği, açık geri çağırmaları kullanmadan veya kodunuzu birden çok işlev veya lambda ifadesine el ile bölmeden zaman uyumsuz işlevleri çağırabilmeniz için izin verir.

Bir işlevi [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiriciyle işaretlerseniz, işlevindeki [await](../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanabilirsiniz. Denetim, `Async` işlevindeki bir `Await` ifadesine ulaştığında, Denetim çağırana döner ve beklenen görev tamamlanana kadar işlevdeki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme işlevinde çalışmaya çalışabilir.

> [!NOTE]
> Bir `Async` yordam, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında arayan öğesine geri döner veya `Async` yordamının sonuna, hangisi önce gerçekleştiğine gelir.

`Async` işlevi <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>dönüş türüne sahip olabilir. Aşağıda <xref:System.Threading.Tasks.Task%601> dönüş türüne sahip `Async` işleve bir örnek verilmiştir.

Bir `Async` işlevi herhangi bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametresi bildiremeyebilir.

Bir [alt ifade](sub-statement.md) `Async` değiştiricisi ile de işaretlenebilir. Bu, öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır. Bir `Async` `Sub` yordamı beklelenemez ve `Async` `Sub` yordamının çağıranı `Sub` yordamı tarafından oluşturulan özel durumları yakalayamaz.

`Async` işlevleri hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Yineleyici Işlevleri

*Yineleyici* işlevi, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir. Yineleyici işlevi, her öğeyi birer birer döndürmek için [yield](yield-statement.md) ifadesini kullanır. Bir [yield](yield-statement.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır. Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.

Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki](for-each-next-statement.md) ifade.

Yineleyici işlevinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olabilir.

Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `Function` yordamının gövdesini oluşturan adı, parametreleri ve kodu bildirmek için `Function` bildirimini kullanır. `ParamArray` değiştiricisi, işlevin değişken sayıda bağımsız değişken kabul etmesine olanak sağlar.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, önceki örnekte belirtilen işlevi çağırır.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `DelayAsync` dönüş türü <xref:System.Threading.Tasks.Task%601>olan bir `Async` `Function`. `DelayAsync`, bir tamsayı döndüren bir `Return` bildirimine sahiptir. Bu nedenle `DelayAsync` işlev bildiriminin `Task(Of Integer)`dönüş türü olması gerekir. Dönüş türü `Task(Of Integer)`olduğundan, `DoSomethingAsync` `Await` ifadesinin değerlendirmesi bir tamsayı oluşturur. Bu bildirimde gösterilmiştir: `Dim result As Integer = Await delayTask`.

`startButton_Click` yordam bir `Async Sub` yordamının bir örneğidir. `DoSomethingAsync` bir `Async` işlevi olduğundan, aşağıdaki ifadede gösterildiği gibi, `DoSomethingAsync` çağrısı için de beklenen bir görev olmalıdır: `Await DoSomethingAsync()`. Bir `Await` ifadesi içerdiğinden `startButton_Click` `Sub` yordamının `Async` değiştiricisi ile tanımlanması gerekir.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](sub-statement.md)
- [İşlev Yordamları](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Parametre Listesi](parameter-list.md)
- [Dim Deyimi](dim-statement.md)
- [Call Deyimi](call-statement.md)
- [Durumunu](of-clause.md)
- [Parametre Dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordam Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [İşlev İfadesi](../../../visual-basic/language-reference/operators/function-expression.md)
