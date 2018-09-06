---
title: using Yönergesi (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 1ed7ac49cde6792cddff898e8b9930a83598e02c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880996"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="3aee6-102">using Yönergesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3aee6-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="3aee6-103">`using` Yönergesi sahip üç kullanır:</span><span class="sxs-lookup"><span data-stu-id="3aee6-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="3aee6-104">Böylece bu ad alanındaki bir türü kullanımını uygun gerekmez türlerinin kullanımı bir ad alanında izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="3aee6-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="3aee6-105">Statik üyeleri ve iç içe geçmiş türler bir türün tür adıyla erişimini nitele zorunda kalmadan erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="3aee6-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="3aee6-106">Daha fazla bilgi için [using static yönergesi](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="3aee6-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="3aee6-107">Bir ad alanı veya bir tür için bir diğer ad oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3aee6-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="3aee6-108">Bu adlı bir *ALIAS yönergesi kullanarak*.</span><span class="sxs-lookup"><span data-stu-id="3aee6-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="3aee6-109">`using` Oluşturmak için de anahtar sözcüğü kullanılır *using deyimlerini*, emin olun yardımcı <xref:System.IDisposable> dosyaları ve yazı tipleri gibi nesnelerin doğru bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="3aee6-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="3aee6-110">Bkz: [using deyimi](../../../csharp/language-reference/keywords/using-statement.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="3aee6-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="3aee6-111">Statik tür kullanma</span><span class="sxs-lookup"><span data-stu-id="3aee6-111">Using Static Type</span></span>  
 <span data-ttu-id="3aee6-112">Bir türün statik üyeleri, tür adıyla erişimini nitele zorunda kalmadan erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3aee6-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="3aee6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aee6-113">Remarks</span></span>  
 <span data-ttu-id="3aee6-114">Kapsamı bir `using` yönergesi göründüğü dosyanın sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3aee6-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>
 
 <span data-ttu-id="3aee6-115">`using` Yönergesi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="3aee6-115">The `using` directive can appear:</span></span>
- <span data-ttu-id="3aee6-116">Herhangi bir ad alanı veya tür tanımı önce bir kaynak kodu dosyasının başında.</span><span class="sxs-lookup"><span data-stu-id="3aee6-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="3aee6-117">Herhangi bir ad alanı, ancak önce tüm ad alanı veya tür bu ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="3aee6-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="3aee6-118">Aksi durumda, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3aee6-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>
  
 <span data-ttu-id="3aee6-119">Oluşturma bir `using` Sınıflandır tanımlayıcı bir ad alanı veya tür için daha kolay hale getirmek için ALIAS yönergesi.</span><span class="sxs-lookup"><span data-stu-id="3aee6-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="3aee6-120">Herhangi `using` yönergesi, tam ad alanı veya tür bağımsız olarak, kullanılmalıdır `using` önce gelen yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="3aee6-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="3aee6-121">Hayır `using` diğer ad bildiriminde kullanıldığında bir `using` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="3aee6-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="3aee6-122">Örneğin, aşağıdaki bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3aee6-122">For example, the following generates a compiler error:</span></span>
 ```csharp
 using s = System.Text;
 using s.RegularExpressions; 
 ```
  
 <span data-ttu-id="3aee6-123">Oluşturma bir `using` ad alanını belirtmek zorunda kalmadan bir ad alanındaki türleri kullanılacak yönergesi.</span><span class="sxs-lookup"><span data-stu-id="3aee6-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="3aee6-124">A `using` yönergesi verme erişim için belirttiğiniz ad alanı içinde iç içe geçmiş tüm ad alanları.</span><span class="sxs-lookup"><span data-stu-id="3aee6-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="3aee6-125">Ad alanları, iki kategoride gelir: sistem tarafından tanımlanan ve kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="3aee6-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="3aee6-126">Kullanıcı tanımlı ad alanlarında, kod içinde tanımlanan ad alanları ' dir.</span><span class="sxs-lookup"><span data-stu-id="3aee6-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="3aee6-127">Sistem tarafından tanımlanan ad alanları listesi için bkz. [.NET API Browser](https://docs.microsoft.com/en-us/dotnet/api/).</span><span class="sxs-lookup"><span data-stu-id="3aee6-127">For a list of the system-defined namespaces, see [.NET API Browser](https://docs.microsoft.com/en-us/dotnet/api/).</span></span>  
  
 <span data-ttu-id="3aee6-128">Başvuran diğer derlemelerdeki yöntemleri hakkında daha fazla örnek için bkz: [oluştur ve kullanım bütünleştirilmiş kodları kullanarak komut satırı](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="3aee6-128">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="3aee6-129">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="3aee6-129">Example 1</span></span>  
  
 <span data-ttu-id="3aee6-130">Aşağıdaki örnek nasıl tanımlanacağını ve kullanılacağını gösterir. bir `using` için bir ad alanı diğer adı:</span><span class="sxs-lookup"><span data-stu-id="3aee6-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="3aee6-131">Kullanarak bir diğer ad yönergesi, sağ tarafta açık genel tür olamaz.</span><span class="sxs-lookup"><span data-stu-id="3aee6-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="3aee6-132">Örneğin, bir using diğer adı için bir liste oluşturamazsınız\<T >, ancak bir listesi için bir tane oluşturabilirsiniz\<int >.</span><span class="sxs-lookup"><span data-stu-id="3aee6-132">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="3aee6-133">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="3aee6-133">Example 2</span></span>  
  
 <span data-ttu-id="3aee6-134">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir `using` yönergesi ve `using` bir sınıf için diğer ad:</span><span class="sxs-lookup"><span data-stu-id="3aee6-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3aee6-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3aee6-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3aee6-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3aee6-136">See Also</span></span>

- [<span data-ttu-id="3aee6-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3aee6-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3aee6-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3aee6-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3aee6-139">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="3aee6-139">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
- [<span data-ttu-id="3aee6-140">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3aee6-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="3aee6-141">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3aee6-141">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="3aee6-142">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="3aee6-142">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="3aee6-143">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="3aee6-143">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
