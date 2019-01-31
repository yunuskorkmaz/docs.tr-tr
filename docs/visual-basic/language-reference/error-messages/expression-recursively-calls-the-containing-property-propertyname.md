---
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 9382c6b6850036f3ca3795f0aa80f49b892c0a5e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259767"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="b5377-102">İfade yinelemeli olarak çağırıyor kapsayan özelliği '\<propertyname >'</span><span class="sxs-lookup"><span data-stu-id="b5377-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="b5377-103">Bir deyimde `Set` yordamı bir özellik tanımı, özelliğin adını bir değer depolar.</span><span class="sxs-lookup"><span data-stu-id="b5377-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="b5377-104">Bir özelliğin değerini tutmak için önerilen yaklaşım tanımlamaktır bir `Private` değişken özelliğin kapsayıcısındaki ve her ikisinde de kullanın `Get` ve `Set` yordamları.</span><span class="sxs-lookup"><span data-stu-id="b5377-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="b5377-105">`Set` Yordamı ardından depolamak gelen değeri bu `Private` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b5377-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="b5377-106">`Get` Yordamı davranacağını gibi bir `Function` yordam, özellik adı için bir değer atamak ve dönüş denetimi ile karşılaşıldığında `End Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b5377-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="b5377-107">Önerilen yaklaşım, ancak dahil etmektir `Private` değeri olarak değişken bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b5377-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="b5377-108">`Set` Yordamı davranacağını gibi bir `Sub` bir değer döndürmeyen bir yordam,.</span><span class="sxs-lookup"><span data-stu-id="b5377-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="b5377-109">Bu nedenle, içinde özel bir anlamı yordam veya özellik adına sahip bir `Set` yordam ve depolayamaz değeri içine.</span><span class="sxs-lookup"><span data-stu-id="b5377-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="b5377-110">Aşağıdaki örnekte, ardından tarafından önerilen yaklaşım, bu hataya neden olabilecek bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5377-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="b5377-111">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="b5377-111">By default, this message is a warning.</span></span> <span data-ttu-id="b5377-112">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için lütfen bkz [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b5377-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b5377-113">**Hata Kimliği:** BC42026</span><span class="sxs-lookup"><span data-stu-id="b5377-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5377-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b5377-114">To correct this error</span></span>  
  
-   <span data-ttu-id="b5377-115">Yukarıdaki örnekte gösterildiği gibi önerilen yaklaşım kullanılacak özellik tanımını yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="b5377-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5377-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5377-116">See also</span></span>
- [<span data-ttu-id="b5377-117">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="b5377-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="b5377-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b5377-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="b5377-119">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="b5377-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
