---
title: Option Compare Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 281b18322f5be4e7dadcb9533680b25016a44c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="option-compare-statement"></a>Option Compare Deyimi
Dize verilerini karşılaştırılırken kullanılacak varsayılan karşılaştırma yöntemi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`Binary`|İsteğe bağlı. Dize karşılaştırmaları iç ikili gösterimlerini karakterleri türetilmiş bir sıralama düzeni göre sonuçlanır.<br /><br /> Bu tür karşılaştırma, özellikle dizeleri metin olarak yorumlanacağını olmayan karakterleri içerebilir yararlıdır. Bu durumda, büyük/küçük harfe gibi alfabetik eşitliğini eğilim karşılaştırmalar için istemezsiniz.|  
|`Text`|İsteğe bağlı. Dize karşılaştırmaları sisteminizin bölgeye göre belirlenir büyük küçük harf duyarsız metin sıralama düzenini temel sonuçlanır.<br /><br /> Bu tür karşılaştırma dizelerinizi tüm metin karakterleri içeriyorsa ve büyük/küçük harfe ve yakından ilgili harf gibi hesap alfabetik eşitliğini alırken Karşılaştırılacak istiyorsanız yararlıdır. Örneğin, düşünmek isteyebilirsiniz `A` ve `a` eşit olması ve `Ä` ve `ä` önce gelmesini `B` ve `b`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullandıysanız, `Option Compare` ifadesi, başka bir kaynak kod deyimleri önce bir dosyada görünmelidir.  
  
 `Option Compare` Deyimi dize karşılaştırma yöntemi belirtir (`Binary` veya `Text`).  Varsayılan metin karşılaştırma yöntemi `Binary`.  
  
 A `Binary` karşılaştırma her dizedeki her karakter sayısal Unicode değerini karşılaştırır. A `Text` karşılaştırma sözcük anlamlarını geçerli kültürü göre her Unicode karakter karşılaştırır.  
  
 Microsoft Windows'daki sıralama düzeni kod sayfası tarafından belirlenir. Daha fazla bilgi için bkz: [kod sayfaları](/cpp/c-runtime-library/code-pages).  
  
 Aşağıdaki örnekte, İngilizce/Avrupa kod sayfası (ANSI 1252) karakter kullanarak sıralanır `Option Compare Binary`, tipik bir ikili sıralama üretir.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Ne zaman aynı kod sayfasını aynı karakterler sıralandığını kullanarak `Option Compare Text`, aşağıdaki metni sıralama düzeni üretilir.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Bir seçenek karşılaştırdığınızda deyimi mevcut değil  
 Kaynak kodu içermiyorsa bir `Option Compare` deyimi, **seçeneği karşılaştırmak** ayarı [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır. Komut satırı derleyicisi kullanırsanız, ayarı tarafından belirtilen [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneği kullanılır.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>IDE içinde ayarlama seçeneği karşılaştırmak için  
  
1.  İçinde **Çözüm Gezgini**, bir proje seçin. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [NIB: Proje özellikleriyle yönetme Proje Tasarımcısı](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Değer kümesinde **seçeneği karşılaştırmak** kutusu.  
  
 Bir proje oluşturduğunuzda **seçeneği karşılaştırmak** ayarı **derleme** sekmesini ayarlanmış **seçeneği karşılaştırmak** ayarı **seçenekleri** iletişim kutusu. Bu, üzerinde ayarı değiştirmek için **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda, genişletin **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **VB varsayılanları** olan **ikili**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Option Compare komut satırında ayarlamak için  
  
-   Dahil [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneği **vbc** komutu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Option Compare` ikili karşılaştırma varsayılan dize karşılaştırma yöntemi olarak ayarlamak için ifade. Bu kodu kullanmak için açıklamadan çıkarın `Option Compare Binary` deyimi ve kaynak dosyasının en üstte yerleştirin.  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Option Compare` büyük küçük harf duyarsız metin sıralama düzeni varsayılan dize karşılaştırma yöntemi olarak ayarlamak için ifade. Bu kodu kullanmak için açıklamadan çıkarın `Option Compare Text` deyimi ve kaynak dosyasının en üstte yerleştirin.  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>  
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [/ optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [Karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Like işleci](../../../visual-basic/language-reference/operators/like-operator.md)  
 [Dize işlevleri](../../../visual-basic/language-reference/functions/string-functions.md)  
 [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
