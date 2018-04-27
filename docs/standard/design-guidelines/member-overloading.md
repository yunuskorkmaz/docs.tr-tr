---
title: Üye aşırı yüklemesi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 546db0540cf7852b40678476f732663369b15824
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="member-overloading"></a><span data-ttu-id="63c9a-102">Üye aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="63c9a-102">Member Overloading</span></span>
<span data-ttu-id="63c9a-103">Üye aşırı yüklemesi, iki veya daha fazla üye, yalnızca sayısını veya parametre türünü farklılık gösterir ancak aynı ada sahip aynı türde oluşturmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="63c9a-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="63c9a-104">Örneğin, aşağıdakileri de `WriteLine` yöntemi aşırı yüklenmiş:</span><span class="sxs-lookup"><span data-stu-id="63c9a-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="63c9a-105">Yalnızca yöntemleri oluşturucular ve Dizinli Özellikler parametreleri olabileceğinden, bu üyeler yalnızca aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="63c9a-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="63c9a-106">Aşırı yüklemesi, kullanılabilirlik, verimliliği ve yeniden kullanılabilir kitaplıkları okunabilirliğini artırmak için en önemli teknikler biridir.</span><span class="sxs-lookup"><span data-stu-id="63c9a-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="63c9a-107">Parametrelerin sayısı aşırı oluşturucular ve yöntemleri daha basit sürümlerini sağlamak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="63c9a-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="63c9a-108">Parametre türü aşırı yüklemesi farklı türleri seçili kümesi üzerinde aynı işlemler üyeleri için aynı üye adı kullanmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="63c9a-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="63c9a-109">**✓ YAPMAK** kısa aşırı yüklemeler tarafından kullanılan varsayılan belirtmek için açıklayıcı parametre adları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="63c9a-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="63c9a-110">**KAÇININ x** rasgele aşırı parametre adlarında değişen.</span><span class="sxs-lookup"><span data-stu-id="63c9a-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="63c9a-111">Aynı giriş başka bir aşırı içindeki bir parametre olarak bir aşırı parametresinde temsil ediyorsa parametreleri aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="63c9a-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="63c9a-112">**KAÇININ x** parametrelerinde sıralama içinde tutarsız olan aşırı yüklenmiş üyeler.</span><span class="sxs-lookup"><span data-stu-id="63c9a-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="63c9a-113">Aynı adlı parametreleri, tüm aşırı aynı konumda görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="63c9a-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="63c9a-114">**✓ YAPMAK** (genişletilebilirlik gerekliyse) yalnızca en uzun aşırı sanal olun.</span><span class="sxs-lookup"><span data-stu-id="63c9a-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="63c9a-115">Daha kısa aşırı yalnızca üzerinden uzun bir aşırı yüklemesine çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="63c9a-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="63c9a-116">**X yok** kullanmak `ref` veya `out` üyeleri aşırı yüklemeyi değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="63c9a-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="63c9a-117">Bazı diller şöyle aşırı çağrıları çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="63c9a-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="63c9a-118">Ayrıca, bu tür aşırı genellikle tamamen farklı semantiklerine sahip ve büyük olasılıkla aşırı ancak iki ayrı yöntem bunun yerine olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="63c9a-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="63c9a-119">**X yok** aşırı aynı konuma ve benzer türleri parametrelerle henüz farklı semantiği ile sahip.</span><span class="sxs-lookup"><span data-stu-id="63c9a-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="63c9a-120">**✓ YAPMAK** izin `null` isteğe bağlı bağımsız değişkenler için geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="63c9a-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="63c9a-121">**✓ YAPMAK** varsayılan bağımsız değişkenler üyeleriyle tanımlama yerine aşırı üye kullanın.</span><span class="sxs-lookup"><span data-stu-id="63c9a-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="63c9a-122">Varsayılan bağımsız değişkenler, CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="63c9a-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="63c9a-123">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="63c9a-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="63c9a-124">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="63c9a-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c9a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63c9a-125">See Also</span></span>  
 [<span data-ttu-id="63c9a-126">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="63c9a-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="63c9a-127">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="63c9a-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
