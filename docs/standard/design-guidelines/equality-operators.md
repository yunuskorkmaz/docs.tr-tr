---
title: Eşitlik İşleçleri
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 2331a852adb4dd254af85060a5077f454bcfe0eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734432"
---
# <a name="equality-operators"></a><span data-ttu-id="6e46f-102">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6e46f-102">Equality Operators</span></span>

<span data-ttu-id="6e46f-103">Bu bölüm, eşitlik işleçlerini aşırı yüklemeyi ve `operator==` `operator!=` eşitlik işleçlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e46f-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="6e46f-104">❌ Farklı bir eşitlik işleçlerinden birini aşırı yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="6e46f-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="6e46f-105">✔️, <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçlerinin tam olarak aynı semantiğe ve benzer performans özelliklerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6e46f-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="6e46f-106">Bu genellikle `Object.Equals` eşitlik işleçleri aşırı yüklendiğinde geçersiz kılınması gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e46f-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="6e46f-107">❌ Eşitlik işleçlerinden özel durumlar oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="6e46f-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="6e46f-108">Örneğin, bağımsız değişkenlerden biri oluşturmak yerine null ise false döndürün `NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="6e46f-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="6e46f-109">Değer türlerinde eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="6e46f-109">Equality Operators on Value Types</span></span>

 <span data-ttu-id="6e46f-110">eşitlik anlamlı ise, değer türlerinde eşitlik işleçlerini aşırı yükleme ✔️.</span><span class="sxs-lookup"><span data-stu-id="6e46f-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="6e46f-111">Çoğu programlama dilinde, değer türleri için varsayılan bir uygulama yoktur `operator==` .</span><span class="sxs-lookup"><span data-stu-id="6e46f-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="6e46f-112">Başvuru türlerinde eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="6e46f-112">Equality Operators on Reference Types</span></span>

 <span data-ttu-id="6e46f-113">❌ Değişebilir başvuru türlerinde eşitlik işleçlerini aşırı yüklemeyi ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="6e46f-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="6e46f-114">Birçok dilde başvuru türleri için yerleşik eşitlik işleçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="6e46f-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="6e46f-115">Yerleşik operatörler genellikle başvuru eşitliğini uygular ve varsayılan davranış değer eşitliğine değiştirildiğinde çok sayıda geliştirici şaşırtır.</span><span class="sxs-lookup"><span data-stu-id="6e46f-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="6e46f-116">Bu sorun, sabit başvuru türleri için azaltıldığı için, değişiklik, başvuru eşitliği ve değer eşitlik arasındaki farkı fark ettiğini çok daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6e46f-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="6e46f-117">❌ Uygulama, başvuru eşitlemeden önemli ölçüde daha yavaş olacaksa, başvuru türlerinde eşitlik işleçlerini aşırı yüklemeden KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="6e46f-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="6e46f-118">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6e46f-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6e46f-119">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="6e46f-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6e46f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e46f-120">See also</span></span>

- [<span data-ttu-id="6e46f-121">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6e46f-121">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="6e46f-122">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6e46f-122">Usage Guidelines</span></span>](usage-guidelines.md)
