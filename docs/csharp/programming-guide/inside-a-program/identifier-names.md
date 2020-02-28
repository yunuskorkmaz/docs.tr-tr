---
title: Tanımlayıcı adları
description: C# Programlama dilinde geçerli tanımlayıcı adları için kuralları öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673374"
---
# <a name="identifier-names"></a><span data-ttu-id="9114c-103">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="9114c-103">Identifier names</span></span>

<span data-ttu-id="9114c-104">**Tanımlayıcı** , bir türe atadığınız addır (sınıf, arabirim, yapı, temsilci veya Enum), üye, değişken veya ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9114c-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="9114c-105">Geçerli tanımlayıcılar şu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="9114c-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="9114c-106">Tanımlayıcılar bir harfle başlamalı veya `_`.</span><span class="sxs-lookup"><span data-stu-id="9114c-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="9114c-107">Tanımlayıcılar Unicode harf karakterleri, ondalık basamak karakterleri, Unicode bağlantı karakterleri, Unicode birleştiren karakterler veya Unicode biçimlendirme karakterlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9114c-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="9114c-108">Unicode kategorileri hakkında daha fazla bilgi için bkz. [Unicode kategori veritabanı](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="9114c-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="9114c-109">Tanımlayıcıda `@` önekini kullanarak, C# anahtar sözcüklerle eşleşen tanımlayıcılar bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9114c-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="9114c-110">`@` tanımlayıcı adının bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="9114c-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="9114c-111">Örneğin, `@if` `if`adlı bir tanımlayıcı bildirir.</span><span class="sxs-lookup"><span data-stu-id="9114c-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="9114c-112">Bu tam [tanımlayıcılar](../../language-reference/tokens/verbatim.md) öncelikle diğer dillerde belirtilen tanımlayıcılarla birlikte çalışabilirlik içindir.</span><span class="sxs-lookup"><span data-stu-id="9114c-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="9114c-113">Geçerli tanımlayıcıların tamamen tanımı için, [ C# dil belirtiminde tanımlayıcılar konusuna](../../../../_csharplang/spec/lexical-structure.md#identifiers)bakın.</span><span class="sxs-lookup"><span data-stu-id="9114c-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="9114c-114">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="9114c-114">Naming conventions</span></span>

<span data-ttu-id="9114c-115">Kuralların yanı sıra, .NET API 'Lerinde kullanılan bir dizi tanımlayıcı [adlandırma kuralı](../../../standard/design-guidelines/naming-guidelines.md) vardır.</span><span class="sxs-lookup"><span data-stu-id="9114c-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="9114c-116">Kural gereği, C# programlar tür adları, ad alanları ve tüm genel üyeler için `PascalCase` kullanır.</span><span class="sxs-lookup"><span data-stu-id="9114c-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="9114c-117">Ayrıca, aşağıdaki kurallar ortaktır:</span><span class="sxs-lookup"><span data-stu-id="9114c-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="9114c-118">Arabirim adları, büyük bir `I`başlar.</span><span class="sxs-lookup"><span data-stu-id="9114c-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="9114c-119">Öznitelik türleri `Attribute`sözcüğüyle biter.</span><span class="sxs-lookup"><span data-stu-id="9114c-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="9114c-120">Sabit listesi türleri, bayraklar için tekil bir ad ve bayraklar için bir çoğul ad kullanır.</span><span class="sxs-lookup"><span data-stu-id="9114c-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="9114c-121">Tanımlayıcılar iki ardışık `_` karakter içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="9114c-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="9114c-122">Bu adlar derleyicinin ürettiği tanımlayıcılar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9114c-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9114c-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9114c-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9114c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9114c-124">See also</span></span>

- [<span data-ttu-id="9114c-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9114c-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9114c-126">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="9114c-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="9114c-127">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9114c-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9114c-128">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="9114c-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="9114c-129">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="9114c-129">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="9114c-130">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="9114c-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="9114c-131">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="9114c-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="9114c-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="9114c-132">Delegates</span></span>](../delegates/index.md)
