---
title: Option Infer deyimi (Visual Basic)
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
ms.openlocfilehash: a85d8012eea14abe4ddcdb35fa154245894a7f97
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582936"
---
# <a name="option-infer-statement"></a>Option Infer Deyimi
Bildirme değişkenleri olarak yerel tür çıkarımı kullanımını etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`On`|İsteğe bağlı. Yerel tür çıkarımı sağlar.|  
|`Off`|İsteğe bağlı. Yerel tür çıkarımı devre dışı bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarlanacak `Option Infer` bir dosyaya yazın `Option Infer On` veya `Option Infer Off` önce başka bir kaynak kodu dosyasının üst. Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değeri önceliğe sahiptir.  
  
 Ayarladığınızda `Option Infer` için `On`, açıkça bir veri türü bildirmeden yerel değişkenleri bildirebilirsiniz. Derleyici, veri türü bir değişkenin kendi başlatma ifadesinin türünden çıkarır.  
  
 Aşağıdaki çizimde, `Option Infer` açıktır. Değişken bildiriminde `Dim someVar = 2` tür çıkarımı tarafından bir tamsayı olarak bildirilir.

 Option Infer açık olduğunda IntelliSense aşağıdaki ekran gösterilir: 
  
 ![Option Infer açık olduğunda, IntelliSense görünümü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 Aşağıdaki çizimde, `Option Infer` devre dışıdır. Değişken bildiriminde `Dim someVar = 2` olarak bildirilen bir `Object` tür çıkarımı tarafından. Bu örnekte, **Option Strict** ayarı **kapalı** üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 Option Infer devre dışıyken IntelliSense aşağıdaki ekran görüntüsünde gösterilmektedir:
 
 ![Option Infer devre dışıyken IntelliSense görünümü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  Ne zaman bir değişken bildirimi olarak bir `Object`, program çalışırken çalışma zamanı türünü değiştirebilirsiniz. Visual Basic adlı işlemler gerçekleştirdiğinde *kutulama* ve *kutudan çıkarma* arasında dönüştürmek için bir `Object` ve daha yavaş yürütme getiren bir değer türü. Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için bkz. [Visual Basic dil belirtimi](~/_vblang/spec/conversions.md#value-type-conversions).
  
 Tür çıkarımı yordam düzeyinde uygulanır ve bir yordamda bir sınıf, yapı, modül veya arabirimi dışından geçerli değildir.  
  
 Ek bilgi için bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Bir Option Infer deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Infer` deyimi **Option Infer** ayarını [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisini kullanılıyorsa [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Option Infer IDE içinde ayarlamak için  
  
1. İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
2. Tıklayın **derleme** sekmesi.  
  
3. Değer kümesindeki **Option Infer** kutusu.  
  
 Yeni bir proje oluşturduğunuzda **Option Infer** ayarını **derleme** sekmesinde ayarlanmış **Option Infer** ayarı **VB varsayılanları** iletişim kutusu. Erişim için **VB varsayılanları** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarda **VB varsayılanları** olduğu `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Option Infer komut satırında ayarlamak için  
  
- Dahil [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneğini **vbc** komutu.  
  
## <a name="default-data-types-and-values"></a>Varsayılan veri türleri ve değerleri  
 Aşağıdaki tabloda çeşitli birleşimlerini başlatıcısında ve veri türünü belirtmenin sonuçlarını açıklar bir `Dim` deyimi.  
  
|Belirtilen veri türü?|Belirtilen başlatıcı?|Örnek|Sonuç|  
|---|---|---|---|  
|Hayır|Hayır|`Dim qty`|Varsa `Option Strict` olan kapalı (varsayılan), değişkeni ayarlanır `Nothing`.<br /><br /> Varsa `Option Strict` açıktır, bir derleme zamanı hatası oluşur.|  
|Hayır|Evet|`Dim qty = 5`|Varsa `Option Infer` değişken alır veri öğesinin başlatıcısını yazın (varsayılan), olan. Bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türünü alan `Object`.<br /><br /> Varsa `Option Infer` kapalıdır ve `Option Strict` açıktır, bir derleme zamanı hatası oluşur.|  
|Evet|Hayır|`Dim qty As Integer`|Değişken veri türü için varsayılan değer için başlatılır. Daha fazla bilgi için [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Evet|Evet|`Dim qty  As Integer = 5`|Başlatıcı veri türü belirtilen veri türüne dönüştürülebilir değil, bir derleme zamanı hatası oluşur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler göstermektedir nasıl `Option Infer` ifade yerel tür çıkarımı etkinleştirir.  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir değişken olarak tanımlandığında çalışma zamanı tür farklı olduğunu gösterir. bir `Object`.  
  
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
