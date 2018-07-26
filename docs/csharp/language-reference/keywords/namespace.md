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
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245622"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="b8bc9-102">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b8bc9-102">namespace (C# Reference)</span></span>
<span data-ttu-id="b8bc9-103">`namespace` Anahtar sözcüğü, bir dizi ilgili nesneleri içeren bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="b8bc9-104">Kod öğelerini düzenlemek ve genel olarak benzersiz türleri oluşturmak için bir ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="b8bc9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8bc9-105">Remarks</span></span>  
 <span data-ttu-id="b8bc9-106">Ad alanı içinde bir veya daha fazla türlerinden birini bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b8bc9-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="b8bc9-107">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="b8bc9-107">another namespace</span></span>  
  
-   [<span data-ttu-id="b8bc9-108">class</span><span class="sxs-lookup"><span data-stu-id="b8bc9-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="b8bc9-109">interface</span><span class="sxs-lookup"><span data-stu-id="b8bc9-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="b8bc9-110">struct</span><span class="sxs-lookup"><span data-stu-id="b8bc9-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="b8bc9-111">enum</span><span class="sxs-lookup"><span data-stu-id="b8bc9-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="b8bc9-112">delegate</span><span class="sxs-lookup"><span data-stu-id="b8bc9-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="b8bc9-113">Açıkça bir C# kaynak dosyası içinde bir ad alanı bildirimini olsun veya olmasın, derleyici varsayılan bir ad alanı ekler.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="b8bc9-114">Bazen genel ad alanı adlandırılır, bu adlandırılmamış ad, her bir dosyanın yok.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="b8bc9-115">Genel ad alanındaki herhangi bir tanımlayıcı adlandırılmış bir ad alanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="b8bc9-116">Ad alanları, örtük olarak genel erişimi vardır ve bu değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="b8bc9-117">Bir ad alanındaki öğeler atayabilirsiniz erişim değiştiricileri ile ilgili tartışma için bkz: [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b8bc9-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="b8bc9-118">İki veya daha fazla bildirimlerinde ad alanı tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="b8bc9-119">Örneğin, aşağıdaki örnekte iki sınıf kapsamında tanımlar `MyCompany` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="b8bc9-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="b8bc9-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8bc9-120">Example</span></span>  
 <span data-ttu-id="b8bc9-121">Aşağıdaki örnek, bir iç içe geçmiş ad alanındaki statik bir yöntemi çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="b8bc9-122">Daha Fazla Bilgi İçin</span><span class="sxs-lookup"><span data-stu-id="b8bc9-122">For More Information</span></span>  
 <span data-ttu-id="b8bc9-123">Ad alanlarını kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="b8bc9-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="b8bc9-124">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="b8bc9-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="b8bc9-125">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8bc9-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="b8bc9-126">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8bc9-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="b8bc9-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b8bc9-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8bc9-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8bc9-128">See Also</span></span>  
 [<span data-ttu-id="b8bc9-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b8bc9-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b8bc9-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b8bc9-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b8bc9-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b8bc9-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b8bc9-132">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b8bc9-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="b8bc9-133">using</span><span class="sxs-lookup"><span data-stu-id="b8bc9-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
