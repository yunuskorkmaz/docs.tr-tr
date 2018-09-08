---
title: Üye aşırı yüklemesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208237"
---
# <a name="member-overloading"></a><span data-ttu-id="879bb-102">Üye aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="879bb-102">Member Overloading</span></span>
<span data-ttu-id="879bb-103">Üye aşırı yüklemesi, iki veya daha fazla üye, yalnızca sayı veya parametre türünü farklılık gösterir ancak aynı ada sahip aynı türde oluşturma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="879bb-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="879bb-104">Örneğin, aşağıdaki içinde `WriteLine` yöntemi aşırı yüklüdür:</span><span class="sxs-lookup"><span data-stu-id="879bb-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="879bb-105">Yalnızca yöntemler, Oluşturucular ve Dizinli Özellikler parametreleri olabileceğinden, yalnızca bu üyeleri aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="879bb-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="879bb-106">Aşırı yükleme, kullanılabilirlik, üretkenlik ve yeniden kullanılabilir kitaplıklar okunabilirliğini geliştirmek için en önemli teknikleri biridir.</span><span class="sxs-lookup"><span data-stu-id="879bb-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="879bb-107">Parametre sayısına göre aşırı yüklemesi, daha basit sürümlerini Kurucular ve yöntemler sağlamak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="879bb-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="879bb-108">Parametre türü üzerinde aşırı yükleme üyelerinin farklı türleri seçili kümesi aynı işlemleri gerçekleştirmek için aynı üye adını kullanmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="879bb-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="879bb-109">**✓ DO** kısa aşırı yüklemeler tarafından kullanılan varsayılan belirtmek için açıklayıcı parametre adları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="879bb-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="879bb-110">**X AVOID** rasgele aşırı parametre adlarında değişen.</span><span class="sxs-lookup"><span data-stu-id="879bb-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="879bb-111">Başka bir aşırı parametre olarak aynı girişe bir aşırı parametre temsil ediyorsa, parametreleri aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="879bb-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="879bb-112">**X AVOID** parametrelerinde sıralama içinde tutarsız olan aşırı yüklenmiş üyeler.</span><span class="sxs-lookup"><span data-stu-id="879bb-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="879bb-113">Aynı adlı parametreleri, tüm aşırı yüklemeler aynı konumda görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="879bb-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="879bb-114">**✓ DO** (genişletilebilirlik gerekliyse) yalnızca en uzun aşırı sanal olun.</span><span class="sxs-lookup"><span data-stu-id="879bb-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="879bb-115">Kısa aşırı yüklemeleri yalnızca aracılığıyla için uzun bir aşırı yüklemesini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="879bb-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="879bb-116">**X DO NOT** kullanmak `ref` veya `out` üyeleri aşırı yüklemeyi değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="879bb-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="879bb-117">Bazı diller, benzer aşırı yüküne çağrıları çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="879bb-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="879bb-118">Ayrıca, stl'yi Bu aşırı genellikle tamamen farklı semantiklere sahip ve büyük olasılıkla aşırı ancak iki ayrı yöntem bunun yerine olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="879bb-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="879bb-119">**X DO NOT** aşırı aynı konuma ve benzer türleri parametrelerle henüz farklı semantiği ile sahip.</span><span class="sxs-lookup"><span data-stu-id="879bb-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="879bb-120">**✓ DO** izin `null` isteğe bağlı bağımsız değişkenler için geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="879bb-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="879bb-121">**✓ DO** varsayılan bağımsız değişkenler üyeleriyle tanımlama yerine aşırı üye kullanın.</span><span class="sxs-lookup"><span data-stu-id="879bb-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="879bb-122">Varsayılan bağımsız değişkenler, CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="879bb-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="879bb-123">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="879bb-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="879bb-124">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="879bb-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879bb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="879bb-125">See also</span></span>

- [<span data-ttu-id="879bb-126">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="879bb-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="879bb-127">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="879bb-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
