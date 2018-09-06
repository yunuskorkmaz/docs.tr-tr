---
title: Kültüre Duyarsız Dize İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1e1b476a1de1f0c348e264c9dc6b42ceb81eff
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869347"
---
# <a name="culture-insensitive-string-operations"></a><span data-ttu-id="ad0a2-102">Kültüre Duyarsız Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="ad0a2-102">Culture-Insensitive String Operations</span></span>
<span data-ttu-id="ad0a2-103">Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-103">Culture-sensitive string operations can be an advantage if you are creating applications designed to display results to users on a per-culture basis.</span></span> <span data-ttu-id="ad0a2-104">Varsayılan olarak, kültüre duyarlı yöntemler kültürü kullanmak için elde <xref:System.Globalization.CultureInfo.CurrentCulture%2A> özelliği için geçerli iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-104">By default, culture-sensitive methods obtain the culture to use from the <xref:System.Globalization.CultureInfo.CurrentCulture%2A> property for the current thread.</span></span>  
  
 <span data-ttu-id="ad0a2-105">Kültüre duyarlı dize işlemlerinin her zaman istenen davranış olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-105">Note that culture-sensitive string operations are not always the desired behavior.</span></span> <span data-ttu-id="ad0a2-106">Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-106">Using culture-sensitive operations when results should be independent of culture can cause application code to fail on cultures with custom case mappings and sorting rules.</span></span> <span data-ttu-id="ad0a2-107">Örneğin, "Dize karşılaştırmaları geçerli kültürü kullanan" bölümüne bakın. [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-107">For an example, see the "String Comparisons that Use the Current Culture" section in the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article.</span></span>  
  
 <span data-ttu-id="ad0a2-108">Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-108">Whether string operations should be culture-sensitive or culture-insensitive depends on how your application uses the results.</span></span> <span data-ttu-id="ad0a2-109">Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-109">String operations that display results to the user should typically be culture-sensitive.</span></span> <span data-ttu-id="ad0a2-110">Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-110">For example, if an application displays a sorted list of localized strings in a list box, the application should perform a culture-sensitive sort.</span></span>  
  
 <span data-ttu-id="ad0a2-111">Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-111">Results of string operations that are used internally should typically be culture-insensitive.</span></span> <span data-ttu-id="ad0a2-112">Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-112">In general, if the application is working with file names, persistence formats, or symbolic information that is not displayed to the user, results of string operations should not vary by culture.</span></span> <span data-ttu-id="ad0a2-113">Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-113">For example, if an application compares a string to determine whether it is a recognized XML tag, the comparison should not be culture-sensitive.</span></span> <span data-ttu-id="ad0a2-114">Bir güvenlik kararı bir dize karşılaştırma veya harf değiştirme işlemi sonuçlarına alıyorsa, ayrıca, işlemi kültür-sonucu değerinden etkilenmemesini sağlamak için duyarlı olmalıdır <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-114">In addition, if a security decision is based on the result of a string comparison or case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span></span>  
  
 <span data-ttu-id="ad0a2-115">Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştiriyor olsanız da olmasanız da, varsayılan olarak kültüre duyarlı sonuçlar getiren .NET Framework yöntemlerinden haberdar olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-115">Whether or not you are developing an application that includes code to handle localization and globalization issues, you should be aware of the .NET Framework methods that retrieve culture-sensitive results by default.</span></span> <span data-ttu-id="ad0a2-116">Bu konunun amacı kültüre duyarlı olmayan sonuçlar elde etmek üzere uygulamalarınızın bu yöntemleri kullanmasının doğru yolunu göstermektir.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-116">The purpose of this topic is to illustrate the correct way for your applications to use these methods to obtain culture-insensitive results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0a2-117">See also</span></span>

- [<span data-ttu-id="ad0a2-118">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="ad0a2-118">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
