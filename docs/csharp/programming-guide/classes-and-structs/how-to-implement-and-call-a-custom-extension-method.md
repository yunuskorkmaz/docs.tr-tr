---
title: Özel bir genişletme yöntemi uygulama ve çağırma-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f9937c4b7c6e66af0ee3bc6f6d9ef3b3b1edd530
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241831"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="03874-102">Özel bir genişletme yöntemi uygulama ve çağırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="03874-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="03874-103">Bu konu başlığı altında, tüm .NET türleri için kendi genişletme yöntemlerinizi nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="03874-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="03874-104">İstemci kodu, uzantıları içeren DLL 'ye bir başvuru ekleyerek ve uzantı yöntemlerinin tanımlandığı ad alanını belirten bir [using](../../language-reference/keywords/using-directive.md) yönergesi ekleyerek uzantı yöntemlerinizi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="03874-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="03874-105">Genişletme yöntemini tanımlamak ve çağırmak için</span><span class="sxs-lookup"><span data-stu-id="03874-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="03874-106">Uzantı yöntemini içerecek bir statik [sınıf](./static-classes-and-static-class-members.md) tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="03874-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="03874-107">Sınıf, istemci koduna görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03874-107">The class must be visible to client code.</span></span> <span data-ttu-id="03874-108">Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="03874-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="03874-109">Genişletme yöntemini, en az içeren sınıfla aynı görünürlüğe sahip statik bir yöntem olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="03874-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="03874-110">Metodun ilk parametresi, yöntemin üzerinde çalıştığı türü belirtir; önünde [Bu](../../language-reference/keywords/this.md) değiştiriciye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03874-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="03874-111">Çağıran kodda, `using` uzantı yöntemi sınıfını içeren [ad alanını](../../language-reference/keywords/namespace.md) belirtmek için bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03874-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="03874-112">Yöntemleri, tür üzerinde örnek yöntemmiş gibi çağırın.</span><span class="sxs-lookup"><span data-stu-id="03874-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="03874-113">İlk parametrenin, işlecin uygulandığı türü temsil ettiğinden ve derleyicinin zaten nesnenizin türünü bildiği için kodu çağırarak belirtildiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="03874-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="03874-114">Yalnızca 2 ile parametreler için bağımsız değişkenler sağlamanız gerekir `n` .</span><span class="sxs-lookup"><span data-stu-id="03874-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03874-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="03874-115">Example</span></span>  
 <span data-ttu-id="03874-116">Aşağıdaki örnek, sınıfında adlı bir genişletme yöntemi uygular `WordCount` `CustomExtensions.StringExtension` .</span><span class="sxs-lookup"><span data-stu-id="03874-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="03874-117">Yöntemi, <xref:System.String> ilk yöntem parametresi olarak belirtilen sınıfında çalışır.</span><span class="sxs-lookup"><span data-stu-id="03874-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="03874-118">`CustomExtensions`Ad alanı uygulama ad alanına aktarılır ve yöntemi yöntemi içinde çağırılır `Main` .</span><span class="sxs-lookup"><span data-stu-id="03874-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="03874-119">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="03874-119">.NET Security</span></span>  
 <span data-ttu-id="03874-120">Uzantı yöntemleri, belirli bir güvenlik güvenlik açığı sunmaz.</span><span class="sxs-lookup"><span data-stu-id="03874-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="03874-121">Tüm ad çakışmaları, türün kendisi tarafından tanımlanan örnek veya statik yöntem üzerinde çözümlendikleri için, bir tür üzerindeki mevcut yöntemlerin kimliğine bürünmek için hiçbir şekilde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="03874-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="03874-122">Genişletme metotları genişletilmiş sınıftaki herhangi bir özel veriye erişemez.</span><span class="sxs-lookup"><span data-stu-id="03874-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03874-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03874-123">See also</span></span>

- [<span data-ttu-id="03874-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="03874-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="03874-125">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="03874-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="03874-126">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="03874-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="03874-127">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="03874-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="03874-128">protected</span><span class="sxs-lookup"><span data-stu-id="03874-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="03874-129">internal</span><span class="sxs-lookup"><span data-stu-id="03874-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="03874-130">public</span><span class="sxs-lookup"><span data-stu-id="03874-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="03874-131">this</span><span class="sxs-lookup"><span data-stu-id="03874-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="03874-132">uzayına</span><span class="sxs-lookup"><span data-stu-id="03874-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
