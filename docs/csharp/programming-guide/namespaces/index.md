---
title: Ad Alanları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 0e678f6577c07e4d56c485e0fd104397eddbd079
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517461"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="bbd29-102">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bbd29-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="bbd29-103">Ad alanlarında, C# programlama iki yolla yoğun olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbd29-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="bbd29-104">İlk olarak, .NET Framework ad alanları, çok sayıda sınıfa gibi düzenlemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="bbd29-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="bbd29-105">`System` bir ad alanı ve `Console` bu ad alanındaki bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="bbd29-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="bbd29-106">`using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="bbd29-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="bbd29-107">Daha fazla bilgi için [using yönergesi](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="bbd29-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="bbd29-108">İkinci olarak, kendi ad alanlarını bildirme sınıf ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd29-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="bbd29-109">Kullanım [ad alanı](../../../csharp/language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar:</span><span class="sxs-lookup"><span data-stu-id="bbd29-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="bbd29-110">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="bbd29-110">Namespaces Overview</span></span>  
 <span data-ttu-id="bbd29-111">Ad alanları, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bbd29-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="bbd29-112">Bunlar, büyük kod projeleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="bbd29-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="bbd29-113">Kullanarak sınırlandırılmıştır `.` işleci.</span><span class="sxs-lookup"><span data-stu-id="bbd29-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="bbd29-114">`using directive` Obviates gereksinimi her sınıf ad alanının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="bbd29-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="bbd29-115">`global` Ad "Kök" ad alanı: `global::System` her zaman .NET Framework ad alanına başvuruda bulunacak `System`.</span><span class="sxs-lookup"><span data-stu-id="bbd29-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bbd29-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bbd29-116">Related Sections</span></span>  
 <span data-ttu-id="bbd29-117">Ad alanları hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bbd29-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="bbd29-118">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbd29-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="bbd29-119">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbd29-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="bbd29-120">Nasıl yapılır: Ad Alanımı Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbd29-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="bbd29-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="bbd29-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbd29-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd29-122">See Also</span></span>

- [<span data-ttu-id="bbd29-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bbd29-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bbd29-124">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="bbd29-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="bbd29-125">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="bbd29-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="bbd29-126">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="bbd29-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="bbd29-127">. İşleç</span><span class="sxs-lookup"><span data-stu-id="bbd29-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
