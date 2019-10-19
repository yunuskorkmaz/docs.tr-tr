---
title: Option Compare ekstresi (Visual Basic)
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
ms.openlocfilehash: 43d3faf3a6630cd308913ce2325a5f7fe96e474c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581580"
---
# <a name="option-compare-statement"></a>Option Compare Deyimi
Dize verilerini karşılaştırırken kullanılacak varsayılan karşılaştırma yöntemini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`Binary`|İsteğe bağlı. Karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzenini temel alan dize karşılaştırmalarına neden olur.<br /><br /> Bu tür karşılaştırma, özellikle dizeler metin olarak yorumlanmaması gereken karakterler içeriyorsa yararlıdır. Bu durumda, büyük/küçük harf duyarlı gibi alfabetik denklikleri karşılaştırma yapmak istemezsiniz.|  
|`Text`|İsteğe bağlı. Sisteminizin yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız metin sıralama düzeni temelinde dize karşılaştırmaları sonucu oluşur.<br /><br /> Bu tür bir karşılaştırma, Dizeleriniz tüm metin karakterlerini içeriyorsa ve büyük/küçük harf duyarlı ve yakından ilgili mektuplar gibi hesap alfabetik denklikleri, bunları karşılaştırmak istiyorsanız yararlıdır. Örneğin, `A` ve `a` eşit olacak şekilde düşünmek ve `Ä` ve `ä` önce `B` ve `b` önce gelmesi isteyebilirsiniz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıldıysa, `Option Compare` deyimi herhangi bir diğer kaynak kodu deyiminden önce bir dosyada yer almalıdır.  
  
 @No__t_0 ifadesinde dize karşılaştırma yöntemi (`Binary` veya `Text`) belirtilir.  Varsayılan metin karşılaştırma yöntemi `Binary` ' dır.  
  
 @No__t_0 karşılaştırma, her dizedeki her bir karakterin sayısal Unicode değerini karşılaştırır. @No__t_0 karşılaştırma, her Unicode karakteri geçerli kültürün sözcük temelli anlam temelinde karşılaştırır.  
  
 Microsoft Windows 'da sıralama düzeni kod sayfası tarafından belirlenir. Daha fazla bilgi için bkz. [kod sayfaları](/cpp/c-runtime-library/code-pages).  
  
 Aşağıdaki örnekte, Ingilizce/Avrupa kod sayfasındaki (ANSI 1252) karakterler, tipik bir ikili sıralama düzeni üreten `Option Compare Binary` kullanılarak sıralanır.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Aynı kod sayfasında aynı karakterler `Option Compare Text` kullanılarak sıralandığında, aşağıdaki metin sıralama düzeni oluşturulur.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Bir Option Compare deyimleri mevcut olmadığında  
 Kaynak kodu `Option Compare` bir ifade içermiyorsa, derleme sayfasındaki **karşılaştırma ayarı seçeneği** [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisini kullanırsanız, [/OptionCompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneği tarafından belirtilen ayar kullanılır.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>IDE 'de seçenek karşılaştırması ayarlamak için  
  
1. **Çözüm Gezgini**bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesine tıklayın.  
  
3. **Seçenek karşılaştırma** kutusunda değeri ayarlayın.  
  
 Bir proje oluşturduğunuzda, **Derle** sekmesindeki **Seçenek karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek karşılaştırma** ayarına ayarlanır. Bu ayarı değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** içindeki ilk varsayılan ayar **ikili**' dır.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Komut satırında seçenek karşılaştırması ayarlamak için  
  
- **Vbc** komutuna [/OptionCompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneğini ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ikili karşılaştırmayı varsayılan dize karşılaştırma yöntemi olarak ayarlamak için `Option Compare` ifadesini kullanır. Bu kodu kullanmak için `Option Compare Binary` deyimin açıklamasını kaldırın ve kaynak dosyanın en üstüne yerleştirin.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, büyük/küçük harf duyarsız metin sıralama düzenini varsayılan dize karşılaştırma yöntemi olarak ayarlamak için `Option Compare` ifadesini kullanır. Bu kodu kullanmak için `Option Compare Text` deyimin açıklamasını kaldırın ve kaynak dosyanın en üstüne yerleştirin.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like İşleci](../../../visual-basic/language-reference/operators/like-operator.md)
- [Dize İşlevleri](../../../visual-basic/language-reference/functions/string-functions.md)
- [Option Explicit Deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
