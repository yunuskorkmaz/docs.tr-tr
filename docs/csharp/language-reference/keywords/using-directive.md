---
title: "using Yönergesi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 02c50b1e7a54d776985b60570c898e7d0739c44c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="989be-102">using Yönergesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="989be-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="989be-103">`using` Yönergesi sahip üç kullanır:</span><span class="sxs-lookup"><span data-stu-id="989be-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="989be-104">Böylece bu ad alanındaki bir türü kullanımını nitelemek gerekmez türlerinin bir ad alanına izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="989be-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="989be-105">Tür adı ile erişim nitelemek zorunda kalmadan bir türün statik üyeleri erişmesine izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="989be-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="989be-106">Daha fazla bilgi için bkz: [statik yönergesi kullanarak](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="989be-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="989be-107">Bir ad alanı veya bir tür için bir diğer adı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="989be-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="989be-108">Bu adlı bir *ALIAS yönergesi kullanarak*.</span><span class="sxs-lookup"><span data-stu-id="989be-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="989be-109">`using` Anahtar oluşturmak için kullanılan aynı zamanda *using deyimleri*, hangi yardımcı olun <xref:System.IDisposable> dosyaları ve yazı tipleri gibi nesneleri doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="989be-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="989be-110">Bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="989be-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="989be-111">Statik türü kullanılarak</span><span class="sxs-lookup"><span data-stu-id="989be-111">Using Static Type</span></span>  
 <span data-ttu-id="989be-112">Tür adı ile erişim nitelemek zorunda kalmadan bir türün statik üyeleri erişebilir:</span><span class="sxs-lookup"><span data-stu-id="989be-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="989be-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="989be-113">Remarks</span></span>  
 <span data-ttu-id="989be-114">Kapsamı bir `using` yönergesi göründüğü dosyasına sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="989be-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="989be-115">Oluşturma bir `using` tanımlayıcı bir ad alanı veya türü nitelemek kolaylaştırmak için diğer ad.</span><span class="sxs-lookup"><span data-stu-id="989be-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="989be-116">Kullanarak bir sağ tarafı alias yönerge her zaman kullanımından bağımsız olarak tam bir türü olmalıdır önce gelen yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="989be-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="989be-117">Oluşturma bir `using` ad alanını belirtmek zorunda kalmadan bir ad alanındaki türleri kullanılacak yönergesi.</span><span class="sxs-lookup"><span data-stu-id="989be-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="989be-118">A `using` yönergesi verme erişim belirttiğiniz ad alanında iç içe geçmiş herhangi bir ad alanları için.</span><span class="sxs-lookup"><span data-stu-id="989be-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="989be-119">Ad alanları gelen iki kategoride: kullanıcı tanımlı ve sistem tanımlı.</span><span class="sxs-lookup"><span data-stu-id="989be-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="989be-120">Kullanıcı tarafından tanımlanan ad alanları, kodunuzda tanımlanan ad alanları olur.</span><span class="sxs-lookup"><span data-stu-id="989be-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="989be-121">Sistem tarafından tanımlanan ad alanları listesi için bkz: [.NET Framework sınıf kitaplığına genel bakış](../../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="989be-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="989be-122">Başvuran diğer derlemelerden yöntemleri ile ilgili örnekler için bkz: [oluşturma ve derlemeler kullanarak komut satırı](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="989be-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="989be-123">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="989be-123">Example 1</span></span>  
  
 <span data-ttu-id="989be-124">Aşağıdaki örnek tanımlama ve kullanma gösterilmektedir bir `using` bir ad alanı için diğer ad:</span><span class="sxs-lookup"><span data-stu-id="989be-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="989be-125">Kullanarak bir diğer ad yönergesi sağ tarafta açık genel tür sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="989be-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="989be-126">Örneğin, bir diğer ad için bir liste kullanarak oluşturamazsınız\<T >, ancak bir liste için bir tane oluşturabilirsiniz\<int >.</span><span class="sxs-lookup"><span data-stu-id="989be-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="989be-127">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="989be-127">Example 2</span></span>  
  
 <span data-ttu-id="989be-128">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir `using` yönergesi ve `using` bir sınıf için diğer ad:</span><span class="sxs-lookup"><span data-stu-id="989be-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="989be-129">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="989be-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="989be-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="989be-130">See Also</span></span>  
 [<span data-ttu-id="989be-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="989be-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="989be-132">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="989be-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="989be-133">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="989be-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="989be-134">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="989be-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="989be-135">Namespace anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="989be-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="989be-136">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="989be-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="989be-137">using deyimi</span><span class="sxs-lookup"><span data-stu-id="989be-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
