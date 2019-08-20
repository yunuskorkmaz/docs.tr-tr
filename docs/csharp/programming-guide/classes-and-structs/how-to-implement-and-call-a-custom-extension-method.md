---
title: 'Nasıl yapılır: Özel bir genişletme yöntemi uygulama ve çağırma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 26ad1d2251388237e186d1ba0e885fd7def66467
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596873"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="cd1af-102">Nasıl yapılır: Özel bir genişletme yöntemi uygulayın ve çağırın (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cd1af-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="cd1af-103">Bu konu başlığı altında, tüm .NET türleri için kendi genişletme yöntemlerinizi nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd1af-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="cd1af-104">İstemci kodu, uzantıları içeren DLL 'ye bir başvuru ekleyerek ve uzantı yöntemlerinin tanımlandığı ad alanını belirten bir [using](../../language-reference/keywords/using-directive.md) yönergesi ekleyerek uzantı yöntemlerinizi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd1af-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="cd1af-105">Genişletme yöntemini tanımlamak ve çağırmak için</span><span class="sxs-lookup"><span data-stu-id="cd1af-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="cd1af-106">Uzantı yöntemini içerecek bir statik [sınıf](./static-classes-and-static-class-members.md) tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd1af-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="cd1af-107">Sınıf, istemci koduna görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd1af-107">The class must be visible to client code.</span></span> <span data-ttu-id="cd1af-108">Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="cd1af-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="cd1af-109">Genişletme yöntemini, en az içeren sınıfla aynı görünürlüğe sahip statik bir yöntem olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cd1af-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="cd1af-110">Metodun ilk parametresi, yöntemin üzerinde çalıştığı türü belirtir; önünde [Bu](../../language-reference/keywords/this.md) değiştiriciye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd1af-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="cd1af-111">Çağıran kodda, uzantı yöntemi sınıfını içeren `using` [ad alanını](../../language-reference/keywords/namespace.md) belirtmek için bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd1af-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="cd1af-112">Yöntemleri, tür üzerinde örnek yöntemmiş gibi çağırın.</span><span class="sxs-lookup"><span data-stu-id="cd1af-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="cd1af-113">İlk parametrenin, işlecin uygulandığı türü temsil ettiğinden ve derleyicinin zaten nesnenizin türünü bildiği için kodu çağırarak belirtildiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cd1af-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="cd1af-114">Yalnızca 2 ile `n`parametreler için bağımsız değişkenler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd1af-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd1af-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd1af-115">Example</span></span>  
 <span data-ttu-id="cd1af-116">Aşağıdaki örnek, `WordCount` `CustomExtensions.StringExtension` sınıfında adlı bir genişletme yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="cd1af-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="cd1af-117">Yöntemi, ilk yöntem parametresi <xref:System.String> olarak belirtilen sınıfında çalışır.</span><span class="sxs-lookup"><span data-stu-id="cd1af-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="cd1af-118">Ad alanı uygulama ad alanına aktarılır ve yöntemi `Main` yöntemi içinde çağırılır. `CustomExtensions`</span><span class="sxs-lookup"><span data-stu-id="cd1af-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="cd1af-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cd1af-119">.NET Framework Security</span></span>  
 <span data-ttu-id="cd1af-120">Uzantı yöntemleri, belirli bir güvenlik güvenlik açığı sunmaz.</span><span class="sxs-lookup"><span data-stu-id="cd1af-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="cd1af-121">Tüm ad çakışmaları, türün kendisi tarafından tanımlanan örnek veya statik yöntem üzerinde çözümlendikleri için, bir tür üzerindeki mevcut yöntemlerin kimliğine bürünmek için hiçbir şekilde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cd1af-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="cd1af-122">Genişletme metotları genişletilmiş sınıftaki herhangi bir özel veriye erişemez.</span><span class="sxs-lookup"><span data-stu-id="cd1af-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1af-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd1af-123">See also</span></span>

- [<span data-ttu-id="cd1af-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cd1af-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd1af-125">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="cd1af-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="cd1af-126">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="cd1af-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="cd1af-127">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="cd1af-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="cd1af-128">protected</span><span class="sxs-lookup"><span data-stu-id="cd1af-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="cd1af-129">internal</span><span class="sxs-lookup"><span data-stu-id="cd1af-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="cd1af-130">public</span><span class="sxs-lookup"><span data-stu-id="cd1af-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="cd1af-131">this</span><span class="sxs-lookup"><span data-stu-id="cd1af-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="cd1af-132">namespace</span><span class="sxs-lookup"><span data-stu-id="cd1af-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
