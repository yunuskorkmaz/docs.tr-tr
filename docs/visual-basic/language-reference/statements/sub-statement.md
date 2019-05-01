---
title: Sub Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: ab94865f4881b40b38f67eb40d2f9fa2e1982af8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783844"
---
# <a name="sub-statement-visual-basic"></a>Sub Deyimi (Visual Basic)

Adı, parametreleri ve kodu tanımlayan bildirir bir `Sub` yordamı.

## <a name="syntax"></a>Sözdizimi

```
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bkz: [öznitelik listesi](attribute-list.md).

- `Partial`

  İsteğe bağlı. Kısmi bir yöntemin tanımını gösterir. Bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  İsteğe bağlı. Bkz: [paylaşılan](../modifiers/shared.md).

- `Shadows`

  İsteğe bağlı. Bkz: [Shadows](../modifiers/shadows.md).

- `Async`

  İsteğe bağlı. Bkz: [zaman uyumsuz](../modifiers/async.md).

- `name`

  Gerekli. Yordamın adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Bir sınıf için bir oluşturucu yordam oluşturmak için kümesinin adı bir `Sub` yordama `New` anahtar sözcüğü. Daha fazla bilgi için [nesne ömrü: Nesneler nasıl oluşturulur ve imha](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  İsteğe bağlı. Genel bir yordam için tür parametreleri listesi. Bkz: [türü listesinde](type-list.md).

- `parameterlist`

  İsteğe bağlı. Bu yordamı parametrelerini temsil eden yerel değişken adlarının listesi. Bkz: [parametre listesi](parameter-list.md).

- `Implements`

  İsteğe bağlı. Bu yordam bir veya daha fazla uyguladığını belirtir `Sub` yordamları, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim içinde tanımlanmış her biri. Bkz: [uygulayan deyimi](implements-statement.md).

- `implementslist`

  Gerekli if `Implements` sağlanır. Listesi `Sub` uygulanmakta olan yordamlar.

  `implementedprocedure [ , implementedprocedure ... ]`

  Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:

  `interface.definedname`

  |Bölümü|Açıklama|
  |---|---|
  |`interface`|Gerekli. Bu yordam tarafından uygulanan arabirimin adını sınıf veya yapı içeren.|
  |`definedname`|Gerekli. Ad tarafından yordamı tanımlanan `interface`.|

- `Handles`

  İsteğe bağlı. Bu yordam, bir veya daha fazla belirli olayları işleyebileceğini belirtir. Bkz: [işler](handles-clause.md).

- `eventlist`

  Gerekli if `Handles` sağlanır. Bu yordamı işleme olayların listesi.

  `eventspecifier [ , eventspecifier ... ]`

  Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:

  `eventvariable.event`

  |Bölümü|Açıklama|
  |---|---|
  |`eventvariable`|Gerekli. Nesne değişkeni sınıfın veya olayı yükselten yapı veri türü ile bildirilmiş.|
  |`event`|Gerekli. Bu yordamı işleme olayın adı.|

- `statements`

  İsteğe bağlı. Bu yordam içinde çalıştırılacak deyimler bloğunu.

- `End Sub`

  Bu yordamın tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

Tüm yürütülebilir kod yordam içinde olmalıdır. Kullanım bir `Sub` çağrıldığı koda bir değer döndürmesi istemediğinizde yordamı. Kullanım bir `Function` yordamı, bir değer döndürmek istediğinizde.

## <a name="defining-a-sub-procedure"></a>Bir alt yordam tanımlama

Tanımlayabileceğiniz bir `Sub` yordamı yalnızca Modül düzeyinde. Bir alt yordam bildirimi bağlamı, bu nedenle, bir sınıf, yapı, modül veya bir arabirim olmalıdır ve bir kaynak dosyası, bir ad alanı, bir yordam veya bir bloğu olamaz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

`Sub` yordamları varsayılan genel erişim için. Erişim değiştiricileri kullanarak, kullanıcıların erişim düzeylerini ayarlayabilirsiniz.

Yordamı kullanıyorsa `Implements` anahtar sözcüğü, kapsayan sınıf veya yapı olmalıdır bir `Implements` deyim indisinin hemen ardından kendi `Class` veya `Structure` deyimi. `Implements` Deyimi, belirtilen her bir arabirime içermelidir `implementslist`. Ancak, bir arabirim tarafından tanımlayan adı `Sub` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).

## <a name="returning-from-a-sub-procedure"></a>Bir alt yordamdan döndürme

Olduğunda bir `Sub` yordamı çağıran koda döndürür, yürütme adlı deyiminden sonraki ile devam eder.

Aşağıdaki örnek, geri döndürme gösterir. bir `Sub` yordamı.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub` Ve `Return` deyimleri neden hemen çıkılmadan bir `Sub` yordamı. Herhangi bir sayıda `Exit Sub` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Sub` ve `Return` deyimleri.

## <a name="calling-a-sub-procedure"></a>Bir alt yordam çağırma

Çağrısı bir `Sub` yordam adı bir deyimde kullanarak ve ardından bu ada sahip, bağımsız değişken listesi parantez içinde aşağıdaki yordamı. Herhangi bir bağımsız değişkeni belirtmezseniz ayraçları atlayabilirsiniz. Ancak, kodunuz her zaman parantezler eklerseniz daha okunabilir olur.

A `Sub` yordam ve `Function` yordam parametreleri ve bir dizi deyim gerçekleştirin. Ancak, bir `Function` yordamı döndürür bir değer ve bir `Sub` yordamı değil. Bu nedenle, kullanamazsınız bir `Sub` yordamda bir ifade.

Kullanabileceğiniz `Call` çağırdığınızda anahtar sözcüğü bir `Sub` yordamı, ancak bu anahtar sözcüğü birçok kullanım için önerilmez. Daha fazla bilgi için [Call deyimi](call-statement.md).

Visual Basic, aritmetik ifadeler iç verimliliğini artırmak için bazen yeniden düzenler. Diğer yordamlar çağrı ifadeleri, bağımsız değişken listesi içeriyorsa, bu nedenle, söz konusu ifadelerden belirli bir sırada çağrılacak varsayılır olmamalıdır.

## <a name="async-sub-procedures"></a>Zaman uyumsuz alt yordamlar

Zaman uyumsuz özelliğini kullanarak, açık geri çağırmaları kullanarak veya kodunuzun birden çok işlevleri veya lambda ifadelerinde el ile bölme olmadan zaman uyumsuz işlevleri çağırabilirsiniz.

Bir yordam ile işaretlerseniz [zaman uyumsuz](../modifiers/async.md) kullanabileceğiniz değiştiricisi [Await](../../../visual-basic/language-reference/operators/await-operator.md) yordamda işleci. Ulaştığında denetlemek bir `Await` ifadesinde `Async` yordam, Denetim çağırana döner ve awaited görevi tamamlanıncaya kadar yordamı ediyor askıya alınır. Görev tamamlandığında, yürütme yordamda devam edebilir.

> [!NOTE]
> Bir `Async` yordamı döndürür henüz tam olmadığı ya da ilk beklenen nesne karşılaşıldığında çağıran ya da sonunda `Async` yordamı ulaşıldığında, hangisi daha önce gerçekleşirse.

Ayrıca işaretleyebilirsiniz bir [Function deyimi](function-statement.md) ile `Async` değiştiricisi. Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>. Bu konuda gösteren bir örnek daha sonra söz bir `Async` dönüş türü olan işlev <xref:System.Threading.Tasks.Task%601>.

`Async` `Sub` yordamları, burada bir değer döndürülemez için olay işleyicileri, öncelikli olarak kullanılır. Bir `Async` `Sub` yordamı beklenemez ve çağıran bir `Async` `Sub` yordamı catch özel durumları olamaz, `Sub` yordam oluşturur.

Bir `Async` yordamı herhangi bildiremez [ByRef](../modifiers/byref.md) parametreleri.

Hakkında daha fazla bilgi için `Async` prosedürler [Async ve Await ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda akış kontrolü](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte `Sub` adı, parametreleri ve gövdesini kodunu tanımlamak için deyimi bir `Sub` yordamı.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `DelayAsync` olduğu bir `Async` `Function` dönüş türü olan <xref:System.Threading.Tasks.Task%601>. `DelayAsync` sahip bir `Return` deyimi bir tamsayı döndürür. Bu nedenle, işlev bildirimi `DelayAsync` dönüş türüne sahip olmalıdır `Task(Of Integer)`. Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi bir tamsayı üretir: `Dim result As Integer = Await delayTask`.

`startButton_Click` Yordamdır örneği bir `Async Sub` yordamı. Çünkü `DoSomethingAsync` olduğu bir `Async` işlevi, görev için yapılan çağrının `DoSomethingAsync` , aşağıdaki deyimi gösterildiği gibi beklenmesini gerekir: `Await DoSomethingAsync()`. `startButton_Click` `Sub` Yordamı ile tanımlanmalıdır `Async` değiştiricisi olduğundan bir `Await` ifade.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](implements-statement.md)
- [Function Deyimi](function-statement.md)
- [Parametre Listesi](parameter-list.md)
- [Dim Deyimi](dim-statement.md)
- [Call Deyimi](call-statement.md)
- [,](of-clause.md)
- [Parametre Dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordam Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Kısmi Yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
