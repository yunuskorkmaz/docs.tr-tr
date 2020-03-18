---
title: Tanımlayıcı adları
description: C# programlama dilinde geçerli tanımlayıcı adlarının kurallarını öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673374"
---
# <a name="identifier-names"></a><span data-ttu-id="e5d16-103">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="e5d16-103">Identifier names</span></span>

<span data-ttu-id="e5d16-104">**Tanımlayıcı,** bir türe (sınıf, arabirim, yapı, temsilci veya enum), üye, değişken veya ad alanına atadığınız addır.</span><span class="sxs-lookup"><span data-stu-id="e5d16-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="e5d16-105">Geçerli tanımlayıcılar aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="e5d16-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="e5d16-106">Tanımlayıcılar bir harfle başlamalı, ya `_`da.</span><span class="sxs-lookup"><span data-stu-id="e5d16-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="e5d16-107">Tanımlayıcılar Unicode harf karakterleri, ondalık basamak karakterleri, Unicode bağlama karakterleri, Unicode birleştiren karakterler veya Unicode biçimlendirme karakterleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e5d16-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="e5d16-108">Unicode kategorileri hakkında daha fazla bilgi için [Unicode Kategori Veritabanı'na](https://www.unicode.org/reports/tr44/)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5d16-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="e5d16-109">Tanımlayıcıdaki `@` öneki kullanarak C# anahtar kelimeleriyle eşleşen tanımlayıcıları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5d16-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="e5d16-110">Tanımlayıcı `@` adının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="e5d16-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="e5d16-111">Örneğin, `@if` adlı `if`bir tanımlayıcı bildirir.</span><span class="sxs-lookup"><span data-stu-id="e5d16-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="e5d16-112">Bu [kelime tanımlayıcıları](../../language-reference/tokens/verbatim.md) öncelikle diğer dillerde bildirilen tanımlayıcılarla birlikte çalışabilirlik içindir.</span><span class="sxs-lookup"><span data-stu-id="e5d16-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="e5d16-113">Geçerli tanımlayıcıların tam bir tanımı için [C# Dil Belirtiminde tanımlayıcılar konusuna](../../../../_csharplang/spec/lexical-structure.md#identifiers)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5d16-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="e5d16-114">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e5d16-114">Naming conventions</span></span>

<span data-ttu-id="e5d16-115">Kurallara ek olarak, .NET API'leri boyunca kullanılan bir dizi tanımlayıcı [adlandırma kuralı](../../../standard/design-guidelines/naming-guidelines.md) vardır.</span><span class="sxs-lookup"><span data-stu-id="e5d16-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="e5d16-116">C# programları, kural `PascalCase` kuralına göre tür adları, ad alanları ve tüm ortak üyeler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d16-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="e5d16-117">Buna ek olarak, aşağıdaki sözleşmeler yaygındır:</span><span class="sxs-lookup"><span data-stu-id="e5d16-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="e5d16-118">Arabirim adları büyük `I`harfle başlar.</span><span class="sxs-lookup"><span data-stu-id="e5d16-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="e5d16-119">Öznitelik türleri sözcüğüyle `Attribute`birlikte sona erer.</span><span class="sxs-lookup"><span data-stu-id="e5d16-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="e5d16-120">Enum türleri, bayrak olmayanlar için tekil bir ad ve bayraklar için çoğul bir ad kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5d16-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="e5d16-121">Tanımlayıcılar iki ardışık `_` karakter içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="e5d16-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="e5d16-122">Bu adlar derleyici oluşturulan tanımlayıcılar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5d16-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5d16-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e5d16-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5d16-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5d16-124">See also</span></span>

- [<span data-ttu-id="e5d16-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e5d16-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e5d16-126">C# Programı İçinde</span><span class="sxs-lookup"><span data-stu-id="e5d16-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="e5d16-127">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e5d16-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e5d16-128">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e5d16-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="e5d16-129">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="e5d16-129">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="e5d16-130">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="e5d16-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="e5d16-131">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e5d16-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="e5d16-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e5d16-132">Delegates</span></span>](../delegates/index.md)
