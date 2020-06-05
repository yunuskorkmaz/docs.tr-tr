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
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404634"
---
# <a name="function-statement-visual-basic"></a>Function Deyimi (Visual Basic)

Bir yordamı tanımlayan adı, parametreleri ve kodu bildirir `Function` .

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

  - [Geneldir](../modifiers/public.md)

  - [Korunamadı](../modifiers/protected.md)

  - [Dost](../modifiers/friend.md)

  - [Özelleştirme](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Özel korumalı](../modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.

- `proceduremodifiers`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Aşırı Yüklemeler](../modifiers/overloads.md)

  - [Geçersiz Kılmalar](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  İsteğe bağlı. Bkz. [paylaşılan](../modifiers/shared.md).

- `Shadows`

  İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).

- `Async`

  İsteğe bağlı. Bkz. [zaman uyumsuz](../modifiers/async.md).

- `Iterator`

  İsteğe bağlı. Bkz. [Yineleyici](../modifiers/iterator.md).

- `name`

  Gereklidir. Yordamın adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  İsteğe bağlı. Genel bir yordamın tür parametrelerinin listesi. Bkz. [tür listesi](type-list.md).

- `parameterlist`

  İsteğe bağlı. Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi. Bkz. [parametre listesi](parameter-list.md).

- `returntype`

  İse gereklidir `Option Strict` `On` . Bu yordamın döndürdüğü değerin veri türü.

- `Implements`

  İsteğe bağlı. Bu yordamın `Function` , her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla yordam uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).

- `implementslist`

  Sağlanırsa gereklidir `Implements` . `Function`Uygulanan yordamların listesi.

  `implementedprocedure [ , implementedprocedure ... ]`

  Her birinin `implementedprocedure` aşağıdaki söz dizimi ve parçaları vardır:

  `interface.definedname`

  |Bölüm|Description|
  |---|---|
  |`interface`|Gereklidir. Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.|
  |`definedname`|Gereklidir. Yordamın tanımlandığı ad `interface` .|

- `Handles`

  İsteğe bağlı. Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir. Bkz. [işleyiciler](handles-clause.md).

- `eventlist`

  Sağlanırsa gereklidir `Handles` . Bu yordamın işleyeceği olayların listesi.

  `eventspecifier [ , eventspecifier ... ]`

  Her birinin `eventspecifier` aşağıdaki söz dizimi ve parçaları vardır:

  `eventvariable.event`

  |Bölüm|Description|
  |---|---|
  |`eventvariable`|Gereklidir. Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.|
  |`event`|Gereklidir. Bu yordamın işleyeceği olayın adı.|

- `statements`

  İsteğe bağlı. Bu yordamda yürütülecek deyim bloğu.

- `End Function`

  Bu yordamın tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

Tüm yürütülebilir kodların bir yordamın içinde olması gerekir. Her yordam, sırasıyla bir sınıf, yapı veya kapsayan sınıf, yapı veya modül olarak başvurulan bir modül içinde bildirilmiştir.

Çağırma koduna bir değer döndürmek için bir `Function` yordam kullanın; Aksi takdirde, bir `Sub` yordam kullanın.

## <a name="defining-a-function"></a>Işlev tanımlama

Bir `Function` yordamı yalnızca modül düzeyinde tanımlayabilirsiniz. Bu nedenle, bir işlev için bildirim bağlamı bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

`Function`yordamlar, genel erişim için varsayılan olarak. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

`Function`Yordam, yordamın döndürdüğü değerin veri türünü bildirebilirler. Herhangi bir veri türü veya bir numaralandırma, bir yapı, sınıf veya arabirim adı belirtebilirsiniz. `returntype`Parametresini belirtmezseniz, yordam döndürür `Object` .

Bu yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının aynı zamanda `Implements` veya ifadesiyle hemen sonraki bir deyime sahip olması gerekir `Class` `Structure` . `Implements`İfadesinin içinde belirtilen her arabirimi içermesi gerekir `implementslist` . Ancak, bir arabirimin `Function` (içinde) tanımladığı adın `definedname` Bu yordamın adıyla eşleşmesi gerekmez (içinde `name` ).

