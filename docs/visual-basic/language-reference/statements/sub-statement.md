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
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583197"
---
# <a name="sub-statement-visual-basic"></a>Sub Deyimi (Visual Basic)

Bir `Sub` yordamını tanımlayan adı, parametreleri ve kodu bildirir.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).

- `Partial`

  İsteğe bağlı. Kısmi bir yöntemin tanımını gösterir. Bkz. [kısmi Yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  İsteğe bağlı. Aşağıdakilerden biri olabilir:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.

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

  İsteğe bağlı. Bkz. [paylaşılan](../modifiers/shared.md).

- `Shadows`

  İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).

- `Async`

  İsteğe bağlı. Bkz. [zaman uyumsuz](../modifiers/async.md).

- `name`

  Gerekli. Yordamın adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamının adını `New` anahtar sözcüğüne ayarlayın. Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  İsteğe bağlı. Genel bir yordamın tür parametrelerinin listesi. Bkz. [tür listesi](type-list.md).

- `parameterlist`

  İsteğe bağlı. Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi. Bkz. [parametre listesi](parameter-list.md).

- `Implements`

  İsteğe bağlı. Bu yordamın, her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla `Sub` yordamlarını uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).

- `implementslist`

  @No__t_0 sağlanırsa gereklidir. Uygulanan `Sub` yordamlarının listesi.

  `implementedprocedure [ , implementedprocedure ... ]`

  Her `implementedprocedure` aşağıdaki söz dizimi ve bölümlere sahiptir:

  `interface.definedname`

  |Bölümüyle|Açıklama|
  |---|---|
  |`interface`|Gerekli. Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.|
  |`definedname`|Gerekli. Yordamın `interface` tanımladığı ad.|

- `Handles`

  İsteğe bağlı. Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir. Bkz. [işleyiciler](handles-clause.md).

- `eventlist`

  @No__t_0 sağlanırsa gereklidir. Bu yordamın işleyeceği olayların listesi.

  `eventspecifier [ , eventspecifier ... ]`

  Her `eventspecifier` aşağıdaki söz dizimi ve bölümlere sahiptir:

  `eventvariable.event`

  |Bölümüyle|Açıklama|
  |---|---|
  |`eventvariable`|Gerekli. Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.|
  |`event`|Gerekli. Bu yordamın işleyeceği olayın adı.|

- `statements`

  İsteğe bağlı. Bu yordam içinde çalıştırılacak deyimler bloğu.

- `End Sub`

  Bu yordamın tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

Tüm yürütülebilir kodların bir yordamın içinde olması gerekir. Çağırma koduna bir değer döndürmek istemediğiniz zaman `Sub` prosedürü kullanın. Bir değer döndürmek istediğinizde `Function` prosedürü kullanın.

## <a name="defining-a-sub-procedure"></a>Bir alt yordam tanımlama

Bir `Sub` yordamını yalnızca modül düzeyinde tanımlayabilirsiniz. Bir alt yordamın bildirim bağlamı, bu nedenle bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

yordamları, genel erişim için varsayılan `Sub`. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

Yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Class` veya `Structure` deyimlerinden hemen sonraki bir `Implements` ifadesine sahip olması gerekir. @No__t_0 deyimin `implementslist` belirtilen her arabirimi içermesi gerekir. Ancak, bir arabirimin `Sub` tanımladığı adın (`definedname`) bu yordamın adıyla eşleşmesi gerekmez (`name`).

## <a name="returning-from-a-sub-procedure"></a>Bir alt yordamdan dönme

Bir `Sub` yordamı çağıran koda döndüğünde, yürütme onu çağıran deyimden sonra ifadesiyle devam eder.

Aşağıdaki örnekte, bir `Sub` yordamından döndürülen bir dönüş gösterilmektedir.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

@No__t_0 ve `Return` deyimleri, bir `Sub` yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Sub` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Sub` ve `Return` deyimlerini karıştırabilirsiniz.

## <a name="calling-a-sub-procedure"></a>Bir alt yordamı çağırma

Bir ifadede yordam adını kullanarak bir `Sub` yordamı çağırır ve ardından bu adı parantez içindeki bağımsız değişken listesiyle takip edersiniz. Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz. Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.

@No__t_0 yordamı ve `Function` yordamı parametrelere sahip olabilir ve bir dizi deyim gerçekleştirebilir. Ancak, bir `Function` yordam bir değer döndürür ve bir `Sub` yordamı değildir. Bu nedenle, bir ifadede `Sub` yordamı kullanamazsınız.

Bir `Sub` yordamını çağırdığınızda `Call` anahtar sözcüğünü kullanabilirsiniz, ancak bu anahtar sözcük çoğu kullanımlar için önerilmez. Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).

Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler. Bu nedenle, bağımsız değişken listeniz diğer yordamları çağıran ifadeler içeriyorsa, bu ifadelerin belirli bir sırada çağrılacağını varsaymamalıdır.

## <a name="async-sub-procedures"></a>Zaman uyumsuz alt yordamlar

Async özelliğini kullanarak, zaman uyumsuz işlevleri açık geri çağırmaları kullanmadan çağırabilir veya kodunuzu birden çok işlev veya lambda ifadesine el ile böedebilirsiniz.

Bir yordamı [zaman uyumsuz](../modifiers/async.md) değiştiriciyle işaretlerseniz, yordamda [await](../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanabilirsiniz. Denetim, `Async` yordamındaki bir `Await` ifadesine ulaştığında denetim çağırana döner ve beklenen görev tamamlanana kadar yordamdaki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme yordamda çalışmaya çalışabilir.

> [!NOTE]
> Bir `Async` yordamı, henüz tamamlanmamış ilk beklenen nesne ile karşılaşıldığında ya da `Async` yordamının sonuna ulaşıldığında, hangisi önce gerçekleşirse arayan öğesine geri döner.

Ayrıca, `Async` değiştiricisiyle bir [Işlev ifadesini](function-statement.md) işaretleyebilirsiniz. @No__t_0 işlevi <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task> dönüş türüne sahip olabilir. Bu konunun ilerleyen kısımlarında yer alan örnek, <xref:System.Threading.Tasks.Task%601> dönüş türüne sahip bir `Async` işlevi gösterir.

`Async` `Sub` yordamlar öncelikle bir değerin döndürülmeyeceğini olay işleyicileri için kullanılır. Bir `Async` `Sub` yordamı beklenemez ve bir `Async` `Sub` yordamının çağıranı `Sub` yordamının oluşturduğunu özel durumları yakalayamaz.

@No__t_0 yordam [ByRef](../modifiers/byref.md) parametreleri bildiremez.

@No__t_0 yordamları hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `Sub` yordamının gövdesini oluşturan adı, parametreleri ve kodu tanımlamak için `Sub` ifadesini kullanır.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `DelayAsync` dönüş türü <xref:System.Threading.Tasks.Task%601> olan bir `Async` `Function`. `DelayAsync`, bir tamsayı döndüren bir `Return` bildirimine sahiptir. Bu nedenle `DelayAsync` işlev bildirimi `Task(Of Integer)` dönüş türüne sahip olmalıdır. Dönüş türü `Task(Of Integer)` olduğu için, aşağıdaki deyimde gösterildiği gibi, `DoSomethingAsync` `Await` ifadenin değerlendirmesi bir tamsayı üretir: `Dim result As Integer = Await delayTask`.

@No__t_0 yordam bir `Async Sub` yordamının bir örneğidir. @No__t_0 bir `Async` işlevi olduğundan, aşağıdaki ifadede gösterildiği gibi, `DoSomethingAsync` çağrısı için de beklenen bir görev olmalıdır: `Await DoSomethingAsync()`. Bir `Await` ifadesi içerdiğinden `startButton_Click` `Sub` yordamının `Async` değiştiricisi ile tanımlanması gerekir.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](implements-statement.md)
- [Function Deyimi](function-statement.md)
- [Parametre Listesi](parameter-list.md)
- [Dim Deyimi](dim-statement.md)
- [Call Deyimi](call-statement.md)
- [Durumunu](of-clause.md)
- [Parametre Dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordam Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Kısmi Yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
