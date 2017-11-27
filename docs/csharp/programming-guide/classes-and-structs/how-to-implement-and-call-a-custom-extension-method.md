---
title: "Nasıl yapılır: Özel bir Uzantı Metodu Uygulama ve Arama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7de999c53f02fcc2bde4a8ccf504ba2b1d032638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="0e735-102">Nasıl yapılır: Özel bir Uzantı Metodu Uygulama ve Arama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0e735-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="0e735-103">Bu konu, kendi içinde herhangi bir türü için genişletme yöntemleri uygulamak gösterilmiştir [.NET Framework sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkID=217856), veya genişletmek istediğiniz herhangi bir .NET türü.</span><span class="sxs-lookup"><span data-stu-id="0e735-103">This topic shows how to implement your own extension methods for any type in the [.NET Framework Class Library](http://go.microsoft.com/fwlink/?LinkID=217856), or any other .NET type that you want to extend.</span></span> <span data-ttu-id="0e735-104">İstemci kodu, genişletme yöntemleri kullanabilir, bunları içeren DLL bir başvuru ekleyerek ve ekleyerek bir [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergesi genişletme yöntemleri tanımlanır ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e735-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="0e735-105">Tanımlama ve uzantı yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="0e735-105">To define and call the extension method</span></span>  
  
1.  <span data-ttu-id="0e735-106">Statik tanımlamak [sınıfı](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) genişletme yöntemi içerecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="0e735-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="0e735-107">Sınıfı için istemci kodu görünür olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e735-107">The class must be visible to client code.</span></span> <span data-ttu-id="0e735-108">Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0e735-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2.  <span data-ttu-id="0e735-109">En az genişletme yöntemi ile statik bir yöntem olarak uygulamak aynı görünürlük içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="0e735-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3.  <span data-ttu-id="0e735-110">Yönteminin ilk parametresi, yöntemin işlediği türünü belirtir; ile gelmelidir [bu](../../../csharp/language-reference/keywords/this.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0e735-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4.  <span data-ttu-id="0e735-111">Çağıran kodu ekleyin bir `using` belirtmek için yönergesi [ad alanı](../../../csharp/language-reference/keywords/namespace.md) uzantısı yöntemi sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="0e735-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5.  <span data-ttu-id="0e735-112">Türün örnek yöntemleri değilmiş gibi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0e735-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="0e735-113">İlk parametre işleci uygulanmakta türünü temsil eder çünkü kodu çağırarak belirtilmemiş ve derleyici, nesne türü zaten bilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e735-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="0e735-114">Yalnızca 2 parametreleriyle bağımsız değişkenleri sağlamak zorunda `n`.</span><span class="sxs-lookup"><span data-stu-id="0e735-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e735-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e735-115">Example</span></span>  
 <span data-ttu-id="0e735-116">Aşağıdaki örnek adlı bir genişletme yöntemi uygulayan `WordCount` içinde `CustomExtensions.StringExtension` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e735-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="0e735-117">Yöntemin işlediği <xref:System.String> ilk yöntemi parametre olarak belirtilen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e735-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="0e735-118">`CustomExtensions` Uygulama ad alanına ad alanı içe aktarılan ve içinde çağrılan yöntemi `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e735-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e735-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e735-119">Compiling the Code</span></span>  
 <span data-ttu-id="0e735-120">Bu kodu çalıştırmak için kopyalamak ve içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e735-120">To run this code, copy and paste it into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="0e735-121">Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll bir başvuru içeriyor ve bir `using` System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="0e735-121">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="0e735-122">Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e735-122">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0e735-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0e735-123">.NET Framework Security</span></span>  
 <span data-ttu-id="0e735-124">Genişletme yöntemleri hiçbir belirli güvenlik açıkları sunar.</span><span class="sxs-lookup"><span data-stu-id="0e735-124">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="0e735-125">Tüm ad çakışmaları örneği veya türü tarafından tanımlanan statik yöntemi lehinde çözümlenir çünkü bir türün varolan yöntemleri kimliğine bürünmek için hiçbir zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e735-125">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="0e735-126">Genişletme yöntemleri genişletilmiş sınıfındaki tüm özel verilere erişemez.</span><span class="sxs-lookup"><span data-stu-id="0e735-126">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e735-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e735-127">See Also</span></span>  
 [<span data-ttu-id="0e735-128">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0e735-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0e735-129">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0e735-129">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="0e735-130">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="0e735-130">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="0e735-131">Statik sınıflar ve statik sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="0e735-131">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="0e735-132">korumalı</span><span class="sxs-lookup"><span data-stu-id="0e735-132">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="0e735-133">İç</span><span class="sxs-lookup"><span data-stu-id="0e735-133">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 [<span data-ttu-id="0e735-134">Ortak</span><span class="sxs-lookup"><span data-stu-id="0e735-134">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="0e735-135">Bu</span><span class="sxs-lookup"><span data-stu-id="0e735-135">this</span></span>](../../../csharp/language-reference/keywords/this.md)  
 [<span data-ttu-id="0e735-136">ad alanı</span><span class="sxs-lookup"><span data-stu-id="0e735-136">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
