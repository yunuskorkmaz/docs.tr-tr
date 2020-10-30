---
title: Kültüre Duyarsız Dize İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET], culture-insensitive string operations
- strings [.NET], culture-insensitive string operations
- localization [.NET], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 3a6085d15dbaa30144436b163a6ecb777698f4f1
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064008"
---
# <a name="culture-insensitive-string-operations"></a><span data-ttu-id="77c7a-102">Kültüre duyarsız dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="77c7a-102">Culture-insensitive string operations</span></span>

<span data-ttu-id="77c7a-103">Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir.</span><span class="sxs-lookup"><span data-stu-id="77c7a-103">Culture-sensitive string operations can be an advantage if you are creating applications designed to display results to users on a per-culture basis.</span></span> <span data-ttu-id="77c7a-104">Varsayılan olarak, kültüre duyarlı yöntemler <xref:System.Globalization.CultureInfo.CurrentCulture%2A> geçerli iş parçacığının özelliğinden kullanılacak kültürü elde eder.</span><span class="sxs-lookup"><span data-stu-id="77c7a-104">By default, culture-sensitive methods obtain the culture to use from the <xref:System.Globalization.CultureInfo.CurrentCulture%2A> property for the current thread.</span></span>

<span data-ttu-id="77c7a-105">Bazen kültüre duyarlı dize işlemleri istenen davranış değildir.</span><span class="sxs-lookup"><span data-stu-id="77c7a-105">Sometimes, culture-sensitive string operations are not the desired behavior.</span></span> <span data-ttu-id="77c7a-106">Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="77c7a-106">Using culture-sensitive operations when results should be independent of culture can cause application code to fail on cultures with custom case mappings and sorting rules.</span></span> <span data-ttu-id="77c7a-107">Bir örnek için, [dizeler kullanmak Için En Iyi Yöntemler](../base-types/best-practices-strings.md) konusunun ["geçerli kültürü kullanan dize karşılaştırmaları"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="77c7a-107">For an example, see the ["String Comparisons that Use the Current Culture"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) section in the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article.</span></span>

<span data-ttu-id="77c7a-108">Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="77c7a-108">Whether string operations should be culture-sensitive or culture-insensitive depends on how your application uses the results.</span></span> <span data-ttu-id="77c7a-109">Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77c7a-109">String operations that display results to the user should typically be culture-sensitive.</span></span> <span data-ttu-id="77c7a-110">Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="77c7a-110">For example, if an application displays a sorted list of localized strings in a list box, the application should perform a culture-sensitive sort.</span></span>

<span data-ttu-id="77c7a-111">Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77c7a-111">Results of string operations that are used internally should typically be culture-insensitive.</span></span> <span data-ttu-id="77c7a-112">Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="77c7a-112">In general, if the application is working with file names, persistence formats, or symbolic information that is not displayed to the user, results of string operations should not vary by culture.</span></span> <span data-ttu-id="77c7a-113">Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="77c7a-113">For example, if an application compares a string to determine whether it is a recognized XML tag, the comparison should not be culture-sensitive.</span></span> <span data-ttu-id="77c7a-114">Buna ek olarak, bir güvenlik kararı bir dize karşılaştırma veya örnek değişikliği işleminin sonucunu temel alıyorsa, sonucun değerinden etkilenmemesini sağlamak için işlem kültür duyarsız olmalıdır <xref:System.Globalization.CultureInfo.CurrentCulture%2A> .</span><span class="sxs-lookup"><span data-stu-id="77c7a-114">In addition, if a security decision is based on the result of a string comparison or case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span></span>

<span data-ttu-id="77c7a-115">Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştirirken, varsayılan olarak kültüre duyarlı sonuçları alan .NET yöntemlerinden haberdar olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="77c7a-115">Whether or not you're developing an application that includes code to handle localization and globalization issues, you should be aware of the .NET methods that retrieve culture-sensitive results by default.</span></span>

## <a name="see-also"></a><span data-ttu-id="77c7a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77c7a-116">See also</span></span>

- [<span data-ttu-id="77c7a-117">Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="77c7a-117">Globalization and Localization</span></span>](index.md)
