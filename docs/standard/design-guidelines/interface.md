---
title: Arabirim Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 9f8ff38d5825091d4d5d3716ed6025a8d04c592d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821014"
---
# <a name="interface-design"></a><span data-ttu-id="71083-102">Arabirim Tasarımı</span><span class="sxs-lookup"><span data-stu-id="71083-102">Interface Design</span></span>
<span data-ttu-id="71083-103">Çoğu API 'Ler sınıflar ve yapılar kullanılarak en iyi modellense de, arabirimlerin daha uygun veya tek seçenek olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="71083-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="71083-104">CLR birden çok devralmayı desteklemez (yani, CLR sınıfları birden fazla taban sınıftan devralamaz), ancak türlerin bir temel sınıftan devralmaya ek olarak bir veya daha fazla arabirim uygulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="71083-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="71083-105">Bu nedenle, arabirimler genellikle birden çok devralmanın etkisini elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71083-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="71083-106">Örneğin, <xref:System.IDisposable> türlerin katılmak istedikleri diğer devralma hiyerarşisinden bağımsız olarak elden atımı desteklemesini sağlayan bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="71083-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="71083-107">Bir arabirimin tanımlanmasıyla ilgili diğer durum, bazı değer türleri dahil olmak üzere çeşitli türlerde desteklenebilir ortak bir arabirim oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="71083-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="71083-108">Değer türleri dışındaki türlerden devralınabilir <xref:System.ValueType> , ancak arabirimler uygulayabilir, bu nedenle ortak temel tür sağlamak için tek seçenektir.</span><span class="sxs-lookup"><span data-stu-id="71083-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="71083-109">✔️, bazı ortak API 'leri değer türlerini içeren bir tür kümesi tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="71083-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="71083-110">daha önce başka bir türden daha önce devraldığı türler üzerinde işlevselliğini desteklemeniz gerekiyorsa, bir arabirim tanımlamayı düşünün ✔️.</span><span class="sxs-lookup"><span data-stu-id="71083-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="71083-111">❌ İşaretleyici arabirimlerini kullanmaktan KAÇıNıN (üye olmayan arabirimler).</span><span class="sxs-lookup"><span data-stu-id="71083-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="71083-112">Bir sınıfı belirli bir özelliğe (işaret) sahip olacak şekilde işaretlemeniz gerekiyorsa, genel olarak, bir arabirim yerine özel bir öznitelik kullanın.</span><span class="sxs-lookup"><span data-stu-id="71083-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="71083-113">✔️, bir arabirimin uygulanması olan en az bir tür sağlar.</span><span class="sxs-lookup"><span data-stu-id="71083-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="71083-114">Bunu yapmak, arabirimin tasarımını doğrulamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="71083-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="71083-115">Örneğin, <xref:System.Collections.Generic.List%601> arabirimin bir uygulamasıdır <xref:System.Collections.Generic.IList%601> .</span><span class="sxs-lookup"><span data-stu-id="71083-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="71083-116">✔️, tanımladığınız her arabirimi tüketen en az bir API (bir parametre olarak arabirimi veya arabirim olarak yazılmış bir özellik) sağlar.</span><span class="sxs-lookup"><span data-stu-id="71083-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="71083-117">Bunu yapmak, arabirim tasarımını doğrulamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="71083-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="71083-118">Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="71083-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="71083-119">❌ Daha önce sevk edilen bir arabirime üye eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="71083-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="71083-120">Bunun yapılması, arabirimin uygulamalarını bozar.</span><span class="sxs-lookup"><span data-stu-id="71083-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="71083-121">Sürüm oluşturma sorunlarından kaçınmak için yeni bir arabirim oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="71083-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="71083-122">Bu kılavuzlar bölümünde açıklanan durumlar haricinde, genel olarak, yönetilen kod yeniden kullanılabilir kitaplıklarını tasarlarken arabirimler yerine sınıfları seçin.</span><span class="sxs-lookup"><span data-stu-id="71083-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="71083-123">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="71083-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="71083-124">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="71083-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="71083-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71083-125">See also</span></span>

- [<span data-ttu-id="71083-126">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="71083-126">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="71083-127">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="71083-127">Framework Design Guidelines</span></span>](index.md)
