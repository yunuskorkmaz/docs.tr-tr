---
title: ad alanı anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b5c6b8081c188d5b184930222d54ad8f4b5d7a71
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242769"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="505e2-102">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="505e2-102">namespace (C# Reference)</span></span>

<span data-ttu-id="505e2-103">`namespace` Anahtar sözcüğü, bir dizi ilgili nesneleri içeren bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="505e2-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="505e2-104">Kod öğelerini düzenlemek ve genel olarak benzersiz türleri oluşturmak için bir ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="505e2-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="505e2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="505e2-105">Remarks</span></span>

<span data-ttu-id="505e2-106">Ad alanı içinde sıfır veya daha fazla türlerinden birini bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="505e2-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="505e2-107">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="505e2-107">another namespace</span></span>

- [<span data-ttu-id="505e2-108">class</span><span class="sxs-lookup"><span data-stu-id="505e2-108">class</span></span>](class.md)

- [<span data-ttu-id="505e2-109">interface</span><span class="sxs-lookup"><span data-stu-id="505e2-109">interface</span></span>](interface.md)

- [<span data-ttu-id="505e2-110">struct</span><span class="sxs-lookup"><span data-stu-id="505e2-110">struct</span></span>](struct.md)

- [<span data-ttu-id="505e2-111">enum</span><span class="sxs-lookup"><span data-stu-id="505e2-111">enum</span></span>](enum.md)

- [<span data-ttu-id="505e2-112">delegate</span><span class="sxs-lookup"><span data-stu-id="505e2-112">delegate</span></span>](delegate.md)

<span data-ttu-id="505e2-113">Açıkça bir C# kaynak dosyası içinde bir ad alanı bildirimini olsun veya olmasın, derleyici varsayılan bir ad alanı ekler.</span><span class="sxs-lookup"><span data-stu-id="505e2-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="505e2-114">Bazen genel ad alanı adlandırılır, bu adlandırılmamış ad, her bir dosyanın yok.</span><span class="sxs-lookup"><span data-stu-id="505e2-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="505e2-115">Genel ad alanındaki herhangi bir tanımlayıcı adlandırılmış bir ad alanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="505e2-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="505e2-116">Ad alanları, örtük olarak genel erişimi vardır ve bu değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="505e2-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="505e2-117">Bir ad alanındaki öğeler atayabilirsiniz erişim değiştiricileri ile ilgili tartışma için bkz: [erişim değiştiricileri](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="505e2-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="505e2-118">İki veya daha fazla bildirimlerinde ad alanı tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="505e2-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="505e2-119">Örneğin, aşağıdaki örnekte iki sınıf kapsamında tanımlar `MyCompany` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="505e2-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="505e2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="505e2-120">Example</span></span>

<span data-ttu-id="505e2-121">Aşağıdaki örnek, bir iç içe geçmiş ad alanındaki statik bir yöntemi çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="505e2-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a><span data-ttu-id="505e2-122">İlgili kaynaklar</span><span class="sxs-lookup"><span data-stu-id="505e2-122">Related resources</span></span>

<span data-ttu-id="505e2-123">Ad alanlarını kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="505e2-123">For more information about using namespaces, see the following topics:</span></span>

- [<span data-ttu-id="505e2-124">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="505e2-124">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

- [<span data-ttu-id="505e2-125">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="505e2-125">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)

- [<span data-ttu-id="505e2-126">Nasıl yapılır: Genel Namespace diğer adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="505e2-126">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="505e2-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="505e2-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="505e2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="505e2-128">See also</span></span>

- [<span data-ttu-id="505e2-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="505e2-129">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="505e2-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="505e2-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="505e2-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="505e2-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="505e2-132">Ad Alanı Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="505e2-132">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="505e2-133">using</span><span class="sxs-lookup"><span data-stu-id="505e2-133">using</span></span>](using.md)