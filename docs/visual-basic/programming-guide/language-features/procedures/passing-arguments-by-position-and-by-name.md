---
title: "Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)
Çağırdığınızda bir `Sub` veya `Function` yordam bağımsız değişkenleri iletebilir *konuma göre* — yordam tanımında göründükleri sırada — veya bunları geçirebilirsiniz *ada göre*, olmadan konumlandırmak için şekilde.  
  
 Ada göre bir bağımsız değişken geçirdiğinizde, bağımsız değişken adını ardından bir iki nokta üst üste ve eşittir işareti tarafından bildirilen belirtin (`:=`), ardından bağımsız değişken değeri. Adlandırılmış bağımsız değişkenler herhangi bir sırada sağlayabilir.  
  
 Örneğin, aşağıdaki `Sub` yordamın kullandığı üç bağımsız değişken:  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Bu yordam çağrısı, konum, ad veya her ikisinin bir karışımıyla kullanarak bağımsız değişkenleri belirtebilirsiniz.  
  
## <a name="passing-arguments-by-position"></a>Konuma göre bağımsız değişkenleri geçirme  
 Yordam çağrısı `studentInfo` konuma göre geçirilen ve aşağıdaki örnekte gösterildiği gibi virgülle ayrılmış bağımsız değişkenlerini:  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 İsteğe bağlı bir bağımsız değişken konumsal bağımsız değişken listesinde atlarsanız, onun yerine virgül ile tutmanız gerekir. Aşağıdaki örnek çağrıları `studentInfo` olmadan `age` bağımsız değişkeni:  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>Ada göre bağımsız değişkenleri geçirme  
 Alternatif olarak, çağırabilirsiniz `studentInfo` adıyla geçirilen bağımsız değişkenlerle aşağıdaki örnekte gösterildiği gibi virgülle ayrıca sınırlandırılmış:  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Bağımsız değişkenleri konuma ve ada göre bir arada kullanma  
 Aşağıdaki örnekte gösterildiği gibi değişkenleri hem konuma ve ada göre tek bir yordam çağrısında sağlayabilir:  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 Önceki örnekte, hiçbir ek virgülle belirtilmemişse yerini tutmak için gerekli `age` bağımsız değişkeni, bu yana `birth` adıyla geçirilir.  
  
 Bağımsız değişkenler bir karışımını konumunu ve adını, konumsal bağımsız değişkenler sağladığında tüm ilk gelmelidir. Ada göre bağımsız değişken sağlayın sonra kalan bağımsız değişkenleri tüm ada göre olması gerekir.  
  
## <a name="supplying-optional-arguments-by-name"></a>Ada göre isteğe bağlı bağımsız değişkenler sağlama  
 Birden fazla isteğe bağlı bağımsız değişkeni olan bir yordam çağırma bağımsız değişkenleri ada göre geçirme özellikle yararlıdır. Ada göre bağımsız değişken sağlarsanız, konumsal bağımsız değişkenler eksik belirtmek için ardışık virgül kullanmak zorunda değil. Ada göre bağımsız değişkenleri geçirme Ayrıca, geçirme ve hangilerinin atlama hangi bağımsız değişkenleri izlemek kolaylaştırır.  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>Bağımsız değişken adı tarafından sağladığını kısıtlamaları  
 Gerekli bağımsız girmekten kaçının adıyla bağımsız değişkenlerini geçiremezsiniz. İsteğe bağlı bağımsız değişkenler atlayabilirsiniz.  
  
 Ada göre parametre dizisi geçiremezsiniz. Bu yordam çağrısı, belirsiz sayıda parametre dizisi için virgülle ayrılmış bağımsız değişkenleri sağlayın ve derleyici birden fazla bağımsız değişken tek bir adla ilişkilendiremezsiniz kaynaklanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [İsteğe bağlı parametreler](./optional-parameters.md)  
 [Parametre dizileri](./parameter-arrays.md)  
 [İsteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
