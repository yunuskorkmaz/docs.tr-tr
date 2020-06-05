---
title: Option Infer Deyimi
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
ms.openlocfilehash: 977e492c1c8ec5040c22169d91268c9c2241f6c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404362"
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

Bir dosyada ayarlamak için, `Option Infer` `Option Infer On` `Option Infer Off` dosyanın en üstüne, diğer herhangi bir kaynak kodundan önce yazın. Bir dosyada için ayarlanan değer `Option Infer` IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.

`Option Infer` `On` ' I ' a ayarladığınızda, açıkça bir veri türü belirtmeden yerel değişkenler bildirebilirsiniz. Derleyici, başlangıç ifadesinin türünden bir değişkenin veri türünü ifade eden.

Aşağıdaki çizimde `Option Infer` açıktır. Bildirimdeki değişken `Dim someVar = 2` tür çıkarımı tarafından tamsayı olarak bildirilmiştir.

Aşağıdaki ekran görüntüsünde, seçenek çıkarımı açık olduğunda IntelliSense gösterilmektedir:

![Seçenek çıkarımı açık olduğunda IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)

Aşağıdaki çizimde kapalı `Option Infer` . Bildirimdeki değişken `Dim someVar = 2` `Object` tür çıkarımı olarak bildirilmiştir. Bu örnekte, **seçenek katı** ayarı [derleme sayfasında, Proje tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) **kapalı** olarak ayarlanır.

Aşağıdaki ekran görüntüsünde, seçenek çıkarımı kapalı olduğunda IntelliSense gösterilmektedir:

![Seçenek çıkarımı kapalıyken IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> Bir değişken olarak bildirildiği zaman `Object` , program çalışırken çalışma zamanı türü değişebilir. Visual Basic, bir ve bir değer türü arasında dönüştürmek için *kutulama* ve *kutudan* çıkarma adlı işlemleri gerçekleştirir `Object` , bu da yürütmeyi daha yavaş yapar. Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/conversions.md#value-type-conversions)bakın.

Tür çıkarımı yordam düzeyinde uygulanır ve bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.

Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>Bir Option Infer deyimleri mevcut olmadığında

Kaynak kodu bir `Option Infer` ifade içermiyorsa, derleme sayfasındaki **seçenek çıkarımı** ayarı [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa [-OptionInfer](../../reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.

#### <a name="to-set-option-infer-in-the-ide"></a>IDE 'de seçenek çıkarımı ayarlamak için

1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Derle** sekmesine tıklayın.

3. **Seçenek çıkarımı** kutusunda değeri ayarlayın.

Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **seçenek** çıkar ayarı, **vb Varsayılanları** iletişim kutusundaki **seçenek çıkarımı** ayarı olarak ayarlanır. **Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb** varsayılan olarak ilk varsayılan ayar `On` .

#### <a name="to-set-option-infer-on-the-command-line"></a>Komut satırında bir seçenek çıkarımı ayarlamak için

**Vbc** komutuna [-OptionInfer](../../reference/command-line-compiler/optioninfer.md) derleyici seçeneğini ekleyin.

## <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri

Aşağıdaki tabloda, bir deyimindeki veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır `Dim` .

|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|
|---|---|---|---|
|Hayır|Hayır|`Dim qty`|`Option Strict`Kapalıysa (varsayılan), değişkeni olarak ayarlanır `Nothing` .<br /><br /> `Option Strict`Açık ise, bir derleme zamanı hatası oluşur.|
|No|Evet|`Dim qty = 5`|`Option Infer`Açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> `Option Infer`Kapalıysa ve `Option Strict` kapalıysa, değişken veri türünü alır `Object` .<br /><br /> `Option Infer`Kapalıysa ve açık ise `Option Strict` , bir derleme zamanı hatası oluşur.|
|Yes|No|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Daha fazla bilgi için bkz. [Dim deyimleri](dim-statement.md).|
|Yes|Yes|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|

## <a name="example"></a>Örnek

Aşağıdaki örneklerde, `Option Infer` ifadesinin yerel tür çıkarımı nasıl etkinleştirdiğini gösterilmektedir.

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir değişken olarak tanımlandığında çalışma zamanı türünün farklı kullanılabileceğini gösterir `Object` .

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](dim-statement.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare Deyimi](option-compare-statement.md)
- [Option Explicit Deyimi](option-explicit-statement.md)
- [Option Strict Deyimi](option-strict-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../reference/command-line-compiler/optioninfer.md)
- [Kutulama ve Kutudan Çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
