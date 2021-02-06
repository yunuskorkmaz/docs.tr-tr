---
description: 'Daha fazla bilgi edinin: üye aşırı yüklemesi'
title: Üye Aşırı Yüklemesi
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: d3a545bfec552686e55c9f713d58784497946819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641960"
---
# <a name="member-overloading"></a><span data-ttu-id="ebc07-103">Üye Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="ebc07-103">Member Overloading</span></span>

<span data-ttu-id="ebc07-104">Üye aşırı yüklemesi, aynı türde yalnızca parametre sayısı veya türünde farklı ancak aynı ada sahip iki veya daha fazla üye oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-104">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="ebc07-105">Örneğin, aşağıdaki, `WriteLine` yöntemi aşırı yüklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="ebc07-105">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="ebc07-106">Yalnızca Yöntemler, oluşturucular ve dizinli Özellikler parametrelere sahip olabileceğinden yalnızca bu Üyeler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-106">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="ebc07-107">Aşırı yükleme, yeniden kullanılabilir kitaplıkların kullanılabilirliğini, verimliliğini ve okunabilirliğini iyileştirmeye yönelik en önemli tekniklerden biridir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-107">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="ebc07-108">Parametrelerin sayısı üzerinde aşırı yükleme, oluşturucuların ve yöntemlerin daha basit sürümlerini sağlamayı olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="ebc07-108">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="ebc07-109">Parametre türü üzerinde aşırı yükleme, seçilen farklı türde bir küme üzerinde özdeş işlemler gerçekleştiren Üyeler için aynı üye adını kullanmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="ebc07-109">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="ebc07-110">✔️ daha kısa aşırı yüklemeler tarafından kullanılan varsayılan adı belirtmek için açıklayıcı parametre adları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="ebc07-110">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="ebc07-111">❌ Aşırı yüklerde rasgele değişen parametre adlarından KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="ebc07-111">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="ebc07-112">Bir aşırı yükteki bir parametre başka bir aşırı yükteki parametre ile aynı girişi gösteriyorsa, parametrelerin aynı ada sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-112">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="ebc07-113">❌ Aşırı yüklenmiş Üyeler içindeki parametrelerin sıralaması için tutarsız yapmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="ebc07-113">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="ebc07-114">Aynı ada sahip parametreler tüm aşırı yüklerdeki aynı konumda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-114">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="ebc07-115">✔️ yalnızca en uzun aşırı yükleme sanal (genişletilebilirlik gerekliyse) yapın.</span><span class="sxs-lookup"><span data-stu-id="ebc07-115">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="ebc07-116">Daha kısa aşırı yüklemeler yalnızca daha uzun bir aşırı yüklemeye çağrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-116">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="ebc07-117">❌`ref` `out` Üyeleri aşırı yüklemek için veya değiştiricilerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ebc07-117">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="ebc07-118">Bazı diller bunun gibi aşırı yüklemelerin çağrılarını çözemez.</span><span class="sxs-lookup"><span data-stu-id="ebc07-118">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="ebc07-119">Buna ek olarak, bu aşırı yüklemeler genellikle tamamen farklı semantiklere sahiptir ve muhtemelen aşırı yükleme olmaması gerekir, bunun yerine iki ayrı Yöntem</span><span class="sxs-lookup"><span data-stu-id="ebc07-119">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="ebc07-120">❌ Aynı konumda ve benzer türlerde parametrelere sahip tekrar yüklemeler yoktur, ancak bu farklı semantiklerdir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-120">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="ebc07-121">`null`isteğe bağlı bağımsız değişkenler için ✔️ izin verme.</span><span class="sxs-lookup"><span data-stu-id="ebc07-121">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="ebc07-122">✔️ Varsayılan bağımsız değişkenlerle üyeleri tanımlamak yerine üye aşırı yüklemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebc07-122">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="ebc07-123">Varsayılan bağımsız değişkenler CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ebc07-123">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="ebc07-124">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ebc07-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ebc07-125">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="ebc07-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ebc07-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebc07-126">See also</span></span>

- [<span data-ttu-id="ebc07-127">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ebc07-127">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="ebc07-128">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ebc07-128">Framework Design Guidelines</span></span>](index.md)
