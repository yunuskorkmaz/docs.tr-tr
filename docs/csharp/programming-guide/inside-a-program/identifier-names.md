---
title: Tanımlayıcı adları
description: C# Programlama dilinde geçerli tanımlayıcı adları için kuralları öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589345"
---
# <a name="identifier-names"></a><span data-ttu-id="b0f27-103">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="b0f27-103">Identifier names</span></span>

<span data-ttu-id="b0f27-104">**Tanımlayıcı** , bir türe atadığınız addır (sınıf, arabirim, yapı, temsilci veya Enum), üye, değişken veya ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b0f27-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="b0f27-105">Geçerli tanımlayıcılar şu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="b0f27-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="b0f27-106">Tanımlayıcılar bir harfle başlamalı veya `_`.</span><span class="sxs-lookup"><span data-stu-id="b0f27-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="b0f27-107">Tanımlayıcılar Unicode harf karakterleri, ondalık basamak karakterleri, Unicode bağlantı karakterleri, Unicode birleştiren karakterler veya Unicode biçimlendirme karakterlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b0f27-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="b0f27-108">Unicode kategorileri hakkında daha fazla bilgi için bkz. [Unicode kategori veritabanı](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="b0f27-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="b0f27-109">Tanımlayıcıda `@` öneki kullanarak, anahtar C# sözcüklerle eşleşen tanımlayıcılar bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0f27-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="b0f27-110">`@` Tanımlayıcı adının bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="b0f27-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="b0f27-111">Örneğin, `@if` adlı `if`bir tanımlayıcı bildirir.</span><span class="sxs-lookup"><span data-stu-id="b0f27-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="b0f27-112">Bu tam [tanımlayıcılar](../../language-reference/tokens/verbatim.md) öncelikle diğer dillerde belirtilen tanımlayıcılarla birlikte çalışabilirlik içindir.</span><span class="sxs-lookup"><span data-stu-id="b0f27-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="b0f27-113">Geçerli tanımlayıcıların tamamen tanımı için, [ C# dil belirtiminde tanımlayıcılar konusuna](../../../../_csharplang/spec/lexical-structure.md#identifiers)bakın.</span><span class="sxs-lookup"><span data-stu-id="b0f27-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="b0f27-114">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="b0f27-114">Naming conventions</span></span>

<span data-ttu-id="b0f27-115">Kuralların yanı sıra, .NET API 'Lerinde kullanılan bir dizi tanımlayıcı [adlandırma kuralı](../../../standard/design-guidelines/naming-guidelines.md) vardır.</span><span class="sxs-lookup"><span data-stu-id="b0f27-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="b0f27-116">Kural gereği, C# programlar tür `PascalCase` adları, ad alanları ve tüm genel Üyeler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0f27-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="b0f27-117">Ayrıca, aşağıdaki kurallar ortaktır:</span><span class="sxs-lookup"><span data-stu-id="b0f27-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="b0f27-118">Arabirim adları sermaye `I`ile başlar.</span><span class="sxs-lookup"><span data-stu-id="b0f27-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="b0f27-119">Öznitelik türleri kelimeyle `Attribute`biter.</span><span class="sxs-lookup"><span data-stu-id="b0f27-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="b0f27-120">Sabit listesi türleri, bayraklar için tekil bir ad ve bayraklar için bir çoğul ad kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0f27-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="b0f27-121">Tanımlayıcılar iki ardışık `_` karakter içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="b0f27-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="b0f27-122">Bu adlar derleyicinin ürettiği tanımlayıcılar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b0f27-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0f27-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b0f27-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0f27-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0f27-124">See also</span></span>

- [<span data-ttu-id="b0f27-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0f27-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b0f27-126">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="b0f27-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="b0f27-127">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="b0f27-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="b0f27-128">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b0f27-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="b0f27-129">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b0f27-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="b0f27-130">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="b0f27-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="b0f27-131">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b0f27-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="b0f27-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="b0f27-132">Delegates</span></span>](../delegates/index.md)
