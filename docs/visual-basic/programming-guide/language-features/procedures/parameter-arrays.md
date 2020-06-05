---
title: Parametre Dizileri
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
ms.openlocfilehash: dac0575d73ffd4159e89bff344915a33b9d0e5d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364285"
---
# <a name="parameter-arrays-visual-basic"></a>Parametre Dizileri (Visual Basic)
Genellikle, yordam bildiriminin belirttiğinden daha fazla bağımsız değişkenle bir yordam çağrılamaz. Sınırsız sayıda bağımsız değişkene ihtiyacınız olduğunda bir *parametre dizisi*bildirebilirsiniz ve bu, bir yordamın bir parametre için bir dizi değer kabul etmesine izin verir. Yordamı tanımlarken parametre dizisindeki öğelerin sayısını bilmeniz gerekmez. Dizi boyutu, yordamın her çağrısıyla ayrı ayrı belirlenir.  
  
## <a name="declaring-a-paramarray"></a>ParamArray bildirme  
 Parametre listesinde bir parametre dizisini göstermek için [ParamArray](../../../language-reference/modifiers/paramarray.md) anahtar sözcüğünü kullanırsınız. Aşağıdaki kurallar geçerlidir:  
  
- Bir yordam yalnızca bir parametre dizisi tanımlayabilir ve yordam tanımındaki son parametre olmalıdır.  
  
- Parametre dizisinin değere göre geçirilmesi gerekir. Yordam tanımına [ByVal](../../../language-reference/modifiers/byval.md) anahtar sözcüğünü açıkça eklemek iyi bir programlama uygulamasıdır.  
  
- Parametre dizisi otomatik olarak isteğe bağlıdır. Varsayılan değeri, parametre dizisinin öğe türünün boş bir boyutlu dizisidir.  
  
- Parametre dizisinin önceki tüm parametreleri gerekli olmalıdır. Parametre dizisi, tek bir isteğe bağlı parametre olmalıdır.  
  
## <a name="calling-a-paramarray"></a>ParamArray çağırma  
 Bir parametre dizisini tanımlayan bir yordamı çağırdığınızda, bağımsız değişkenini aşağıdaki yöntemlerle sağlayabilirsiniz:  
  
- Nothing — Yani, [ParamArray](../../../language-reference/modifiers/paramarray.md) bağımsız değişkenini atlayabilirsiniz. Bu durumda, yordama boş bir dizi geçirilir. [Nothing](../../../language-reference/nothing.md) anahtar sözcüğünü açıkça geçirirseniz, yordama bir null dizi geçirilir ve çağrılan yordam bu koşulu Denetmezse bir NullReferenceException öğesine neden olabilir.
  
- Virgülle ayırarak rastgele sayıda bağımsız değişken listesi. Her bağımsız değişkenin veri türü, örtülü olarak öğe türüne dönüştürülebilir olmalıdır `ParamArray` .  
  
- Parametre dizisinin öğe türüyle aynı öğe türüne sahip bir dizi.  
  
 Her durumda, yordam içindeki kod parametre dizisini, veri türüyle aynı veri türü öğeleriyle tek boyutlu bir dizi olarak değerlendirir `ParamArray` .  
  
> [!IMPORTANT]
> Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır. Bir parametre dizisini kabul ediyorsanız, çağıran kodun kendisine geçirildiği dizinin boyutunu test etmelisiniz. Uygulamanız için çok büyükse uygun adımları uygulayın. Daha fazla bilgi için bkz. [diziler](../arrays/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, işlevini tanımlar ve çağırır `calcSum` . `ParamArray`Parametresi için değiştirici, `args` işlevin değişken sayıda bağımsız değişken kabul etmesine olanak sağlar.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 Aşağıdaki örnek, bir parametre dizisi ile bir yordam tanımlar ve parametre dizisine geçirilen tüm dizi öğelerinin değerlerini çıkarır.  
  
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
- [Diziler](../arrays/index.md)
- [İsteğe Bağlı](../../../language-reference/modifiers/optional.md)
