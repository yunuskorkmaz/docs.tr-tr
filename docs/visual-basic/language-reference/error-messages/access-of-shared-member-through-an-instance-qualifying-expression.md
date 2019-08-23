---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947706"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="2971d-102">Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek</span><span class="sxs-lookup"><span data-stu-id="2971d-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="2971d-103">Bir sınıf veya yapının örnek değişkeni, bu sınıf veya yapıda tanımlanan bir `Shared` değişkene, özelliğe, yordama veya olaya erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2971d-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="2971d-104">Bu uyarı, bir sınıf veya yapının bir sabit veya numaralandırma ya da iç içe geçmiş sınıf veya yapı gibi örtülü olarak paylaşılan üyesine erişmek için kullanılıyorsa da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2971d-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="2971d-105">Bir üyeyi paylaşma amacı söz konusu üyenin yalnızca tek bir kopyasını oluşturmak ve bu tek kopyayı, bildirildiği sınıf veya yapının her örneği için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2971d-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="2971d-106">Bu amaçla, bu sınıf veya yapının tek bir `Shared` örneğini tutan bir değişken yerine, sınıfının veya yapısının adı aracılığıyla bir üyeye erişmek için tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2971d-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="2971d-107">Bir örnek `Shared` değişken aracılığıyla bir üyeye erişmek, kodun, üyenin olduğunu `Shared`obscuring açısından anlaşılması daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2971d-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="2971d-108">Ayrıca, bu tür erişim, paylaşılan üyenin bir örneğini döndüren bir `Function` yordam gibi diğer eylemleri gerçekleştiren bir ifadenin parçasıysa, Visual Basic ifadeyi ve aksi takdirde gerçekleştireceği diğer eylemleri atlar.</span><span class="sxs-lookup"><span data-stu-id="2971d-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="2971d-109">Daha fazla bilgi ve bir örnek için bkz. [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="2971d-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="2971d-110">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="2971d-110">By default, this message is a warning.</span></span> <span data-ttu-id="2971d-111">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2971d-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2971d-112">**Hata KIMLIĞI:** BC42025</span><span class="sxs-lookup"><span data-stu-id="2971d-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2971d-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2971d-113">To correct this error</span></span>  
  
- <span data-ttu-id="2971d-114">Aşağıdaki örnekte gösterildiği gibi, ona erişmek için `Shared` üyeyi tanımlayan sınıf veya yapının adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2971d-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
> <span data-ttu-id="2971d-115">İki programlama öğesi aynı ada sahip olduğunda kapsamın etkileri için uyarı olun.</span><span class="sxs-lookup"><span data-stu-id="2971d-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="2971d-116">Önceki örnekte, kullanarak `Dim testClass as testClass = Nothing`bir örneği bildirirseniz derleyici, sınıf adı aracılığıyla yöntemine bir erişim `testClass.sayHello()` olarak bir çağrı uygular ve uyarı oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="2971d-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2971d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2971d-117">See also</span></span>

- [<span data-ttu-id="2971d-118">Shared</span><span class="sxs-lookup"><span data-stu-id="2971d-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="2971d-119">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="2971d-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
