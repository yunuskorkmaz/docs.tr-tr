---
title: İfade yinelemeli olarak çağırıyor içeren özellik &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588849"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="52214-102">İfade yinelemeli olarak çağırıyor içeren özellik &#39; &lt;propertyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="52214-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="52214-103">Bir deyimde `Set` yordamı özelliği tanımı bir değer özelliğinin adı depolar.</span><span class="sxs-lookup"><span data-stu-id="52214-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="52214-104">Bir özelliğin değerini tutan önerilen yaklaşım tanımlamaktır bir `Private` özelliğin kapsayıcısında değişken ve ikisi de kullanmak `Get` ve `Set` yordamları.</span><span class="sxs-lookup"><span data-stu-id="52214-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="52214-105">`Set` Yordamı sonra depolamak gelen değeri bu `Private` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="52214-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="52214-106">`Get` Yordamı davranır gibi bir `Function` yordamı, özellik adı için bir değer atamak ve dönüş denetim karşılaşmadan tarafından `End Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="52214-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="52214-107">Önerilen yaklaşım ancak eklemektir `Private` değişken değer olarak bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="52214-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="52214-108">`Set` Yordamı davranır gibi bir `Sub` bir değer döndürmüyor yordamı.</span><span class="sxs-lookup"><span data-stu-id="52214-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="52214-109">Bu nedenle, içinde özel bir anlamı yordamı veya özellik adına sahip bir `Set` yordam ve depolayamaz bir değer içine.</span><span class="sxs-lookup"><span data-stu-id="52214-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="52214-110">Aşağıdaki örnek tarafından önerilen yaklaşım ve ardından bu hataya neden olabilir bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="52214-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```  
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
  
 <span data-ttu-id="52214-111">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="52214-111">By default, this message is a warning.</span></span> <span data-ttu-id="52214-112">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için lütfen bkz [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="52214-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="52214-113">**Hata Kimliği:** BC42026</span><span class="sxs-lookup"><span data-stu-id="52214-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52214-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="52214-114">To correct this error</span></span>  
  
-   <span data-ttu-id="52214-115">Önceki örnekte gösterildiği gibi önerilen yaklaşımı kullanmak için özellik tanımını yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="52214-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52214-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52214-116">See Also</span></span>  
 [<span data-ttu-id="52214-117">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="52214-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="52214-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="52214-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="52214-119">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="52214-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
