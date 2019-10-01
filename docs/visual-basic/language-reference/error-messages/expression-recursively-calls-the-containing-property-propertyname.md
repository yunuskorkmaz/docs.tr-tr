---
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698574"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="3539f-102">İfade, içeren ' \<propertyname > ' özelliğini yinelemeli olarak çağırıyor</span><span class="sxs-lookup"><span data-stu-id="3539f-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="3539f-103">Özellik tanımının `Set` yordamındaki bir ifade, özelliğin adına bir değer depolar.</span><span class="sxs-lookup"><span data-stu-id="3539f-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="3539f-104">Bir özelliğin değerini tutmak için önerilen yaklaşım, özelliğin kapsayıcısında `Private` değişkeni tanımlamak ve hem `Get` hem de `Set` yordamlarında kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3539f-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="3539f-105">@No__t-0 yordamının bu `Private` değişkeninde gelen değeri depolaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3539f-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="3539f-106">@No__t-0 yordamı, bir `Function` yordamı gibi davranır, böylece özellik adına bir değer atayabilir ve `End Get` ifadesiyle karşılaşarak denetim getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3539f-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="3539f-107">Ancak önerilen yaklaşım, [dönüş deyimindeki](../../../visual-basic/language-reference/statements/return-statement.md)değer olarak `Private` değişkenini dahil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3539f-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="3539f-108">@No__t-0 yordamı, bir değer döndürmeyen bir `Sub` yordamı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="3539f-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="3539f-109">Bu nedenle, yordam veya özellik adının `Set` yordamında özel bir anlamı yoktur ve buna bir değer depolayamezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3539f-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="3539f-110">Aşağıdaki örnekte, bu hataya neden olabilecek yaklaşım ve önerilen yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3539f-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```vb  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 <span data-ttu-id="3539f-111">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="3539f-111">By default, this message is a warning.</span></span> <span data-ttu-id="3539f-112">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için lütfen bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3539f-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3539f-113">**Hata kimliği:** BC42026</span><span class="sxs-lookup"><span data-stu-id="3539f-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3539f-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3539f-114">To correct this error</span></span>  
  
- <span data-ttu-id="3539f-115">Önceki örnekte gösterildiği gibi önerilen yaklaşımı kullanmak için özellik tanımını yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="3539f-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3539f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3539f-116">See also</span></span>

- [<span data-ttu-id="3539f-117">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="3539f-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="3539f-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="3539f-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="3539f-119">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="3539f-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
