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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49e313b2d5aa8302ea4b99e643e09f7b43659785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)
Çağırdığınızda bir `Sub` veya `Function` yordam bağımsız değişkenleri iletebilir *konuma göre* — yordam tanımında göründükleri sırada — veya bunları geçirebilirsiniz *ada göre*, olmadan konumlandırmak için şekilde.  
  
 Ada göre bir bağımsız değişken geçirdiğinizde, bağımsız değişken adını ardından bir iki nokta üst üste ve eşittir işareti tarafından bildirilen belirtin (`:=`), ardından bağımsız değişken değeri. Adlandırılmış bağımsız değişkenler herhangi bir sırada sağlayabilir.  
  
 Örneğin, aşağıdaki `Sub` yordamın kullandığı üç bağımsız değişken:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Bu yordam çağrısı, konum, ad veya her ikisinin bir karışımıyla kullanarak bağımsız değişkenleri belirtebilirsiniz.  
  
## <a name="passing-arguments-by-position"></a>Konuma göre bağımsız değişkenleri geçirme  
 Çağırabilirsiniz `Display` değişkenlerinin yöntemiyle konuma göre geçirilen ve aşağıdaki örnekte gösterildiği gibi virgülle ayrılmış:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 İsteğe bağlı bir bağımsız değişken konumsal bağımsız değişken listesinde atlarsanız, onun yerine virgül ile tutmanız gerekir. Aşağıdaki örnek çağrıları `Display` yöntemi olmadan `age` bağımsız değişkeni:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Ada göre bağımsız değişkenleri geçirme  
 Alternatif olarak, çağırabilirsiniz `Display` adıyla geçirilen bağımsız değişkenlerle aşağıdaki örnekte gösterildiği gibi virgülle ayrıca sınırlandırılmış:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Birden fazla isteğe bağlı bağımsız değişkeni olan bir yordam çağırma bu şekilde adıyla bağımsız değişkenleri geçirme özellikle yararlıdır. Ada göre bağımsız değişken sağlarsanız, konumsal bağımsız değişkenler eksik belirtmek için ardışık virgül kullanmak zorunda değil. Ada göre bağımsız değişkenleri geçirme Ayrıca, geçirme ve hangilerinin atlama hangi bağımsız değişkenleri izlemek kolaylaştırır.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Bağımsız değişkenleri konuma ve ada göre bir arada kullanma  

Aşağıdaki örnekte gösterildiği gibi değişkenleri hem konuma ve ada göre tek bir yordam çağrısında sağlayabilir:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 Önceki örnekte, hiçbir ek virgülle belirtilmemişse yerini tutmak için gerekli `age` bağımsız değişkeni, bu yana `birth` adıyla geçirilir.  
  
Bağımsız değişkenler bir karışımını konumunu ve adını, konumsal bağımsız değişkenler sağladığında sürümlerinde Visual Basic 15,5 önce tüm ilk gelmelidir. Ada göre bağımsız değişken sağlayın sonra kalan tüm bağımsız değişkenleri tüm adıyla geçirmelidir.  Örneğin, için aşağıdaki çağrı `Display` yöntemi görüntüler derleyici hatası [BC30241: adlandırılmış bağımsız değişkeni beklenen](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Visual Basic 15,5 ile başlayarak, bitiş konumsal bağımsız değişkenlerin doğru konumda ise konumsal bağımsız değişkenleri adlandırılmış bağımsız değişkenler izleyebilirsiniz. Visual Basic 15,5, önceki çağrısı altında derlenmiş ise `Display` yöntemi başarıyla derlenir ve artık derleyici hatası oluşturur [BC30241](../../../misc/bc30241.md).  

Karışık ve herhangi bir sırada adlandırılmış ve konumsal bağımsız değişkenler eşleştirmek için bu özelliği kodunuzu daha okunabilir hale getirmek için bir adlandırılmış bağımsız değişkeni kullanmak istediğinizde özellikle yararlıdır. Örneğin, aşağıdaki `Person` sınıfı oluşturucusu türünde iki bağımsız değişken gerektirir `Person`, her ikisi de olabilir `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Clear kodu amacı olmasına yardımcı olur, karma adlandırılmış ve konumsal bağımsız değişkenler kullanarak değerini `father` ve `mother` bağımsız değişkenleri olan `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Adlandırılmış bağımsız değişkenler konumsal değişkenleriyle izlemek için aşağıdaki öğeyi Visual Basic projenize eklemeniz gerekir (\*.vbproj) dosyası:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a>Bağımsız değişken adı tarafından sağladığını kısıtlamaları  

Gerekli bağımsız girmekten kaçının adıyla bağımsız değişkenlerini geçiremezsiniz. İsteğe bağlı bağımsız değişkenler atlayabilirsiniz.  
  
Ada göre parametre dizisi geçiremezsiniz. Bu yordam çağrısı, belirsiz sayıda parametre dizisi için virgülle ayrılmış bağımsız değişkenleri sağlayın ve derleyici birden fazla bağımsız değişken tek bir adla ilişkilendiremezsiniz kaynaklanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [İsteğe Bağlı Parametreler](./optional-parameters.md)  
 [Parametre Dizileri](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
