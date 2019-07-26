---
title: Visual Basic'de Kapsam
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512857"
---
# <a name="scope-in-visual-basic"></a>Visual Basic'de Kapsam

Belirtilen bir öğenin *kapsamı* , adını nitelemeden veya bir [içeri aktarmalar Ifadesiyle (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)kullanılabilir hale getirmeden başvurabilen tüm kod kümesidir. Bir öğesi aşağıdaki düzeylerin birinde kapsama sahip olabilir:

|Düzey|Açıklama|
|-----------|-----------------|
|Blok kapsamı|Yalnızca bildirildiği kod bloğu içinde kullanılabilir|
|Yordam kapsamı|İçinde bildirildiği yordamın içindeki tüm kodlar için kullanılabilir|
|Modül kapsamı|Bildirildiği modül, sınıf veya yapı içindeki tüm kodlar için kullanılabilir|
|Ad alanı kapsamı|İçinde bildirildiği ad alanındaki tüm kodlar için kullanılabilir|

Bu kapsam düzeyleri en dar (blok) en geniş (ad alanı) arasında ilerleme gösterir; burada *dar kapsam* , nitelendirme olmadan öğeye başvurabilen en küçük kod kümesidir. Daha fazla bilgi için bu sayfadaki "kapsam düzeyleri" başlığına bakın.

## <a name="specifying-scope-and-defining-variables"></a>Kapsam belirtme ve değişkenleri tanımlama

Bir öğenin kapsamını bildirdiğinizde belirtirsiniz. Kapsam aşağıdaki faktörlere bağlı olabilir:

- İçinde öğeyi bildirdiğiniz bölge (blok, yordam, modül, sınıf veya yapı)

- Öğenin bildirimini içeren ad alanı

- Öğesi için bildirdiğiniz erişim düzeyi

Aynı ada ancak farklı kapsama sahip değişkenler tanımladığınızda, bu durum beklenmedik sonuçlara yol açacağından dikkatli olmanız gerekir. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="levels-of-scope"></a>Kapsam düzeyleri

Bir programlama öğesi, bildirdiğiniz bölgenin tamamında kullanılabilir. Aynı bölgedeki tüm kodlar, adını nitelemeden öğesine başvurabilir.

### <a name="block-scope"></a>Blok kapsamı

Blok, aşağıdaki gibi bildirim deyimlerini başlatma ve sonlandırma içinde yer alan deyimler kümesidir:

- `Do` ve `Loop`

- `For`[`Each`] ve`Next`

- `If` ve `End If`

- `Select` ve `End Select`

- `SyncLock` ve `End SyncLock`

- `Try` ve `End Try`

- `While` ve `End While`

- `With` ve `End With`

Bir blok içinde bir değişken bildirirseniz, bunu yalnızca bu blok içinde kullanabilirsiniz. Aşağıdaki örnekte, `cube` tamsayı değişkeninin kapsamı ve `End If`arasındaki `If` blokdır ve artık yürütme bloğundan dışarı geçtiğinde başvurursunuz `cube` .

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> Bir değişkenin kapsamı bir blokla sınırlı olsa da, ömrü tamamen yordamın tamamıdır. Yordamı yordam sırasında birden fazla kez girerseniz, her blok değişkeni önceki değerini korur. Böyle bir durumda beklenmedik sonuçlara engel olmak için, bloğun başlangıcında blok değişkenlerini başlatmak uygun değildir.

### <a name="procedure-scope"></a>Yordam kapsamı

Yordam içinde belirtilen bir öğe, bu yordamın dışında kullanılamaz. Yalnızca bildirimi içeren yordam bunu kullanabilir. Bu düzeydeki değişkenler *yerel değişkenler*olarak da bilinir. Onları, [static](../../../../visual-basic/language-reference/modifiers/static.md) anahtar sözcüğüyle veya olmadan [Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bildirirsiniz.

Yordam ve blok kapsamı yakından ilgilidir. Bir yordam içinde bir değişken bildirirseniz, ancak bu yordamın içindeki herhangi bir blok dışında, değişkenini blok kapsamına sahip olarak düşünebilirsiniz; burada blok tüm yordamdır.

> [!NOTE]
> `Static` Değişkenler olsalar bile tüm yerel öğeler, göründükleri yordama özeldir. Bir yordam içinde [Public](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü kullanarak hiçbir öğe bildiremezsiniz.

### <a name="module-scope"></a>Modül kapsamı

Kolaylık olması için, tek vadeli *Modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir. Bildirim ifadesini herhangi bir yordamın veya bloğun dışında, ancak modül, sınıf veya yapı içinde yerleştirerek bu düzeydeki öğeleri bildirebilirsiniz.

Modül düzeyinde bir bildirim yaptığınızda seçtiğiniz erişim düzeyi kapsamı belirler. Modül, sınıf veya yapıyı içeren ad alanı da kapsamı etkiler.

[Özel](../../../../visual-basic/language-reference/modifiers/private.md) erişim düzeyi bildirdiğiniz öğeler, bu modüldeki her yordamda kullanılabilir, ancak farklı bir modüldeki herhangi bir koda uygulanmaz. Modül `Dim` düzeyindeki deyimin `Private` değeri, herhangi bir erişim düzeyi anahtar sözcüğü kullanmıyorsanız varsayılan değerdir. Ancak, `Private` `Dim` bildiriminde anahtar sözcüğünü kullanarak kapsamı ve erişim düzeyini daha belirgin hale getirebilirsiniz.

Aşağıdaki örnekte, modülünde tanımlanan tüm yordamlar dize değişkenine `strMsg`başvurabilir. İkinci yordam çağrıldığında, dize değişkeninin `strMsg` içeriğini bir iletişim kutusunda görüntüler.

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a>Ad alanı kapsamı

Bir öğeyi, [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) veya [Public](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü kullanarak modül düzeyinde bildirirseniz, bu, öğenin bildirildiği ad alanı boyunca tüm yordamlarda kullanılabilir hale gelir. Önceki örnekte yapılan aşağıdaki değişiklikle, dize değişkenine `strMsg` , bildiriminin ad alanı içinde herhangi bir yerde kod eklenebilir.

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

Ad alanı kapsamı iç içe geçmiş ad alanlarını içerir. Ad alanı içinde bulunan bir öğe, bu ad alanı içinde iç içe yerleştirilmiş herhangi bir ad alanı içinde de kullanılabilir.

Projeniz herhangi bir [ad alanı bildirisi](../../../../visual-basic/language-reference/statements/namespace-statement.md)içermiyorsa, projedeki her şey aynı ad alanında bulunur. Bu durumda, ad alanı kapsamı Proje kapsamı olarak düşünülebilir. `Public`bir modül, sınıf veya yapıdaki öğeler, projesine başvuran tüm projeler için de kullanılabilir.

## <a name="choice-of-scope"></a>Kapsam seçimi

Bir değişken bildirdiğinizde, kapsamını seçerken aşağıdaki noktaları göz önünde bulundurmanız gerekir.

### <a name="advantages-of-local-variables"></a>Yerel değişkenlerin avantajları

Yerel değişkenler, aşağıdaki nedenlerden dolayı her türlü geçici hesaplama için iyi bir seçimdir:

- **Ad çakışması engelleme.** Yerel değişken adları çakışmaya karşı savunmasız değildir. Örneğin, adlı `intTemp`bir değişken içeren birkaç farklı yordam oluşturabilirsiniz. Her biri `intTemp` yerel değişken olarak bildirildiği sürece, her yordam yalnızca kendi `intTemp`sürümünü tanır. Herhangi bir yordam, diğer yordamlardan değişkenleri etkilemeden `intTemp` `intTemp` yerel içindeki değeri değiştirebilir.

- **Bellek tüketimi.** Yerel değişkenler yalnızca yordamı çalışırken belleği tüketir. Yordamı çağıran koda geri döndüğünde, belleği serbest bırakılır. Aksine, [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) ve [statik](../../../../visual-basic/language-reference/modifiers/static.md) değişkenler, uygulamanız çalışmayı durdurana kadar bellek kaynaklarını kullanır, bu nedenle onları yalnızca gerekli olduğunda kullanın. Örnek *değişkenleri* , örnekleri mevcut olmaya devam ederken belleği tüketir, bu da yerel değişkenlerden daha az verimlidir, ancak büyük olasılıkla `Shared` veya `Static` değişkenlerinden daha etkilidir.

### <a name="minimizing-scope"></a>Kapsamı küçültme

Genel olarak, herhangi bir değişken veya sabit bildirirken, kapsamı olabildiğince dar hale getirmek için iyi bir programlama uygulamasıdır (blok kapsam en dar olur). Bu, belleğin korunmasına yardımcı olur ve yanlış değişkene başvuran kodunuzun yanlışlıkla yanlış olduğunu en aza indirir. Benzer şekilde, bir değişkeni yalnızca yordam çağrıları arasında değerini korumak gerektiğinde [statik](../../../../visual-basic/language-reference/modifiers/static.md) olacak şekilde bildirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Nasıl yapılır: Bir değişkenin kapsamını denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Visual Basic ömrü](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
