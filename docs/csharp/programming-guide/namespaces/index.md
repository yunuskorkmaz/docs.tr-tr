---
title: Ad Alanları (C# Programlama Kılavuzu)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: c4011092a6c605137053b544d4b9f14cce2fdb4c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44366159"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="c8e0f-102">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c8e0f-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="c8e0f-103">Ad alanlarında, C# programlama iki yolla yoğun olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="c8e0f-104">İlk olarak, .NET Framework ad alanları, çok sayıda sınıfa gibi düzenlemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="c8e0f-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
<span data-ttu-id="c8e0f-105">`System` bir ad alanı ve `Console` bu ad alanındaki bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="c8e0f-106">`using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="c8e0f-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
<span data-ttu-id="c8e0f-107">Daha fazla bilgi için [using yönergesi](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="c8e0f-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="c8e0f-108">İkinci olarak, kendi ad alanlarını bildirme sınıf ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="c8e0f-109">Kullanım [ad alanı](../../language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar:</span><span class="sxs-lookup"><span data-stu-id="c8e0f-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

<span data-ttu-id="c8e0f-110">Ad geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="c8e0f-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="c8e0f-111">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="c8e0f-111">Namespaces Overview</span></span>  

<span data-ttu-id="c8e0f-112">Ad alanları, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c8e0f-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="c8e0f-113">Bunlar, büyük kod projeleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-113">They organize large code projects.</span></span>  
- <span data-ttu-id="c8e0f-114">Kullanarak sınırlandırılmıştır `.` işleci.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="c8e0f-115">`using directive` Obviates gereksinimi her sınıf ad alanının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-115">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="c8e0f-116">`global` Ad "Kök" ad alanı: `global::System` her zaman .NET Framework ad alanına başvuruda bulunacak `System`.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="c8e0f-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c8e0f-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8e0f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e0f-118">See Also</span></span>

- [<span data-ttu-id="c8e0f-119">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8e0f-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="c8e0f-120">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8e0f-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="c8e0f-121">Nasıl yapılır: Ad Alanımı Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8e0f-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="c8e0f-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c8e0f-122">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="c8e0f-123">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="c8e0f-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="c8e0f-124">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c8e0f-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="c8e0f-125">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="c8e0f-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="c8e0f-126">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="c8e0f-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="c8e0f-127">. İşleç</span><span class="sxs-lookup"><span data-stu-id="c8e0f-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
>>>>>>> <span data-ttu-id="c8e0f-128">tanımlayıcı adlandırma kuralları ekleme</span><span class="sxs-lookup"><span data-stu-id="c8e0f-128">add identifier naming rules</span></span>
