---
title: Const Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 3b05d4067ef99e03df07d2c316c982051180d961
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382113"
---
# <a name="const-statement-visual-basic"></a>Const Deyimi (Visual Basic)

Bir veya daha fazla sabiti bildirir ve tanımlar.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a>Bölümler

`attributelist`  
İsteğe bağlı. Bu bildirimde belirtilen tüm sabitlere uygulanan özniteliklerin listesi. [Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içinde görüntüleyin.

`accessmodifier`  
İsteğe bağlı. Bu sabitlere hangi kodun erişebileceğini belirtmek için bunu kullanın. [Ortak](../modifiers/public.md), [korumalı](../modifiers/protected.md), [arkadaş](../modifiers/friend.md), [korumalı arkadaş](../modifiers/protected-friend.md), [özel](../modifiers/private.md)veya [özel korumalı](../modifiers/private-protected.md)olabilir.

`Shadows`  
İsteğe bağlı. Bir temel sınıftaki programlama öğesini yeniden bildirmek ve gizlemek için bunu kullanın. Bkz. [gölgeler](../modifiers/shadows.md).

`constantlist`  
Gereklidir. Bu bildirimde bildirildiği sabitlerin listesi.

`constant` `[ ,` `constant` `... ]`

Her birinin `constant` aşağıdaki söz dizimi ve parçaları vardır:

`constantname` `[ As` `datatype` `] =` `initializer`

|Bölüm|Description|
|----------|-----------------|
|`constantname`|Gereklidir. Sabitin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`datatype`|İse gereklidir `Option Strict` `On` . Sabitin veri türü.|
|`initializer`|Gereklidir. Derleme zamanında değerlendirilen ve sabitine atanan ifade.|

## <a name="remarks"></a>Açıklamalar

Uygulamanızda hiçbir değişiklik olmayan bir değer varsa, adlandırılmış bir sabit tanımlayabilir ve bunu bir sabit değer yerine kullanabilirsiniz. Bir ad, bir değerden daha kolay anımsanacak. Sabiti yalnızca bir kez tanımlayabilir ve kodunuzda birçok yerde kullanabilirsiniz. Daha sonraki bir sürümde değeri yeniden tanımlamanız gerekiyorsa, `Const` bir değişiklik yapmak için ihtiyacınız olan tek yerdir.

`Const`Yalnızca modül veya yordam düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir değişken için *Bildirim bağlamı* bir sınıf, yapı, modül, yordam veya blok olmalıdır ve kaynak dosya, ad alanı veya arabirim olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Yerel sabitler (bir yordam içinde) varsayılan olarak genel erişime ve bunlara hiçbir erişim değiştiricilerini kullanamazsınız. Sınıf ve modül üyesi sabitleri (herhangi bir yordam dışında), özel erişim için varsayılan olarak, üye sabitlerinin varsayılan olarak ortak erişimine sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Modül düzeyinde belirtilen bir sabit, herhangi bir yordamın dışında, bir *üye sabiti*; Onu bildiren sınıf, yapı veya modülün bir üyesidir.

  Yordam düzeyinde belirtilen bir sabit, yerel bir *sabittir*; Bu, onu bildiren yordamın veya bloğun yereldir.

- **Özelliklerine.** Öznitelikleri yerel sabitlere değil yalnızca üye sabitlerine uygulayabilirsiniz. Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel sabitler gibi geçici depolama için anlamlı değildir.

- **İlerine.** Varsayılan olarak, tüm sabitler `Shared` , `Static` ve ' dir `ReadOnly` . Bir sabit bildirirken bu anahtar sözcüklerden hiçbirini kullanamazsınız.

  Yordam düzeyinde, `Shadows` Yerel sabitleri bildirmek için veya herhangi bir erişim değiştiricilerini kullanamazsınız.

- **Birden çok sabit.** Aynı bildirim ifadesinde, her birinin bölümünü belirterek, birkaç sabit belirtebilirsiniz `constantname` . Birden çok sabit virgülle ayrılır.

## <a name="data-type-rules"></a>Veri türü kuralları

- **Veri türleri.** `Const`İfade, bir değişkenin veri türünü bildirebilirler. Herhangi bir veri türü veya bir numaralandırma adı belirtebilirsiniz.

- **Varsayılan tür.** Belirtmezseniz `datatype` , sabit, veri türünü alır `initializer` . Hem hem de belirtirseniz `datatype` `initializer` , veri türü `initializer` öğesine dönüştürülebilir olmalıdır `datatype` . Ne yoksa `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak olur `Object` .

- **Farklı türler.** Bildirdiğiniz her değişken için ayrı bir yan tümce kullanarak, farklı sabitler için farklı veri türleri belirtebilirsiniz `As` . Ancak, ortak bir yan tümce kullanarak aynı türde olan birkaç sabiti bildiremezsiniz `As` .

- **Başlatılmasında.** ' De her bir sabit değeri başlatmalısınız `constantlist` . `initializer`Sabitine atanacak bir ifade sağlamak için kullanırsınız. İfade, herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve önceden tanımlanmış sabit listesi üyeleri olabilir. Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.

  İçindeki değişkenleri veya işlevleri kullanamazsınız `initializer` . Ancak, ve gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz `CByte` `CShort` . `AscW` `String` `Char` Derleme zamanında değerlendirilebileceğinizden, bu değeri bir sabit veya bağımsız değişkenle birlikte çağırırsanız de kullanabilirsiniz.

## <a name="behavior"></a>Davranış

- **Kapsam.** Yerel sabitler yalnızca kendi yordamının veya bloğunun içinden erişilebilir. Üye sabitlerine, sınıfları, yapısı veya modülü içinde herhangi bir yerden erişilebilir.

- **Yeter.** Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabitinin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir. Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel sabitlere başvuramaz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Const` sabit değer değerlerinin yerine kullanılacak sabitleri bildirmek için bildirimini kullanır.

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a>Örnek

Veri türü ile bir sabit tanımlarsanız `Object` , Visual Basic derleyici bunun yerine öğesinin türünü sağlar `initializer` `Object` . Aşağıdaki örnekte, sabit, `naturalLogBase` çalışma zamanı türüne sahiptir `Decimal` .

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

Önceki örnekte,, <xref:System.Type.ToString%2A> <xref:System.Type> ' a dönüştürülemediğinden, [GetType işlecinin](../operators/gettype-operator.md)döndürdüğü nesne üzerinde yöntemi kullanılmaktadır <xref:System.Type> `String` `CStr` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum Deyimi](enum-statement.md)
- [#Const Yönergesi](../directives/const-directive.md)
- [Dim Deyimi](dim-statement.md)
- [ReDim Deyimi](redim-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Sabitler ve numaralandırmalar](../../programming-guide/language-features/constants-enums/index.md)
- [Sabitler ve numaralandırmalar](../constants-and-enumerations.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
