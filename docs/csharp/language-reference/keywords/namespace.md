---
title: "namespace (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a><span data-ttu-id="e204a-102">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e204a-102">namespace (C# Reference)</span></span>
<span data-ttu-id="e204a-103">`namespace` Anahtar sözcük, ilgili nesne kümesi içeren kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e204a-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="e204a-104">Kod öğelerini düzenlemek ve genel benzersiz türleri oluşturmak için bir ad alanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e204a-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="e204a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e204a-105">Remarks</span></span>  
 <span data-ttu-id="e204a-106">Ad alanı içinde bir veya daha fazla türlerinden birini bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="e204a-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="e204a-107">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="e204a-107">another namespace</span></span>  
  
-   [<span data-ttu-id="e204a-108">sınıfı</span><span class="sxs-lookup"><span data-stu-id="e204a-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="e204a-109">arabirimi</span><span class="sxs-lookup"><span data-stu-id="e204a-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="e204a-110">yapısı</span><span class="sxs-lookup"><span data-stu-id="e204a-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="e204a-111">Enum</span><span class="sxs-lookup"><span data-stu-id="e204a-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="e204a-112">temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="e204a-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="e204a-113">C# kaynak dosyasında bir ad alanını açıkça bildirme olup olmadığına, bir varsayılan ad alanı derleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="e204a-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="e204a-114">Bazen genel ad alanı da adlandırılır bu adlandırılmamış ad alanı, her dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="e204a-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="e204a-115">Genel ad alanındaki herhangi bir tanımlayıcı, adlandırılmış bir ad alanını kullanmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e204a-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="e204a-116">Ad alanları örtük olarak genel erişimi vardır ve bu değiştirilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="e204a-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="e204a-117">Erişim değiştiricileri öğelere bir ad atamak için bkz [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="e204a-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="e204a-118">Ad alanı iki veya daha fazla bildirimlerinde tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e204a-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="e204a-119">Örneğin, aşağıdaki örnekte bir parçası olarak iki sınıf tanımlar `MyCompany` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="e204a-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="e204a-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e204a-120">Example</span></span>  
 <span data-ttu-id="e204a-121">Aşağıdaki örnek, iç içe geçmiş bir ad alanında bir statik yöntem çağrısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e204a-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="e204a-122">Daha Fazla Bilgi İçin</span><span class="sxs-lookup"><span data-stu-id="e204a-122">For More Information</span></span>  
 <span data-ttu-id="e204a-123">Ad alanlarını kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="e204a-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e204a-124">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="e204a-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="e204a-125">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e204a-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="e204a-126">Nasıl yapılır: Genel Namespace diğer adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e204a-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="e204a-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e204a-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e204a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e204a-128">See Also</span></span>  
 [<span data-ttu-id="e204a-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e204a-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e204a-130">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e204a-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e204a-131">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e204a-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e204a-132">Namespace anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e204a-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="e204a-133">kullanma</span><span class="sxs-lookup"><span data-stu-id="e204a-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
