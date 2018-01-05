---
title: "Soyutlamalar (Soyut türler ve arabirimler)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="39cca-102">Soyutlamalar (Soyut türler ve arabirimler)</span><span class="sxs-lookup"><span data-stu-id="39cca-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="39cca-103">Bir Özet bir sözleşme açıklar ancak sözleşme tam uygulamasını sağlamaz türüdür.</span><span class="sxs-lookup"><span data-stu-id="39cca-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="39cca-104">Soyutlamalar genellikle soyut sınıflar veya arabirimleri olarak uygulanır ve sözleşme uygulama türleri gerekli semantiği açıklayan başvuru belgeleri iyi tanımlanmış bir dizi birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="39cca-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="39cca-105">.NET Framework'teki en önemli soyutlamalar bazıları <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, ve <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="39cca-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="39cca-106">Bir Özet sözleşmenin desteklediği somut bir türde uygulama ve bu somut türde framework API'leri alabilir (üzerinde işletim ile) kullanılarak çerçeveleri genişletebilirsiniz Özet.</span><span class="sxs-lookup"><span data-stu-id="39cca-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="39cca-107">Test zaman dayanacak yapabiliyor anlamlı ve yararlı bir soyutlama tasarlamak çok zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="39cca-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="39cca-108">Ana zorluk üyeleri, daha fazla ve en az doğru yetenek kümesini almaktır.</span><span class="sxs-lookup"><span data-stu-id="39cca-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="39cca-109">Bir Özet çok fazla sayıda üye varsa, zor veya uygulamak bile imkansız olur.</span><span class="sxs-lookup"><span data-stu-id="39cca-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="39cca-110">Taahhüt edilen işlevselliği için çok az sayıda üye varsa, birçok ilginç senaryolarda gereksiz olur.</span><span class="sxs-lookup"><span data-stu-id="39cca-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="39cca-111">Çerçeve içinde çok fazla soyutlamalar kullanılabilirlik framework'ün da olumsuz etkiler.</span><span class="sxs-lookup"><span data-stu-id="39cca-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="39cca-112">Genellikle, bir Özet nasıl somut uygulamaları üzerinde soyutlama işletim API'leri ve daha büyük resmi içine uyduğunu anlama olmadan anlamak oldukça zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="39cca-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="39cca-113">Ayrıca, soyutlamalar ve üyeleri hangi sıklıkta bunları şifreli ve unapproachable kullanımları daha geniş bağlamında ilk anlama olmadan yapar mutlaka soyut adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="39cca-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="39cca-114">Ancak, diğer genişletilebilirlik mekanizmaları genellikle eşleşemez son derece güçlü genişletilebilirlik soyutlamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="39cca-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="39cca-115">Eklentileri gibi birçok mimari düzenleri çekirdek tersine çevirme (IOC) denetim, ardışık düzen ve benzeri altındadır.</span><span class="sxs-lookup"><span data-stu-id="39cca-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="39cca-116">Ayrıca çerçeveleri edilebilirliğini için son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="39cca-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="39cca-117">İyi soyutlamalar birim testi amacıyla ağır bağımlılıkları çıkışı saplama olanaklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="39cca-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="39cca-118">Özet olarak, soyutlamalar modern nesne yönelimli çerçeveleri sought-after zenginliğini için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="39cca-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="39cca-119">**X yok** birkaç somut uygulamaları ve soyutlama kullanan API'ler geliştirerek sınanır sürece soyutlamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="39cca-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="39cca-120">**✓ YAPMAK** bir Özet tasarlarken, bir Özet sınıf arasında bir arabirim dikkatle seçin.</span><span class="sxs-lookup"><span data-stu-id="39cca-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="39cca-121">**✓ DÜŞÜNÜN** başvuru testleri soyutlamalar somut uygulamaları için sağlama.</span><span class="sxs-lookup"><span data-stu-id="39cca-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="39cca-122">Bu tür testleri, kullanıcıların kendi uygulamalarını doğru sözleşmesini uygulama olup olmadığını sınamak izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="39cca-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="39cca-123">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="39cca-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="39cca-124">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="39cca-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cca-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39cca-125">See Also</span></span>  
 [<span data-ttu-id="39cca-126">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="39cca-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="39cca-127">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="39cca-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
