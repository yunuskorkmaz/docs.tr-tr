---
description: "Hakkında daha fazla bilgi edinin: BC42026: Expression, kapsayan özelliği yinelemeli olarak çağırır '<propertyname>"
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 4b6abcbab62ae0c4c5b18b0e6946bcfb21857112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796346"
---
# <a name="bc42026-expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="074de-103">BC42026: Ifade, kapsayan ' ' özelliğini yinelemeli olarak çağırıyor \<propertyname></span><span class="sxs-lookup"><span data-stu-id="074de-103">BC42026: Expression recursively calls the containing property '\<propertyname>'</span></span>

<span data-ttu-id="074de-104">`Set`Özellik tanımı yordamındaki bir ifade, özelliğin adına bir değer depolar.</span><span class="sxs-lookup"><span data-stu-id="074de-104">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>

 <span data-ttu-id="074de-105">Bir özelliğin değerini tutmak için önerilen yaklaşım, `Private` özelliğin kapsayıcısında bir değişken tanımlamak ve hem hem de `Get` `Set` yordamlarında kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="074de-105">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="074de-106">`Set`Yordamın bu değişkende gelen değeri depolaması gerekir `Private` .</span><span class="sxs-lookup"><span data-stu-id="074de-106">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>

 <span data-ttu-id="074de-107">`Get`Yordam, bir yordam gibi davranır `Function` , bu nedenle özellik adına bir değer atayabilir ve deyimden yararlanarak denetim getirebilirsiniz `End Get` .</span><span class="sxs-lookup"><span data-stu-id="074de-107">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="074de-108">Ancak önerilen yaklaşım, `Private` değişkeni bir [Return ifadesine](../statements/return-statement.md)değer olarak dahil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="074de-108">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>

 <span data-ttu-id="074de-109">`Set`Yordam `Sub` , bir değer döndürmeyen bir yordam gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="074de-109">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="074de-110">Bu nedenle, yordam veya özellik adının bir yordam içinde özel bir anlamı yoktur `Set` ve buna bir değer depolayamezsiniz.</span><span class="sxs-lookup"><span data-stu-id="074de-110">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>

 <span data-ttu-id="074de-111">Aşağıdaki örnekte, bu hataya neden olabilecek yaklaşım ve önerilen yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="074de-111">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>

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

 <span data-ttu-id="074de-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="074de-112">By default, this message is a warning.</span></span> <span data-ttu-id="074de-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için lütfen bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="074de-113">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="074de-114">**Hata kimliği:** BC42026</span><span class="sxs-lookup"><span data-stu-id="074de-114">**Error ID:** BC42026</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="074de-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="074de-115">To correct this error</span></span>

- <span data-ttu-id="074de-116">Önceki örnekte gösterildiği gibi önerilen yaklaşımı kullanmak için özellik tanımını yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="074de-116">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>

## <a name="see-also"></a><span data-ttu-id="074de-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="074de-117">See also</span></span>

- [<span data-ttu-id="074de-118">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="074de-118">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="074de-119">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="074de-119">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="074de-120">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="074de-120">Set Statement</span></span>](../statements/set-statement.md)
