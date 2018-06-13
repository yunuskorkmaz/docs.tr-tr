---
title: namespace (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276025"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="1448f-102">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1448f-102">namespace (C# Reference)</span></span>
<span data-ttu-id="1448f-103">`namespace` Anahtar sözcük, ilgili nesne kümesi içeren kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1448f-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="1448f-104">Kod öğelerini düzenlemek ve genel benzersiz türleri oluşturmak için bir ad alanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1448f-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="1448f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1448f-105">Remarks</span></span>  
 <span data-ttu-id="1448f-106">Ad alanı içinde bir veya daha fazla türlerinden birini bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="1448f-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="1448f-107">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="1448f-107">another namespace</span></span>  
  
-   [<span data-ttu-id="1448f-108">class</span><span class="sxs-lookup"><span data-stu-id="1448f-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="1448f-109">interface</span><span class="sxs-lookup"><span data-stu-id="1448f-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="1448f-110">struct</span><span class="sxs-lookup"><span data-stu-id="1448f-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="1448f-111">enum</span><span class="sxs-lookup"><span data-stu-id="1448f-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="1448f-112">delegate</span><span class="sxs-lookup"><span data-stu-id="1448f-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="1448f-113">C# kaynak dosyasında bir ad alanını açıkça bildirme olup olmadığına, bir varsayılan ad alanı derleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="1448f-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="1448f-114">Bazen genel ad alanı da adlandırılır bu adlandırılmamış ad alanı, her dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="1448f-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="1448f-115">Genel ad alanındaki herhangi bir tanımlayıcı, adlandırılmış bir ad alanını kullanmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1448f-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="1448f-116">Ad alanları örtük olarak genel erişimi vardır ve bu değiştirilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="1448f-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="1448f-117">Erişim değiştiricileri öğelere bir ad atamak için bkz [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="1448f-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="1448f-118">Ad alanı iki veya daha fazla bildirimlerinde tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1448f-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="1448f-119">Örneğin, aşağıdaki örnekte bir parçası olarak iki sınıf tanımlar `MyCompany` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="1448f-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="1448f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1448f-120">Example</span></span>  
 <span data-ttu-id="1448f-121">Aşağıdaki örnek, iç içe geçmiş bir ad alanında bir statik yöntem çağrısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1448f-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="1448f-122">Daha Fazla Bilgi İçin</span><span class="sxs-lookup"><span data-stu-id="1448f-122">For More Information</span></span>  
 <span data-ttu-id="1448f-123">Ad alanlarını kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="1448f-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="1448f-124">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="1448f-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="1448f-125">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1448f-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="1448f-126">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1448f-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1448f-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="1448f-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1448f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1448f-128">See Also</span></span>  
 [<span data-ttu-id="1448f-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1448f-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1448f-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1448f-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1448f-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1448f-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1448f-132">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1448f-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="1448f-133">using</span><span class="sxs-lookup"><span data-stu-id="1448f-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
