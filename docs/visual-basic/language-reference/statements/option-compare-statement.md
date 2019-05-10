---
title: Option Compare deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 77f208a0ce94925f1f968d4949f591ccab43e582
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583511"
---
# <a name="option-compare-statement"></a>Option Compare Deyimi
Dize verileri karşılaştırılırken kullanılan varsayılan karşılaştırma yöntemini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`Binary`|İsteğe bağlı. Dize karşılaştırmaları karakterlerin dahili ikili gösterimi türetilmiş bir sıralama düzeni göre sonuçlanır.<br /><br /> Bu karşılaştırma türünü dizeler metin olarak yorumlanacağını olmayan karakterler içeren özellikle yararlı olur. Bu durumda, eğilim karşılaştırmalar büyük/küçük harf duyarsızlığı gibi alfabetik eşitliğini için istemezsiniz.|  
|`Text`|İsteğe bağlı. Dize karşılaştırmaları büyük/küçük harfe metin sıralama düzeni, sisteminizin yerel ayarı tarafından belirlenen göre sonuçlanır.<br /><br /> Bu tür bir karşılaştırma dizeleri, tüm metin karakterleri ve hesabı gibi büyük/küçük harfe ve yakından ilgili harf alfabetik denklikleri alırken Karşılaştırılacak istiyorsanız kullanışlıdır. Örneğin, düşünmek isteyebilirsiniz `A` ve `a` eşit olmasını ve `Ä` ve `ä` önce gelmesi `B` ve `b`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullandıysanız, `Option Compare` deyimi, bir dosyada başka bir kaynak kod deyimlerini önce görünmelidir.  
  
 `Option Compare` Deyimi dize karşılaştırma yöntemini belirtir (`Binary` veya `Text`).  Varsayılan metin karşılaştırma yöntemi: `Binary`.  
  
 A `Binary` karşılaştırması, her dizedeki her karakterin sayısal Unicode değerini karşılaştırır. A `Text` karşılaştırma, sözcük anlamını geçerli kültüründeki göre her bir Unicode karakter karşılaştırır.  
  
 Microsoft Windows içinde sıralama düzeni kod sayfası tarafından belirlenir. Daha fazla bilgi için [kod sayfaları](/cpp/c-runtime-library/code-pages).  
  
 Aşağıdaki örnekte, İngilizce/Avrupa kod sayfası (ANSI 1252) karakterleri kullanılarak sıralanır `Option Compare Binary`, tipik ikili sıralama düzeninde üretir.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Ne zaman aynı aynı kod sayfasında karakter sıralanır kullanarak `Option Compare Text`, aşağıdaki metni sıralama düzeninin üretilir.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Bir seçenek karşılaştırırken deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Compare` deyimi **Option Compare** ayarını [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisini kullanmak, ayarı tarafından belirtilen [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneği kullanılır.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Option Compare IDE içinde ayarlamak için  
  
1. İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
2. Tıklayın **derleme** sekmesi.  
  
3. Değer kümesindeki **Option Compare** kutusu.  
  
 Bir proje oluşturduğunuzda **Option Compare** ayarını **derleme** sekmesinde ayarlanmış **Option Compare** ayarı **seçenekleri** iletişim kutusu. Bu, üzerinde ayarı değiştirmek için **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarda **VB varsayılanları** olduğu **ikili**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Option Compare komut satırında ayarlamak için  
  
- Dahil [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneğini **vbc** komutu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Option Compare` ikili karşılaştırma varsayılan dize karşılaştırma yöntemini ayarlamak için ifade. Bu kodu kullanmak için açıklama durumundan çıkarın `Option Compare Binary` bildirimi ve kaynak dosyasının en üstüne yerleştir.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Option Compare` varsayılan dize karşılaştırma yöntemini büyük/küçük harfe metin sıralama düzeni ayarlamak için ifade. Bu kodu kullanmak için açıklama durumundan çıkarın `Option Compare Text` bildirimi ve kaynak dosyasının en üstüne yerleştir.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like İşleci](../../../visual-basic/language-reference/operators/like-operator.md)
- [Dize İşlevleri](../../../visual-basic/language-reference/functions/string-functions.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
