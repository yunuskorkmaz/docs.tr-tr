---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="9008c-102">Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek</span><span class="sxs-lookup"><span data-stu-id="9008c-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="9008c-103">Bir örnek değişkeni bir sınıf veya yapı kullanılan erişmek için bir `Shared` değişkeni, özelliği, yordam ya da bu sınıf veya yapı tanımlanan olay.</span><span class="sxs-lookup"><span data-stu-id="9008c-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="9008c-104">Bu uyarı bir sınıf veya bir sabit veya numaralandırma, veya iç içe geçmiş sınıf veya yapı gibi yapı örtük olarak paylaşılan bir üyesi erişmek için kullanılan bir örnek değişkeni de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="9008c-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="9008c-105">Üye paylaşımı amacı, bu üye yalnızca tek bir kopyasını oluşturun ve bu tek bir kopya sınıf veya yapı içinde bildirilmiş her örneği için kullanılabilir hale olmaktır.</span><span class="sxs-lookup"><span data-stu-id="9008c-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="9008c-106">Erişmek için bu amacı ile tutarlı bir `Shared` üye, sınıf veya yapı adını aracılığıyla yerine bu sınıf veya yapı tek bir örneğini tutan bir değişken.</span><span class="sxs-lookup"><span data-stu-id="9008c-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="9008c-107">Erişen bir `Shared` üyesi bir örnek değişkeni üzerinden yapabilir kodunuzu üye olgu anlaşılması güç anlaşılması daha zor `Shared`.</span><span class="sxs-lookup"><span data-stu-id="9008c-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="9008c-108">Bu tür erişim ifadenin bir parçası ise, ayrıca, diğer eylemler gibi gerçekleştiren bir `Function` paylaştırılmış üye örneğini döndürür yordamı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ifade ve, aksi takdirde gerçekleştirmek diğer eylemler atlar.</span><span class="sxs-lookup"><span data-stu-id="9008c-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="9008c-109">Daha fazla bilgi ve bir örnek için bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="9008c-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="9008c-110">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="9008c-110">By default, this message is a warning.</span></span> <span data-ttu-id="9008c-111">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9008c-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9008c-112">**Hata Kimliği:** BC42025</span><span class="sxs-lookup"><span data-stu-id="9008c-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9008c-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9008c-113">To correct this error</span></span>  
  
-   <span data-ttu-id="9008c-114">Sınıf veya tanımlayan yapı adını kullanmak `Shared` , aşağıdaki örnekte gösterildiği gibi erişmek için üye.</span><span class="sxs-lookup"><span data-stu-id="9008c-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="9008c-115">Kapsam etkilerini için uyarı iki programlama öğeleri ile aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9008c-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="9008c-116">Önceki örnekte kullanarak bir örnek bildirirseniz `Dim testClass as testClass = Nothing`, çağrı derleyici değerlendirir `testClass.sayHello()` sınıf adı ve hiçbir uyarı aracılığıyla yönteminin bir erişim gerçekleştiği sırada.</span><span class="sxs-lookup"><span data-stu-id="9008c-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9008c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9008c-117">See Also</span></span>  
 [<span data-ttu-id="9008c-118">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="9008c-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="9008c-119">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="9008c-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
