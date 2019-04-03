---
title: Parametre Dizileri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 8ea4c77056701b8f61c1ed5a53cf20d98ae913bc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834172"
---
# <a name="parameter-arrays-visual-basic"></a>Parametre Dizileri (Visual Basic)
Genellikle, yordam bildirimi belirtilenden daha fazla bağımsız değişken içeren bir yordamı çağıramaz. Sonsuz sayıda bağımsız değişken gerektiğinde bildirebilirsiniz bir *parametre dizisi*, bir dizi parametre değerlerini kabul etmek bir yordam sağlar. Yordamı tanımlarken parametresi dizideki öğelerin sayısını öğrenmek zorunda değildir. Dizi boyutu, tek tek her yordam çağrısına göre belirlenir.  
  
## <a name="declaring-a-paramarray"></a>Bir ParamArray bildirme  
 Kullandığınız [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre listesinde bir parametre dizisi belirtmek için anahtar sözcüğü. Aşağıdaki kurallar geçerlidir:  
  
-   Bir yordam yalnızca bir parametre dizisi tanımlayabilirsiniz ve yordam tanımında son parametre olmalıdır.  
  
-   Parametre dizisi değerine göre geçirilmelidir. İyi bir programlama açıkça içerecek şekilde [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordam tanımında anahtar sözcüğü.  
  
-   Parametre dizisi otomatik olarak isteğe bağlıdır. Boş bir tek boyutlu dizi parametresi dizinin öğe türü, varsayılan değerdir.  
  
-   Parametre dizisi önceki tüm parametreler gereklidir. Parametre dizisi, yalnızca isteğe bağlı parametresi olmalıdır.  
  
## <a name="calling-a-paramarray"></a>Bir ParamArray çağırma  
 Bir parametre dizisi tanımlayan bir yordamı çağırdığınızda, bağımsız değişkeni aşağıdaki yollardan birinde belirtebilirsiniz:  
  
-   Hiçbir şey — diğer bir deyişle, atlayabilirsiniz [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) bağımsız değişken. Bu durumda, boş bir dizi yordamına geçirildi. De geçirebilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) aynı etkiye sahip anahtar sözcüğü.  
  
-   Rastgele bir sayıdan bağımsız değişkenleri, virgülle ayrılmış listesi. Her bağımsız değişken veri türünü örtük olarak dönüştürülebilir olmalıdır `ParamArray` öğe türü.  
  
-   Parametre dizinin öğe türü olarak aynı öğe türüne sahip bir dizi.  
  
 Her durumda, yordamı içindeki kod öğelerini aynı veri türünde tek boyutlu bir dizi olarak parametre dizisi işler `ParamArray` veri türü.  
  
> [!IMPORTANT]
>  Süresiz olarak büyük olabilecek bir dizi işlem olduğunda, uygulamanızın bazı iç kapasite taşmasını riski yoktur. Bir parametre dizisi kabul ederseniz, çağıran kodun geçirilen dizinin boyutu için test etmeniz gerekir. Uygulamanız için çok büyük ise, uygun adımları atıyoruz. Daha fazla bilgi için [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tanımlar ve işlev çağrıları `calcSum`. `ParamArray` Parametresi değiştiricisi `args` değişken sayıda bağımsız değişken kabul etmek bu işlevi etkinleştirir.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 Aşağıdaki örnek, bir parametre dizisi içeren bir yordamı tanımlar ve geçirilen parametre dizisi için tüm dizi öğelerinin değerleri çıkarır.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
