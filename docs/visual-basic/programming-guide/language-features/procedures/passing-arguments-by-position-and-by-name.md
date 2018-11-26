---
title: Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: bdaa0351e288b85a3e35818c0f53ef4d772932e5
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296457"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)
Çağırdığınızda bir `Sub` veya `Function` yordamı, bağımsız değişkenleri iletebilir *konuma göre* — yordam tanımında göründükleri sırayla — veya geçirebileceğiniz gibi *ada göre*, olmadan konuma haklısın.  
  
 Ada göre bir bağımsız değişken başarıyla sonuçlandıktan sonra bağımsız değişken adını ardından bir iki nokta üst üste ve bir eşittir işareti tarafından bildirilen belirtin (`:=`) ve ardından bağımsız değişken değeri. Herhangi bir sırada adlandırılmış bağımsız değişkenler sağlayabilirsiniz.  
  
 Örneğin, aşağıdaki `Sub` yordamın kullandığı üç bağımsız değişken:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Bu yordamı çağırdığınızda, bağımsız değişken konumu, ad veya her ikisinin bir karışımıyla kullanarak sağlayabilirsiniz.  
  
## <a name="passing-arguments-by-position"></a>Konuma göre bağımsız değişkenleri geçirme  
 Çağırabilirsiniz `Display` bağımsız değişkenlerinden yöntemiyle konuma göre geçirilen ve aşağıdaki örnekte gösterildiği gibi virgülle ayrılmış:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 İsteğe bağlı bağımsız değişken bir konumsal bağımsız değişken listesindeki atlarsanız, onun yerine bir virgül ile tutmanız gerekir. Aşağıdaki örnek çağrıları `Display` olmadan yöntemi `age` bağımsız değişkeni:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Ada göre bağımsız değişkenleri geçirme  
 Alternatif olarak, çağırabilirsiniz `Display` adına göre geçirilen bağımsız değişkenler ile aşağıdaki örnekte gösterildiği gibi virgülle da sınırlı:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Birden fazla isteğe bağlı bağımsız değişken içeren bir yordamı çağırdığınızda, bu şekilde adıyla bağımsız değişkenleri geçirme özellikle yararlıdır. Ada göre bağımsız değişken sağlarsanız, konumsal bağımsız değişkenler eksik belirtmek için ardışık virgüller kullanmak zorunda değil. Ada göre bağımsız değişken geçirme Ayrıca hangi bağımsız değişkenleri geçirme ve hangilerinin, atlama izlemek kolaylaştırır.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Bağımsız değişkenleri konuma ve ada göre karıştırma  

Aşağıdaki örnekte gösterildiği gibi hem konuma ve ada göre tek bir yordam çağrısında bağımsız değişken belirtebilirsiniz:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 Önceki örnekte, hiçbir ek virgülle belirtilmemişse yerini tutmak için gerekli `age` bağımsız değişkeni, bu yana `birth` adına göre geçirilir.  
  
Bağımsız değişken bir karışımını konumu ve adı, konumsal bağımsız değişkenler sağladığında 15.5 önce'sürümlerinde Visual Basic'in tüm ilk sırada olması gerekir. Kalan herhangi bir bağımsız değişken adına göre bağımsız değişken sağlayın, sonra tüm adına göre geçirilmelidir.  Örneğin, için aşağıdaki çağrı `Display` yöntemi derleyici hatası görüntüler [BC30241: adlandırılmış bağımsız değişken bekleniyor](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Visual Basic 15.5 ile başlayarak, doğru konumda bitiş konumsal bağımsız değişkenler, konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenler izleyebilirsiniz. Visual Basic 15.5, önceki çağrısı altında derlenmişse `Display` yöntem başarıyla derlenir ve artık derleyici hatası oluşturur [BC30241](../../../misc/bc30241.md).  

Bu özelliği karıştırın ve eşleştirin adlandırılmış ve konumsal bağımsız değişkenler herhangi bir sırada kodunuzu daha okunabilir hale getirmek için bir adlandırılmış bağımsız değişken kullanmak istediğinizde özellikle yararlıdır. Örneğin, aşağıdaki `Person` sınıf oluşturucusu türünden iki bağımsız değişkeni gerektirir `Person`, ikisi için de olabilir `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Temizle kodun amacı olmasına yardımcı olur, karma adlandırılmış ve konumsal bağımsız değişkenler kullanarak değerini `father` ve `mother` bağımsız değişkenleri olan `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenler ile takip etmek için aşağıdaki öğe Visual Basic projenize eklemeniz gerekir (\*.vbproj) dosya:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için [Visual Basic dil sürümü ayarını](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Bağımsız değişken adı tarafından sağlama ile ilgili kısıtlamalar  

Gerekli bağımsız değişkenler girmekten kaçınmak için ada göre bağımsız değişkenler geçirilemez. İsteğe bağlı bağımsız değişkenlere atlayabilirsiniz.  
  
Ada göre bir parametre dizisi geçiremezsiniz. Bu yordamı çağırdığınızda, belirsiz sayıda parametre dizisi virgülle ayrılmış bağımsız değişkenleri sağlayın ve derleyicinin tek bir ada sahip birden fazla bağımsız değişken ilişkilendirilemiyor olmasıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [İsteğe Bağlı Parametreler](./optional-parameters.md)  
 [Parametre Dizileri](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
