---
title: Eşitlik İşleçleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741697"
---
# <a name="equality-operators"></a><span data-ttu-id="b297a-102">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b297a-102">Equality Operators</span></span>
<span data-ttu-id="b297a-103">Bu bölümde eşitlik işleçlerini aşırı yükleme ve `operator==` ve eşitlik işleçleri olarak `operator!=` açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b297a-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="b297a-104">❌ eşitlik işleçlerinden birini aşırı yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="b297a-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="b297a-105">✔️ <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiğe ve benzer performans özelliklerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b297a-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="b297a-106">Bu genellikle eşitlik işleçleri aşırı yüklendiğinde `Object.Equals` geçersiz kılınmasının gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b297a-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="b297a-107">❌ eşitlik işleçlerinden özel durumlar oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b297a-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="b297a-108">Örneğin, `NullReferenceException`yapmak yerine bağımsız değişkenlerden biri null ise false döndürün.</span><span class="sxs-lookup"><span data-stu-id="b297a-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="b297a-109">Değer türlerinde eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="b297a-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="b297a-110">eşitlik anlamlı ise, değer türlerinde eşitlik işleçlerini aşırı yükleme ✔️.</span><span class="sxs-lookup"><span data-stu-id="b297a-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="b297a-111">Çoğu programlama dilinde, değer türleri için `operator==` varsayılan bir uygulama yoktur.</span><span class="sxs-lookup"><span data-stu-id="b297a-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="b297a-112">Başvuru türlerinde eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="b297a-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="b297a-113">❌ kesilebilir başvuru türlerinde eşitlik işleçlerini aşırı yüklemeyi ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="b297a-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="b297a-114">Birçok dilde başvuru türleri için yerleşik eşitlik işleçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b297a-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="b297a-115">Yerleşik operatörler genellikle başvuru eşitliğini uygular ve varsayılan davranış değer eşitliğine değiştirildiğinde çok sayıda geliştirici şaşırtır.</span><span class="sxs-lookup"><span data-stu-id="b297a-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="b297a-116">Bu sorun, sabit başvuru türleri için azaltıldığı için, değişiklik, başvuru eşitliği ve değer eşitlik arasındaki farkı fark ettiğini çok daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b297a-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="b297a-117">❌, başvuru eşitlemeden önemli ölçüde daha yavaş olacaksa, başvuru türlerinde eşitlik işleçlerini aşırı yüklemeyi ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="b297a-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="b297a-118">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b297a-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b297a-119">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="b297a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b297a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b297a-120">See also</span></span>

- [<span data-ttu-id="b297a-121">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b297a-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b297a-122">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b297a-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
