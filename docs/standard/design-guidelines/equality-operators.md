---
title: Eşitlik İşleçleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27550a8fd8292029cad9c2e699374a190b1a532e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988468"
---
# <a name="equality-operators"></a><span data-ttu-id="825b0-102">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="825b0-102">Equality Operators</span></span>
<span data-ttu-id="825b0-103">Bu bölümde, aşırı yüklerken eşitlik işleci açıklar ve başvurduğu `operator==` ve `operator!=` eşitlik işleçleri olarak.</span><span class="sxs-lookup"><span data-stu-id="825b0-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="825b0-104">**X DO NOT** eşitlik işleçleri ve diğer aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="825b0-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="825b0-105">**✓ DO** emin <xref:System.Object.Equals%2A?displayProperty=nameWithType> ve eşitlik işleçleri tam olarak aynı semantiği ve benzer performans özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="825b0-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="825b0-106">Bu genellikle anlamına `Object.Equals` eşitlik operatörleri aşırı yüklendiğinde geçersiz kılınması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="825b0-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="825b0-107">**X AVOID** eşitlik işleçleri özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="825b0-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="825b0-108">Örneğin, bağımsız değişkenlerden biri oluşturmak yerine null ise yanlış geri `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="825b0-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="825b0-109">Değer türleri üzerinde eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="825b0-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="825b0-110">**✓ DO** eşitlik anlamlı ise, değer türleri üzerinde eşitlik işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="825b0-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="825b0-111">Çoğu programlama dilinde, hiçbir varsayılan uygulaması olduğundan `operator==` değer türleri için.</span><span class="sxs-lookup"><span data-stu-id="825b0-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="825b0-112">Başvuru türlerinde eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="825b0-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="825b0-113">**X AVOID** kesilebilir başvuru türleri üzerinde eşitlik işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="825b0-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="825b0-114">Birçok dil başvuru türleri için yerleşik eşitlik işleçleri sahip.</span><span class="sxs-lookup"><span data-stu-id="825b0-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="825b0-115">Yerleşik işleçler, genellikle başvuru eşitliği uygulamak ve birçok geliştiricinin varsayılan davranışı için değer eşitliği değiştirildiğinde şaşırmayın.</span><span class="sxs-lookup"><span data-stu-id="825b0-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="825b0-116">Bu sorun, değiştirilemezlik çok başvuru eşitliği değer eşitliği arasındaki fark zorlaştırır çünkü değişmez başvuru türleri için azalır.</span><span class="sxs-lookup"><span data-stu-id="825b0-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="825b0-117">**X AVOID** uygulama önemli ölçüde daha yavaş, başvuru eşitliği olacaksa başvuru türlerinde eşitlik işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="825b0-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="825b0-118">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="825b0-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="825b0-119">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="825b0-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825b0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="825b0-120">See also</span></span>

- [<span data-ttu-id="825b0-121">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="825b0-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="825b0-122">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="825b0-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
