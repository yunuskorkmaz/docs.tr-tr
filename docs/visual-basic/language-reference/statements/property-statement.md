---
description: 'Daha fazla bilgi edinin: Özellik açıklaması'
title: Property Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 95f2ac1f993fc8698d2033dfe50d925cd55a7dc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741399"
---
# <a name="property-statement"></a>Property Deyimi

Bir özelliğin adını ve özellik değerini depolamak ve almak için kullanılan özellik yordamlarını bildirir.

## <a name="syntax"></a>Syntax

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bu özellik veya yordam için uygulanan özniteliklerin listesi `Get` `Set` . Bkz. [öznitelik listesi](attribute-list.md).

- `Default`

  İsteğe bağlı. Bu özelliğin tanımlandığı sınıf veya yapı için varsayılan özellik olduğunu belirtir. Varsayılan Özellikler parametreleri kabul etmeli ve özellik adı belirtilmeden ayarlanabilir ve alınmış olabilir. Özelliğini olarak bildirirseniz `Default` , özelliğinde `Private` veya özellik yordamlarından birinde kullanamazsınız.

- `accessmodifier`

  `Property`Deyimde ve `Get` ve deyimlerinin en üzerinde isteğe bağlı `Set` . Aşağıdakilerden biri olabilir:

  - [Genel](../modifiers/public.md)

  - [Korunamadı](../modifiers/protected.md)

  - [Arkadaş](../modifiers/friend.md)

  - [Özel](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Özel korumalı](../modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.

- `propertymodifiers`

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

- `ReadOnly`

  İsteğe bağlı. Bkz. [ReadOnly](../modifiers/readonly.md).

- `WriteOnly`

  İsteğe bağlı. Bkz. [WriteOnly](../modifiers/writeonly.md).

- `Iterator`

  İsteğe bağlı. Bkz. [Yineleyici](../modifiers/iterator.md).

- `name`

  Gereklidir. Özelliğin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  İsteğe bağlı. Bu özelliğin parametrelerini ve yordamın olası ek parametrelerini temsil eden yerel değişken adlarının listesi `Set` . Bkz. [parametre listesi](parameter-list.md).

- `returntype`

  İse gereklidir `Option Strict` `On` . Bu özellik tarafından döndürülen değerin veri türü.

- `Implements`

  İsteğe bağlı. Bu özelliğin, her biri bu özelliğin kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla özelliği uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).

- `implementslist`

  Sağlanırsa gereklidir `Implements` . Uygulanan özelliklerin listesi.

  `implementedproperty [ , implementedproperty ... ]`

  Her birinin `implementedproperty` aşağıdaki söz dizimi ve parçaları vardır:

  `interface.definedname`

  |Bölüm|Description|
  |---|---|
  |`interface`|Gereklidir. Bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirimin adı.|
  |`definedname`|Gereklidir. Özelliğin tanımlandığı ad `interface` .|

- `Get`

  İsteğe bağlı. Özellik işaretlenmişse gereklidir `ReadOnly` . `Get`Özelliğin değerini döndürmek için kullanılan bir özellik yordamını başlatır.  `Get`İfade, [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.

- `statements`

  İsteğe bağlı. Or yordamı içinde çalıştırılacak deyimler bloğu `Get` `Set` .

- `End Get`

  `Get`Özellik yordamını sonlandırır.

- `Set`

  İsteğe bağlı. Özellik işaretlenmişse gereklidir `WriteOnly` . `Set`Özelliğin değerini depolamak için kullanılan bir özellik yordamını başlatır.  `Set`İfade, [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.

- `End Set`

  `Set`Özellik yordamını sonlandırır.

- `End Property`

  Bu özelliğin tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

`Property`İfade bir özelliğin bildirimini tanıtır. Bir özellik bir `Get` yordama (salt okuma), bir `Set` yordama (salt yazılır) veya her ikisine (okuma-yazma) sahip olabilir. `Get` `Set` Otomatik uygulanan bir özellik kullanırken ve yordamını atlayabilirsiniz. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

`Property`Yalnızca sınıf düzeyinde kullanabilirsiniz. Yani bir özelliğin *Bildirim bağlamı* bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, ad alanı, yordam veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Varsayılan olarak, Özellikler ortak erişim kullanır. Bir özelliğin erişim düzeyini deyimdeki bir erişim değiştiricisiyle ayarlayabilirsiniz `Property` ve isteğe bağlı olarak özellik yordamlarından birini daha kısıtlayıcı bir erişim düzeyine ayarlayabilirsiniz.

Visual Basic, `Set` özellik atamaları sırasında yordama bir parametre geçirir. İçin bir parametre belirtmezseniz `Set` , tümleşik geliştirme ortamı (IDE) adlı örtülü bir parametre kullanır `value` . Bu parametre, özelliğine atanacak değeri tutar. Genellikle bu değeri özel bir yerel değişkende depoluyordu ve yordam her çağrıldığında döndürülür `Get` .

## <a name="rules"></a>Kurallar

- **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz. Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özelliği bildirilirse, `Friend` `Set` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .

  `ReadOnly`Veya `WriteOnly` özelliğini tanımlıyorsanız, tek özellik yordamı ( `Get` veya `Set` sırasıyla) tüm özelliği temsil eder. Bu tür bir yordam için farklı bir erişim düzeyi bildiremezsiniz, çünkü bu özellik için iki erişim düzeyi ayarlayacaktı.

- **Dönüş türü.** `Property`İfade, döndürdüğü değerin veri türünü bildirebilirler. Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.

  Belirtmezseniz `returntype` , özelliği döndürür `Object` .

- **Paylaşır.** Bu özellik `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Implements` veya bildiriminin hemen ardından bir ifadeye sahip olması `Class` gerekir `Structure` . `Implements`Deyimin içinde belirtilen her arabirimi içermesi gerekir `implementslist` . Ancak, bir arabirimin `Property` (içinde) tanımladığı adın `definedname` Bu özelliğin adıyla aynı olması gerekmez (içinde `name` ).

## <a name="behavior"></a>Davranış

- **Bir özellik yordamından döndürülüyor.** Ya da `Get` `Set` yordamı çağıran koda döndüğünde, yürütme onu çağıran deyimden sonraki deyimle devam eder.

  `Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .

- **Dönüş değeri.** Bir yordamdan bir değer döndürmek için `Get` , değeri özellik adına atayabilir veya bir deyime dahil edebilirsiniz `Return` . Aşağıdaki örnek, dönüş değerini özellik adına atar `quoteForTheDay` ve ardından `Exit Property` döndürmek için ifadesini kullanır.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  `Exit Property`' A değer atamakla kullanırsanız `name` , `Get` yordam özelliğin veri türü için varsayılan değeri döndürür.

  `Return`Aynı anda yer aldığı ifade, `Get` yordam dönüş değerini atar ve yordamdan çıkar. Aşağıdaki örnek bunu gösterir.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir sınıfında bir özelliği bildirir.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Uygulanan Özellikler](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
- [Get Deyimi](get-statement.md)
- [Set deyimleri](set-statement.md)
- [Parametre Listesi](parameter-list.md)
- [Varsayılanını](../modifiers/default.md)
