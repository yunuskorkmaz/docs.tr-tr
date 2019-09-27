---
title: Property açıklaması (Visual Basic)
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
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332742"
---
# <a name="property-statement"></a>Property Deyimi

Bir özelliğin adını ve özellik değerini depolamak ve almak için kullanılan özellik yordamlarını bildirir.

## <a name="syntax"></a>Sözdizimi

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

  İsteğe bağlı. Bu özelliğe veya `Get` veya `Set` yordama uygulanan özniteliklerin listesi. Bkz. [öznitelik listesi](attribute-list.md).

- `Default`

  İsteğe bağlı. Bu özelliğin tanımlandığı sınıf veya yapı için varsayılan özellik olduğunu belirtir. Varsayılan Özellikler parametreleri kabul etmeli ve özellik adı belirtilmeden ayarlanabilir ve alınmış olabilir. Özelliği `Default` olarak bildirirseniz, özellik üzerinde veya özellik yordamlarından birinde `Private` kullanamazsınız.

- `accessmodifier`

  @No__t-0 ifadesinde ve `Get` ve `Set` deyimlerinin en üstünde yer alan isteğe bağlıdır. Aşağıdakilerden biri olabilir:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.

- `propertymodifiers`

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

- `ReadOnly`

  İsteğe bağlı. Bkz. [ReadOnly](../modifiers/readonly.md).

- `WriteOnly`

  İsteğe bağlı. Bkz. [WriteOnly](../modifiers/writeonly.md).

- `Iterator`

  İsteğe bağlı. Bkz. [Yineleyici](../modifiers/iterator.md).

- `name`

  Gerekli. Özelliğin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  İsteğe bağlı. Bu özelliğin parametrelerini temsil eden yerel değişken adlarının listesi ve `Set` yordamının olası ek parametreleri. Bkz. [parametre listesi](parameter-list.md).

- `returntype`

  @No__t-0 `On` ise gereklidir. Bu özellik tarafından döndürülen değerin veri türü.

- `Implements`

  İsteğe bağlı. Bu özelliğin, her biri bu özelliğin kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla özelliği uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).

- `implementslist`

  @No__t-0 sağlanırsa gereklidir. Uygulanan özelliklerin listesi.

  `implementedproperty [ , implementedproperty ... ]`

  Her `implementedproperty` aşağıdaki söz dizimi ve bölümlere sahiptir:

  `interface.definedname`

  |Bölümüyle|Açıklama|
  |---|---|
  |`interface`|Gerekli. Bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirimin adı.|
  |`definedname`|Gerekli. @No__t-0 ' da tanımlanan özelliğin adı.|

- `Get`

  İsteğe bağlı. Özellik `ReadOnly` olarak işaretlenmişse gereklidir. Özelliğin değerini döndürmek için kullanılan `Get` özellik yordamını başlatır.  @No__t-0 deyimleri [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.

- `statements`

  İsteğe bağlı. @No__t-0 veya `Set` yordamı içinde çalıştırılacak deyimler bloğu.

- `End Get`

  @No__t-0 özellik yordamını sonlandırır.

- `Set`

  İsteğe bağlı. Özellik `WriteOnly` olarak işaretlenmişse gereklidir. Özelliğin değerini depolamak için kullanılan `Set` özellik yordamını başlatır.  @No__t-0 deyimleri [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.

- `End Set`

  @No__t-0 özellik yordamını sonlandırır.

- `End Property`

  Bu özelliğin tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

@No__t-0 ifadesinde bir özelliğin bildirimi tanıtılmaktadır. Bir özellik `Get` yordamına (salt okuma), bir `Set` yordama (salt yazılır) veya her ikisine (okuma-yazma) sahip olabilir. Otomatik uygulanan bir özellik kullanırken `Get` ve `Set` yordamını atlayabilirsiniz. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

@No__t-0 ' i yalnızca sınıf düzeyinde kullanabilirsiniz. Yani bir özelliğin *Bildirim bağlamı* bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, ad alanı, yordam veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Varsayılan olarak, Özellikler ortak erişim kullanır. Bir özelliğin erişim düzeyini `Property` ifadesinde bir erişim değiştiricisiyle ayarlayabilir ve isteğe bağlı olarak özellik yordamlarından birini daha kısıtlayıcı bir erişim düzeyine ayarlayabilirsiniz.

Visual Basic, özellik atamaları sırasında bir parametreyi `Set` yordamına geçirir. @No__t-0 için bir parametre belirtmezseniz, tümleşik geliştirme ortamı (IDE), `value` adlı örtük bir parametre kullanır. Bu parametre, özelliğine atanacak değeri tutar. Genellikle bu değeri özel bir yerel değişkende depolar ve `Get` yordamı çağrıldığında bunu döndürün.

## <a name="rules"></a>Kurallar

- **Karışık erişim düzeyleri.** Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak `Get` veya `Set` yordamı için farklı bir erişim düzeyi belirtebilirsiniz, ancak her ikisini birden belirtemezsiniz. Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir. Örneğin, özellik `Friend` olarak bildirilirse, `Set` yordamını `Private` değil, `Public` olarak bildirebilirsiniz.

  @No__t-0 veya `WriteOnly` özelliği tanımlıyorsanız, tek özellik yordamı (sırasıyla `Get` veya `Set`) tüm özelliği temsil eder. Bu tür bir yordam için farklı bir erişim düzeyi bildiremezsiniz, çünkü bu özellik için iki erişim düzeyi ayarlayacaktı.

- **Dönüş türü.** @No__t-0 bildirimi, döndürdüğü değerin veri türünü bildirebilirler. Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.

  @No__t-0 belirtmezseniz, özellik `Object` döndürür.

- **Paylaşır.** Bu özellik `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının `Class` veya `Structure` ifadesiyle hemen sonra bir `Implements` ifadesine sahip olması gerekir. @No__t-0 ifadesinin `implementslist` ' de belirtilen her arabirimi içermesi gerekir. Ancak, `Property` ' ı tanımlayan adın (`definedname` ' de), bu özelliğin adıyla aynı olması gerekmez (`name` ' de).

## <a name="behavior"></a>Davranış

- **Bir özellik yordamından döndürülüyor.** @No__t-0 veya `Set` yordamı çağıran koda döndüğünde, yürütme onu çağıran deyimden sonraki deyimle devam eder.

  @No__t-0 ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur. Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve `Return` deyimlerini karıştırabilirsiniz.

- **Dönüş değeri.** @No__t-0 yordamından bir değer döndürmek için, değeri özellik adına atayabilir ya da bir `Return` ifadesine dahil edebilirsiniz. Aşağıdaki örnek, dönüş değerini `quoteForTheDay` özellik adına atar ve sonra geri dönmek için `Exit Property` ifadesini kullanır.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  @No__t-1 ' e bir değer atamadan `Exit Property` ' ı kullanırsanız, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.

  Aynı anda `Return` deyimleri, `Get` yordam dönüş değeri atar ve yordamdan çıkar. Aşağıdaki örnek bunu gösterir.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir sınıfında bir özelliği bildirir.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Uygulanan Özellikler](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Nesneler ve Sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
- [Get Deyimi](get-statement.md)
- [Set Deyimi](set-statement.md)
- [Parametre Listesi](parameter-list.md)
- [Varsayılan](../modifiers/default.md)
