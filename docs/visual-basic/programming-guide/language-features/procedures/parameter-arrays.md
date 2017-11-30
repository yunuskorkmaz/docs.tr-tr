---
title: Parametre Dizileri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a>Parametre Dizileri (Visual Basic)
Genellikle, bir yordam yordamı bildirimi belirtilenden daha fazla bağımsız değişkenlerle çağrılamaz. Sonsuz sayıda bağımsız değişken gerektiğinde bildirebilir bir *parametre dizisi*, bir parametre için değer bir dizi kabul etmek bir yordam sağlar. Yordam tanımlarsanız parametre dizisindeki öğelerin sayısı bilmeniz gerekmez. Dizi boyutu, tek tek her yordam çağrısına tarafından belirlenir.  
  
## <a name="declaring-a-paramarray"></a>Bir ParamArray bildirme  
 Kullandığınız [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre listesinde bir parametre dizisi belirtmek için anahtar sözcüğü. Aşağıdaki kurallar geçerlidir:  
  
-   Bu yordamı tanımı'nda son parametre olmalıdır ve bir yordam yalnızca bir parametre dizisi tanımlayabilirsiniz.  
  
-   Parametre dizisi değere göre geçirilecek gerekir. Açık içerecek şekilde uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamı tanımı bir anahtar sözcük.  
  
-   Parametre dizisine otomatik olarak isteğe bağlıdır. Parametre dizinin öğe türü boş bir tek boyutlu dizi kendi varsayılan değerdir.  
  
-   Parametre dizisi önceki tüm parametreler gerekli olması gerekir. Parametre dizisi yalnızca isteğe bağlı bir parametre olması gerekir.  
  
## <a name="calling-a-paramarray"></a>Bir ParamArray çağırma  
 Bir parametre dizisi tanımlayan bir yordam çağrısı, bağımsız değişkeni aşağıdaki yollardan birinde sağlayabilir:  
  
-   Hiçbir şey — diğer bir deyişle, atlayabilirsiniz [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) bağımsız değişkeni. Bu durumda, boş bir dizi yordama geçirilir. Ayrıca iletebilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) aynı etkiye sahip anahtar sözcük.  
  
-   Bir rastgele sayıda bağımsız değişken, virgülle ayrılmış listesi. Her bağımsız değişkeninin veri türü örtük olarak dönüştürülebilir olmalıdır `ParamArray` öğe türü.  
  
-   Parametre dizinin öğe türü olarak aynı öğe türüne sahip bir dizi.  
  
 Her durumda, yordam içindeki kod aynı veri türünde öğelerin tek boyutlu bir dizi olarak parametre dizisi değerlendirir `ParamArray` veri türü.  
  
> [!IMPORTANT]
>  Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur. Bir parametre dizisi kabul ederseniz, çağrıyı yapan kod kendisine geçirilen dizi boyutu için test etmeniz gerekir. Uygulamanız için çok büyük ise uygun adımları gerçekleştirin. Daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlar ve işlev çağrılarını `calcSum`. `ParamArray` Parametresi değiştiricisi `args` değişken sayıda bağımsız değişken kabul etmek işlevi sağlar.  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 Aşağıdaki örnekte bir parametre dizisi yordamla tanımlar ve parametre dizisine geçirilen tüm dizi öğelerinin değerlerini çıkarır.  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Bağımsız değişkenleri konuma göre ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md)  
 [İsteğe bağlı parametreler](./optional-parameters.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [İsteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md)
