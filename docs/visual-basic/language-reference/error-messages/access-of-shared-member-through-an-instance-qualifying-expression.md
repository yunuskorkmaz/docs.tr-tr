---
title: Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751611"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="b410e-102">Paylaşılan üyeye bir örnek üzerinden erişim; niteleyen ifade değerlendirilmeyecek</span><span class="sxs-lookup"><span data-stu-id="b410e-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="b410e-103">Bir sınıfın veya yapının bir örnek değişkeni kullanılan erişmek için bir `Shared` değişken, özellik, yordam veya o sınıfta veya yapıda da tanımlı olay.</span><span class="sxs-lookup"><span data-stu-id="b410e-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="b410e-104">Bu uyarı bir sınıf veya yapı, sabit veya sabit listesi, bir iç içe geçmiş sınıf veya yapı gibi örtük olarak paylaşılan bir üyesine erişmek için kullanılan bir örnek değişkeni de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b410e-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="b410e-105">Üye paylaşımı amacı, bu üyede tek bir kopyasını oluşturun ve bu tek kopyası, sınıf veya yapı içinde bildirildiği'nin her örneğinin kullanımına sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b410e-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="b410e-106">Bu amaca uygun erişmek için tutarlı bir `Shared` üyesi, bir sınıfın veya yapının adını, yerine bu sınıfı ya da yapı tek bir örneğini tutan değişken üzerinden.</span><span class="sxs-lookup"><span data-stu-id="b410e-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="b410e-107">Erişim bir `Shared` üyeye bir örnek değişkeni üzerinden yapabilir, kodunuzun daha zor bir üyesi olan bir olgu, anlaşılması güç tarafından anlamak `Shared`.</span><span class="sxs-lookup"><span data-stu-id="b410e-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="b410e-108">Bu tür erişim ifadesinin bir parçası ise Ayrıca, diğer eylemler gibi gerçekleştiren bir `Function` paylaşılan üyenin bir örneğinin döndüren yordam, Visual Basic atlar ifade ve aksi takdirde gerçekleştirmek diğer tüm eylemler.</span><span class="sxs-lookup"><span data-stu-id="b410e-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="b410e-109">Daha fazla bilgi ve örnek için bkz. [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b410e-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="b410e-110">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="b410e-110">By default, this message is a warning.</span></span> <span data-ttu-id="b410e-111">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b410e-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b410e-112">**Hata Kimliği:** BC42025</span><span class="sxs-lookup"><span data-stu-id="b410e-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b410e-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b410e-113">To correct this error</span></span>  
  
- <span data-ttu-id="b410e-114">Sınıf veya tanımlayan yapısını adını kullanın `Shared` , aşağıdaki örnekte gösterildiği gibi erişmek için üye.</span><span class="sxs-lookup"><span data-stu-id="b410e-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="b410e-115">Kapsam etkileri için uyarı iki programlama öğeleri aynı ada sahip olun.</span><span class="sxs-lookup"><span data-stu-id="b410e-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="b410e-116">Önceki örnekte kullanarak örneği bildirirseniz `Dim testClass as testClass = Nothing`, derleyici bir çağrı işler `testClass.sayHello()` yöntemin sınıf adı ve hiçbir uyarı aracılığıyla erişim gerçekleştiği sırada.</span><span class="sxs-lookup"><span data-stu-id="b410e-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b410e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b410e-117">See also</span></span>

- [<span data-ttu-id="b410e-118">Shared</span><span class="sxs-lookup"><span data-stu-id="b410e-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="b410e-119">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="b410e-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