> [!NOTE]
> İşlev ifadelerini satır içi olarak tanımlamak için lambda ifadeleri kullanabilirsiniz. Daha fazla bilgi için bkz. [Işlev ifadesi](../operators/function-expression.md) ve [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Bir Işlevden dönme

`Function`Yordam çağıran koda döndüğünde, yürütme yordamı çağıran deyimden sonraki deyimle devam eder.

Bir işlevden bir değer döndürmek için, değeri işlev adına atayabilir veya bir deyime dahil edebilirsiniz `Return` .

`Return`Deyimde döndürülen değeri aynı anda atar ve aşağıdaki örnekte gösterildiği gibi işlevden çıkar.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

Aşağıdaki örnek, dönüş değerini işlev adına atar `myFunction` ve ardından `Exit Function` döndürmek için ifadesini kullanır.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

`Exit Function`Ve `Return` deyimleri, bir yordamdan hemen çıkılmasına neden olur `Function` . Herhangi bir sayıda `Exit Function` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Function` ve deyimlerini karıştırabilirsiniz `Return` .

`Exit Function`' A bir değer atamakla kullanırsanız `name` , yordam içinde belirtilen veri türü için varsayılan değeri döndürür `returntype` . `returntype`Belirtilmemişse, yordamı `Nothing` için varsayılan değer olan döndürür `Object` .

## <a name="calling-a-function"></a>İşlev Çağırma

Yordam adını ve `Function` sonra parantez içindeki bağımsız değişken listesini bir ifadede kullanarak bir yordamı çağırabilirsiniz. Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz. Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.

Bir `Function` yordamı, veya gibi herhangi bir kitaplık işlevini çağırdığınız şekilde çağırabilirsiniz `Sqrt` `Cos` `ChrW` .

Anahtar sözcüğünü kullanarak bir işlevi de çağırabilirsiniz `Call` . Bu durumda, dönüş değeri yok sayılır. `Call`Çoğu durumda anahtar sözcüğünün kullanılması önerilmez. Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).

Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler. Bu nedenle, `Function` işlev aynı ifadedeki değişkenlerin değerini değiştirdiğinde aritmetik ifadede bir yordam kullanmamanız gerekir.

## <a name="async-functions"></a>Zaman uyumsuz Işlevler

*Async* özelliği, açık geri çağırmaları kullanmadan veya kodunuzu birden çok işlev veya lambda ifadesine el ile bölmeden zaman uyumsuz işlevleri çağırabilmeniz için izin verir.

Bir işlevi [zaman uyumsuz](../modifiers/async.md) değiştiriciyle işaretlerseniz, işlevindeki [await](../operators/await-operator.md) işlecini kullanabilirsiniz. Denetim, işlevdeki bir `Await` ifadeye ulaştığında `Async` Denetim çağırana döner ve beklenen görev tamamlanana kadar işlevdeki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme işlevinde çalışmaya çalışabilir.

> [!NOTE]
> Bir `Async` yordam, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağrı yapana geri döner veya `Async` yordamın sonuna, hangisi önce gerçekleşirse olur.

Bir `Async` işlev, veya dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> . `Async`Bir dönüş türüne sahip bir işlev örneği <xref:System.Threading.Tasks.Task%601> aşağıda verilmiştir.

Bir `Async` Işlev [ByRef](../modifiers/byref.md) parametreleri bildiremez.

Bir [alt ifade](sub-statement.md) , `Async` değiştiriciyle de işaretlenebilir. Bu, öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır. Bir yordam beklenemez `Async` `Sub` ve bir yordamın çağıranu `Async` `Sub` yordam tarafından oluşturulan özel durumları yakalayamaz `Sub` .

İşlevler hakkında daha fazla bilgi için `Async` bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Yineleyici Işlevleri

*Yineleyici* işlevi, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir. Yineleyici işlevi, her öğeyi birer birer döndürmek için [yield](yield-statement.md) ifadesini kullanır. Bir [yield](yield-statement.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır. Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.

Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki](for-each-next-statement.md) ifade.

Yineleyici işlevinin dönüş türü,,, veya olabilir <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .

Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Function` bir yordamın gövdesini oluşturan adı, parametreleri ve kodu bildirmek için bildirimini kullanır `Function` . `ParamArray`Değiştirici, işlevin değişken sayıda bağımsız değişken kabul etmesine olanak sağlar.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, önceki örnekte belirtilen işlevi çağırır.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `DelayAsync` `Async` `Function` öğesinin dönüş türü olan bir <xref:System.Threading.Tasks.Task%601> . `DelayAsync`, `Return` bir tamsayı döndüren bir ifadeye sahiptir. Bu nedenle, işlev bildiriminin `DelayAsync` bir dönüş türüne sahip olması gerekir `Task(Of Integer)` . Dönüş türü olduğundan `Task(Of Integer)` , `Await` ifadesinin içindeki değerlendirmesi `DoSomethingAsync` bir tamsayı oluşturur. Bu bildirimde gösterilmiştir: `Dim result As Integer = Await delayTask` .

`startButton_Click`Yordam bir `Async Sub` yordam örneğidir. `DoSomethingAsync`Bir işlev olduğundan `Async` , `DoSomethingAsync` Aşağıdaki ifadede gösterildiği gibi çağrının görevi beklenmelidir: `Await DoSomethingAsync()` . `startButton_Click` `Sub` Bir ifadesi içerdiğinden yordamın değiştirici ile tanımlanması gerekir `Async` `Await` .

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](sub-statement.md)
- [İşlev Yordamları](../../programming-guide/language-features/procedures/function-procedures.md)
- [Parametre Listesi](parameter-list.md)
- [Dim Deyimi](dim-statement.md)
- [Call Deyimi](call-statement.md)
- [Durumunu](of-clause.md)
- [Parametre Dizileri](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordam Sorunlarını Giderme](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [İşlev Ifadesi](../operators/function-expression.md)
