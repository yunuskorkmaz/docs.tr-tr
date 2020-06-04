---
title: Sub Deyimi
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
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404180"
---
# <a name="sub-statement-visual-basic"></a>Sub Deyimi (Visual Basic)

Bir yordamı tanımlayan adı, parametreleri ve kodu bildirir `Sub` .

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

  İsteğe bağlı. Kısmi bir yöntemin tanımını gösterir. Bkz. [kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md).

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

- `name`

  Gereklidir. Yordamın adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md). Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamın adını `New` anahtar sözcüğe ayarlayın. Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  İsteğe bağlı. Genel bir yordamın tür parametrelerinin listesi. Bkz. [tür listesi](type-list.md).

- `parameterlist`

  İsteğe bağlı. Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi. Bkz. [parametre listesi](parameter-list.md).

- `Implements`

  İsteğe bağlı. Bu yordamın `Sub` , her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla yordam uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).

- `implementslist`

  Sağlanırsa gereklidir `Implements` . `Sub`Uygulanan yordamların listesi.

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

  İsteğe bağlı. Bu yordam içinde çalıştırılacak deyimler bloğu.

- `End Sub`

  Bu yordamın tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

Tüm yürütülebilir kodların bir yordamın içinde olması gerekir. `Sub`Çağırma koduna bir değer döndürmek istemediğinizde bir yordam kullanın. Bir `Function` değer döndürmek istediğinizde bir yordam kullanın.

## <a name="defining-a-sub-procedure"></a>Bir alt yordam tanımlama

Bir `Sub` yordamı yalnızca modül düzeyinde tanımlayabilirsiniz. Bir alt yordamın bildirim bağlamı, bu nedenle bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

`Sub`yordamlar, genel erişim için varsayılan olarak. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

Yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Implements` veya ifadesiyle hemen sonraki bir deyime sahip olması gerekir `Class` `Structure` . `Implements`İfadesinin içinde belirtilen her arabirimi içermesi gerekir `implementslist` . Ancak, bir arabirimin `Sub` (içinde) tanımladığı adın `definedname` Bu yordamın adıyla eşleşmesi gerekmez (içinde `name` ).

## <a name="returning-from-a-sub-procedure"></a>Bir alt yordamdan dönme

Bir `Sub` yordam çağıran koda döndüğünde, yürütme onu çağıran deyimden sonra ifadesiyle devam eder.

Aşağıdaki örnek bir yordamdan bir dönüş gösterir `Sub` .

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub`Ve `Return` deyimleri, bir yordamdan hemen çıkılmasına neden olur `Sub` . Herhangi bir sayıda `Exit Sub` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Sub` ve deyimlerini karıştırabilirsiniz `Return` .

## <a name="calling-a-sub-procedure"></a>Bir alt yordamı çağırma

`Sub`Bir deyimindeki yordam adını kullanarak bir yordamı çağırır ve ardından bu adı parantez içindeki bağımsız değişken listesiyle takip edersiniz. Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz. Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.

Bir `Sub` yordam ve `Function` yordam parametrelere sahip olabilir ve bir dizi deyim gerçekleştirebilir. Ancak, bir `Function` yordam bir değer döndürür ve bir `Sub` yordam değildir. Bu nedenle, bir ifadede bir `Sub` yordam kullanamazsınız.

`Call`Bir yordamı çağırdığınızda anahtar sözcüğünü kullanabilirsiniz `Sub` , ancak bu anahtar sözcük çoğu kullanımlar için önerilmez. Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).

Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler. Bu nedenle, bağımsız değişken listeniz diğer yordamları çağıran ifadeler içeriyorsa, bu ifadelerin belirli bir sırada çağrılacağını varsaymamalıdır.

## <a name="async-sub-procedures"></a>Zaman uyumsuz alt yordamlar

Async özelliğini kullanarak, zaman uyumsuz işlevleri açık geri çağırmaları kullanmadan çağırabilir veya kodunuzu birden çok işlev veya lambda ifadesine el ile böedebilirsiniz.

Bir yordamı [zaman uyumsuz](../modifiers/async.md) değiştiriciyle işaretlerseniz, yordamda [await](../operators/await-operator.md) işlecini kullanabilirsiniz. Denetim, yordamda bir `Await` ifadeye ulaştığında `Async` Denetim çağırana döner ve beklenen görev tamamlanana kadar yordamdaki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme yordamda çalışmaya çalışabilir.

> [!NOTE]
> Bir `Async` yordam, henüz tamamlanmamış olan ilk bekleme nesnesine rastlandı veya `Async` yordamın sonuna ulaşıldığında, hangisi önce gerçekleşirse çağıran öğesine geri döner.

Değiştirici ile bir [Işlev ifadesini](function-statement.md) de işaretleyebilirsiniz `Async` . Bir `Async` işlev, veya dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> . Bu konunun ilerleyen kısımlarında yer alan bir örnek `Async` , dönüş türü olan bir işlevi gösterir <xref:System.Threading.Tasks.Task%601> .

`Async``Sub`yordamlar öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır. Bir yordam beklenemez `Async` `Sub` ve bir yordamın çağıranı `Async` `Sub` yordamın aldığı özel durumları yakalayamaz `Sub` .

Bir `Async` yordam [ByRef](../modifiers/byref.md) parametreleri bildiremez.

Yordamlar hakkında daha fazla bilgi için `Async` bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Sub` bir yordamın gövdesini oluşturan adı, parametreleri ve kodu tanımlamak için ifadesini kullanır `Sub` .

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `DelayAsync` `Async` `Function` öğesinin dönüş türü olan bir <xref:System.Threading.Tasks.Task%601> . `DelayAsync`, `Return` bir tamsayı döndüren bir ifadeye sahiptir. Bu nedenle, öğesinin işlev bildirimi `DelayAsync` bir dönüş türüne sahip olmalıdır `Task(Of Integer)` . Dönüş türü olduğu için `Task(Of Integer)` , `Await` içindeki ifadesinin değerlendirmesi `DoSomethingAsync` bir tamsayı oluşturur, çünkü aşağıdaki deyim şunu gösterir: `Dim result As Integer = Await delayTask` .

`startButton_Click`Yordam bir `Async Sub` yordam örneğidir. `DoSomethingAsync`Bir işlev olduğundan `Async` , `DoSomethingAsync` Aşağıdaki ifadede gösterildiği gibi çağrının görevi beklenmelidir: `Await DoSomethingAsync()` . `startButton_Click` `Sub` Bir ifadesi içerdiğinden yordamın değiştirici ile tanımlanması gerekir `Async` `Await` .

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](implements-statement.md)
- [Function Deyimi](function-statement.md)
- [Parametre Listesi](parameter-list.md)
- [Dim Deyimi](dim-statement.md)
- [Call Deyimi](call-statement.md)
- [Durumunu](of-clause.md)
- [Parametre Dizileri](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Yordam Sorunlarını Giderme](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md)
