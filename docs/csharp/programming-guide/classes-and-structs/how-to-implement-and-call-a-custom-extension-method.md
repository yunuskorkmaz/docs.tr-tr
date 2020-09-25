---
title: Özel bir genişletme yöntemi uygulama ve çağırma-C# Programlama Kılavuzu
description: Her türlü .NET türü için uzantı yöntemleri uygulamayı öğrenin. İstemci kodu, bir DLL 'ye başvuru ekleyerek ve bir using yönergesi ekleyerek yöntemlerinizi kullanabilir.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: de4cc423e1823351305a23f331b082aa66add1a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190442"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="dc741-104">Özel bir genişletme yöntemi uygulama ve çağırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dc741-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="dc741-105">Bu konu başlığı altında, tüm .NET türleri için kendi genişletme yöntemlerinizi nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc741-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="dc741-106">İstemci kodu, uzantıları içeren DLL 'ye bir başvuru ekleyerek ve uzantı yöntemlerinin tanımlandığı ad alanını belirten bir [using](../../language-reference/keywords/using-directive.md) yönergesi ekleyerek uzantı yöntemlerinizi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="dc741-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="dc741-107">Genişletme yöntemini tanımlamak ve çağırmak için</span><span class="sxs-lookup"><span data-stu-id="dc741-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="dc741-108">Uzantı yöntemini içerecek bir statik [sınıf](./static-classes-and-static-class-members.md) tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dc741-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="dc741-109">Sınıf, istemci koduna görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc741-109">The class must be visible to client code.</span></span> <span data-ttu-id="dc741-110">Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="dc741-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="dc741-111">Genişletme yöntemini, en az içeren sınıfla aynı görünürlüğe sahip statik bir yöntem olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="dc741-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="dc741-112">Metodun ilk parametresi, yöntemin üzerinde çalıştığı türü belirtir; önünde [Bu](../../language-reference/keywords/this.md) değiştiriciye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc741-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="dc741-113">Çağıran kodda, `using` uzantı yöntemi sınıfını içeren [ad alanını](../../language-reference/keywords/namespace.md) belirtmek için bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dc741-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="dc741-114">Yöntemleri, tür üzerinde örnek yöntemmiş gibi çağırın.</span><span class="sxs-lookup"><span data-stu-id="dc741-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="dc741-115">İlk parametrenin, işlecin uygulandığı türü temsil ettiğinden ve derleyicinin zaten nesnenizin türünü bildiği için kodu çağırarak belirtildiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dc741-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="dc741-116">Yalnızca 2 ile parametreler için bağımsız değişkenler sağlamanız gerekir `n` .</span><span class="sxs-lookup"><span data-stu-id="dc741-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc741-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc741-117">Example</span></span>  

 <span data-ttu-id="dc741-118">Aşağıdaki örnek, sınıfında adlı bir genişletme yöntemi uygular `WordCount` `CustomExtensions.StringExtension` .</span><span class="sxs-lookup"><span data-stu-id="dc741-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="dc741-119">Yöntemi, <xref:System.String> ilk yöntem parametresi olarak belirtilen sınıfında çalışır.</span><span class="sxs-lookup"><span data-stu-id="dc741-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="dc741-120">`CustomExtensions`Ad alanı uygulama ad alanına aktarılır ve yöntemi yöntemi içinde çağırılır `Main` .</span><span class="sxs-lookup"><span data-stu-id="dc741-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="dc741-121">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="dc741-121">.NET Security</span></span>  

 <span data-ttu-id="dc741-122">Uzantı yöntemleri, belirli bir güvenlik güvenlik açığı sunmaz.</span><span class="sxs-lookup"><span data-stu-id="dc741-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="dc741-123">Tüm ad çakışmaları, türün kendisi tarafından tanımlanan örnek veya statik yöntem üzerinde çözümlendikleri için, bir tür üzerindeki mevcut yöntemlerin kimliğine bürünmek için hiçbir şekilde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dc741-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="dc741-124">Genişletme metotları genişletilmiş sınıftaki herhangi bir özel veriye erişemez.</span><span class="sxs-lookup"><span data-stu-id="dc741-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc741-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc741-125">See also</span></span>

- [<span data-ttu-id="dc741-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dc741-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc741-127">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="dc741-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="dc741-128">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="dc741-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="dc741-129">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="dc741-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="dc741-130">protected</span><span class="sxs-lookup"><span data-stu-id="dc741-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="dc741-131">internal</span><span class="sxs-lookup"><span data-stu-id="dc741-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="dc741-132">genel</span><span class="sxs-lookup"><span data-stu-id="dc741-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="dc741-133">Bunun</span><span class="sxs-lookup"><span data-stu-id="dc741-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="dc741-134">uzayına</span><span class="sxs-lookup"><span data-stu-id="dc741-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
