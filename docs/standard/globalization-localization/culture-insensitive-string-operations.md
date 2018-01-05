---
title: "Kültüre Duyarsız Dize İşlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 697d3ec32af6b704fbb1787bbb9ba1de57a0632e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="culture-insensitive-string-operations"></a><span data-ttu-id="0926b-102">Kültüre Duyarsız Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="0926b-102">Culture-Insensitive String Operations</span></span>
<span data-ttu-id="0926b-103">Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir.</span><span class="sxs-lookup"><span data-stu-id="0926b-103">Culture-sensitive string operations can be an advantage if you are creating applications designed to display results to users on a per-culture basis.</span></span> <span data-ttu-id="0926b-104">Varsayılan olarak, aşağıdakiler arasından kullanılacak kültürü kültüre duyarlı yöntemleri elde <xref:System.Globalization.CultureInfo.CurrentCulture%2A> özelliği için geçerli iş parçacığının.</span><span class="sxs-lookup"><span data-stu-id="0926b-104">By default, culture-sensitive methods obtain the culture to use from the <xref:System.Globalization.CultureInfo.CurrentCulture%2A> property for the current thread.</span></span>  
  
 <span data-ttu-id="0926b-105">Kültüre duyarlı dize işlemlerinin her zaman istenen davranış olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0926b-105">Note that culture-sensitive string operations are not always the desired behavior.</span></span> <span data-ttu-id="0926b-106">Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="0926b-106">Using culture-sensitive operations when results should be independent of culture can cause application code to fail on cultures with custom case mappings and sorting rules.</span></span> <span data-ttu-id="0926b-107">Örneğin, "Dize karşılaştırmaları kullanma geçerli kültür" bölümüne bakın [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="0926b-107">For an example, see the "String Comparisons that Use the Current Culture" section in the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article.</span></span>  
  
 <span data-ttu-id="0926b-108">Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0926b-108">Whether string operations should be culture-sensitive or culture-insensitive depends on how your application uses the results.</span></span> <span data-ttu-id="0926b-109">Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0926b-109">String operations that display results to the user should typically be culture-sensitive.</span></span> <span data-ttu-id="0926b-110">Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0926b-110">For example, if an application displays a sorted list of localized strings in a list box, the application should perform a culture-sensitive sort.</span></span>  
  
 <span data-ttu-id="0926b-111">Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0926b-111">Results of string operations that are used internally should typically be culture-insensitive.</span></span> <span data-ttu-id="0926b-112">Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="0926b-112">In general, if the application is working with file names, persistence formats, or symbolic information that is not displayed to the user, results of string operations should not vary by culture.</span></span> <span data-ttu-id="0926b-113">Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0926b-113">For example, if an application compares a string to determine whether it is a recognized XML tag, the comparison should not be culture-sensitive.</span></span> <span data-ttu-id="0926b-114">Dize karşılaştırma ya da durum değişiklik işlemi sonucu üzerinde bir güvenlik karar temel alıyorsa, ayrıca, işlemi kültüre sonuç değeri olarak etkilenmediğinden emin olmak için duyarsız olmalıdır <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span><span class="sxs-lookup"><span data-stu-id="0926b-114">In addition, if a security decision is based on the result of a string comparison or case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span></span>  
  
 <span data-ttu-id="0926b-115">Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştiriyor olsanız da olmasanız da, varsayılan olarak kültüre duyarlı sonuçlar getiren .NET Framework yöntemlerinden haberdar olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0926b-115">Whether or not you are developing an application that includes code to handle localization and globalization issues, you should be aware of the .NET Framework methods that retrieve culture-sensitive results by default.</span></span> <span data-ttu-id="0926b-116">Bu konunun amacı kültüre duyarlı olmayan sonuçlar elde etmek üzere uygulamalarınızın bu yöntemleri kullanmasının doğru yolunu göstermektir.</span><span class="sxs-lookup"><span data-stu-id="0926b-116">The purpose of this topic is to illustrate the correct way for your applications to use these methods to obtain culture-insensitive results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0926b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0926b-117">See Also</span></span>  
 [<span data-ttu-id="0926b-118">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="0926b-118">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
