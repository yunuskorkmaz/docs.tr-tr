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
ms.openlocfilehash: e7f5fcc6d76f654f53eea6677962cb097e98b881
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912309"
---
# <a name="option-infer-statement"></a>Option Infer Deyimi
Değişkenleri bildirirken yerel tür çıkarımı kullanımını mümkün.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`On`|İsteğe bağlı. Yerel tür çıkarımı etkinleştirilir.|  
|`Off`|İsteğe bağlı. Yerel tür çıkarımını devre dışı bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dosyada `Option Infer` ayarlamak için, dosyanın en `Option Infer On` üstüne `Option Infer Off` , diğer herhangi bir kaynak kodundan önce yazın. Bir dosyada için `Option Infer` ayarlanan değer IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.  
  
 ' I ' `Option Infer` a ayarladığınızda, açıkça bir veri türü belirtmeden yerel değişkenler bildirebilirsiniz. `On` Derleyici, başlangıç ifadesinin türünden bir değişkenin veri türünü ifade eden.  
  
 Aşağıdaki çizimde `Option Infer` açıktır. Bildirimdeki `Dim someVar = 2` değişken tür çıkarımı tarafından tamsayı olarak bildirilmiştir.

 Aşağıdaki ekran görüntüsünde, seçenek çıkarımı açık olduğunda IntelliSense gösterilmektedir: 
  
 ![Seçenek çıkarımı açık olduğunda IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 Aşağıdaki çizimde `Option Infer` kapalı. Bildirimdeki `Dim someVar = 2` değişken tür çıkarımı `Object` olarak bildirilmiştir. Bu örnekte, **seçenek katı** ayarı [derleme sayfasında, Proje tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) **kapalı** olarak ayarlanır.  
  
 Aşağıdaki ekran görüntüsünde, seçenek çıkarımı kapalı olduğunda IntelliSense gösterilmektedir:
 
 ![Seçenek çıkarımı kapalıyken IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
> Bir değişken olarak `Object`bildirildiği zaman, program çalışırken çalışma zamanı türü değişebilir. Visual Basic, bir `Object` ve bir değer türü arasında dönüştürmek için *kutulama* ve *kutudan* çıkarma adlı işlemleri gerçekleştirir, bu da yürütmeyi daha yavaş yapar. Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/conversions.md#value-type-conversions)bakın.
  
 Tür çıkarımı yordam düzeyinde uygulanır ve bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.  
  
 Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Bir Option Infer deyimleri mevcut olmadığında  
 Kaynak kodu bir `Option Infer` ifade içermiyorsa, derleme sayfasındaki **seçenek çıkarımı** ayarı [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanılırsa, [/OptionInfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>IDE 'de seçenek çıkarımı ayarlamak için  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesine tıklayın.  
  
3. **Seçenek çıkarımı** kutusunda değeri ayarlayın.  
  
 Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **seçenek** çıkar ayarı, **vb Varsayılanları** iletişim kutusundaki **seçenek çıkarımı** ayarı olarak ayarlanır. **Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. Vb`On`varsayılan olarak ilk varsayılan ayar.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Komut satırında bir seçenek çıkarımı ayarlamak için  
  
- **Vbc** komutuna [/OptionInfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneğini ekleyin.  
  
## <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri  
 Aşağıdaki tabloda, bir `Dim` deyimindeki veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.  
  
|Veri türü belirtildi mi?|Başlatıcı belirtildi mi?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|Kapalıysa (varsayılan), değişkeni olarak `Nothing`ayarlanır. `Option Strict`<br /><br /> `Option Strict` Açık ise, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|`Option Infer` Açık ise (varsayılan), değişkeni başlatıcının veri türünü alır. Bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Kapalıysa ve `Option Strict` kapalıysa, değişken veri türünü `Object`alır. `Option Infer`<br /><br /> `Option Infer` Kapalıysa ve`Option Strict` açık ise, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken, veri türü için varsayılan değer olarak başlatılır. Daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, `Option Infer` ifadesinin yerel tür çıkarımı nasıl etkinleştirdiğini gösterilmektedir.  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir değişken olarak `Object`tanımlandığında çalışma zamanı türünün farklı kullanılabileceğini gösterir.  
  
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
