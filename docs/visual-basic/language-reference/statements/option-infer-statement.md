---
title: Option Infer ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 52da5d059369f8f5a85c23d1ed5ade97523a0e78
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582626"
---
# <a name="option-infer-statement"></a>Option Infer Deyimi

Değişkenleri bildirirken yerel tür çıkarımı kullanımını mümkün.

## <a name="syntax"></a>Sözdizimi

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`On`|İsteğe bağlı. Yerel tür çıkarımı etkinleştirilir.|
|`Off`|İsteğe bağlı. Yerel tür çıkarımını devre dışı bırakır.|

## <a name="remarks"></a>Açıklamalar

Bir dosyada `Option Infer` ayarlamak için, dosyanın en üstüne, diğer herhangi bir kaynak koddan önce `Option Infer On` veya `Option Infer Off` yazın. Bir dosyadaki `Option Infer` için ayarlanan değer IDE 'de veya komut satırında ayarlanan değer ile çakışıyorsa, dosyadaki değerin önceliği vardır.

@No__t_0 `On` ayarladığınızda, açıkça bir veri türü belirtmeden yerel değişkenler bildirebilirsiniz. Derleyici, başlangıç ifadesinin türünden bir değişkenin veri türünü ifade eden.

Aşağıdaki çizimde `Option Infer` açıktır. Bildirim `Dim someVar = 2` değişkeni tür çıkarımı tarafından tamsayı olarak bildirilmiştir.

Aşağıdaki ekran görüntüsünde, seçenek çıkarımı açık olduğunda IntelliSense gösterilmektedir:

![Seçenek çıkarımı açık olduğunda IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)

Aşağıdaki çizimde `Option Infer` kapalıdır. Bildirim `Dim someVar = 2` değişkeni tür çıkarımı tarafından `Object` olarak bildirilmiştir. Bu örnekte, **seçenek katı** ayarı [derleme sayfasında, Proje tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) **kapalı** olarak ayarlanır.

Aşağıdaki ekran görüntüsünde, seçenek çıkarımı kapalı olduğunda IntelliSense gösterilmektedir:

![Seçenek çıkarımı kapalıyken IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> Bir değişken `Object` olarak bildirildiğinde, program çalışırken çalışma zamanı türü değişebilir. Visual Basic, bir `Object` ve değer türü arasında dönüştürmek için *kutulama* ve *kutudan* çıkarma adlı işlemleri gerçekleştirir, bu da yürütmeyi daha yavaş yapar. Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/conversions.md#value-type-conversions)bakın.

Tür çıkarımı yordam düzeyinde uygulanır ve bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.

Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>Bir Option Infer deyimleri mevcut olmadığında

Kaynak kodu `Option Infer` bir ifade içermiyorsa, derleme sayfasındaki **seçenek çıkarımı** ayarı, [proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa, [/OptionInfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.

#### <a name="to-set-option-infer-in-the-ide"></a>IDE 'de seçenek çıkarımı ayarlamak için

1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Derle** sekmesine tıklayın.

3. **Seçenek çıkarımı** kutusunda değeri ayarlayın.

Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **seçenek** çıkar ayarı, **vb Varsayılanları** iletişim kutusundaki **seçenek çıkarımı** ayarı olarak ayarlanır. **Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** içindeki ilk varsayılan ayar `On`.

#### <a name="to-set-option-infer-on-the-command-line"></a>Komut satırında bir seçenek çıkarımı ayarlamak için

**Vbc** komutuna [/OptionInfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneğini ekleyin.

## <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri

Aşağıdaki tabloda, bir `Dim` bildiriminde veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.

|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|
|---|---|---|---|
|Hayır|Hayır|`Dim qty`|@No__t_0 kapalıysa (varsayılan), değişken `Nothing` olarak ayarlanır.<br /><br /> @No__t_0 açık ise, bir derleme zamanı hatası oluşur.|
|Hayır|Evet|`Dim qty = 5`|@No__t_0 açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> @No__t_0 kapalıysa ve `Option Strict` kapalıysa, değişken `Object` veri türünü alır.<br /><br /> @No__t_0 kapalıysa ve `Option Strict` açık ise, bir derleme zamanı hatası oluşur.|
|Evet|Hayır|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).|
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|

## <a name="example"></a>Örnek

Aşağıdaki örneklerde `Option Infer` ifadesinin yerel tür çıkarımı nasıl etkinleştirdiğini gösterilmektedir.

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir değişken `Object` olarak tanımlandığında çalışma zamanı türünün farklı kullanılabileceğini gösterir.

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Kutulama ve Kutudan Çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
