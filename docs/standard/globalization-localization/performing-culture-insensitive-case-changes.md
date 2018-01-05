---
title: "Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e65eb85e1355d3aa98e04e7bd73f0194243dcdb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="59b18-102">Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="59b18-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="59b18-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, Ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> herhangi bir parametre kabul ediyor musunuz aşırı yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b18-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="59b18-104">Varsayılan olarak, bu aşırı parametresiz değerine göre durum değişiklikleri gerçekleştirmek <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59b18-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="59b18-105">Kültür göre değişebilir büyük küçük harfe duyarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="59b18-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="59b18-106">Clear kültüre duyarlı veya kültüre duyarsız büyük/küçük değişikliklerini istediğinizi yapmak için açıkça belirtmek ihtiyaç duyduğunuz bu yöntemlerin aşırı kullanmalısınız bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="59b18-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="59b18-107">Kültüre duyarlı durum değişiklikleri belirtin `CultureInfo.CurrentCulture` için `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="59b18-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="59b18-108">Kültüre duyarsız büyük/küçük değişikliklerini belirtin `CultureInfo.InvariantCulture` için `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="59b18-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="59b18-109">Genellikle, dizeleri daha sonra daha kolay aramasını etkinleştirmek için standart talebine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="59b18-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="59b18-110">Dizeleri bu şekilde kullanıldığında belirtmeniz gerekir `CultureInfo.InvariantCulture` için `culture` parametresi, çünkü değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> durumu değişti zaman ve arama oluşur saat arasında potansiyel olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59b18-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="59b18-111">Güvenlik kararı bir büyük/küçük harf değiştirme işlemi temel alıyorsa, işlemi kültüre sonuç değeri olarak etkilenmediğinden emin olmak için duyarsız olmalıdır `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="59b18-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="59b18-112">"Dize karşılaştırmaları kullanma geçerli kültür" bölümüne bakın [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md) nasıl kültüre duyarlı dize işlemleri gösteren bir örnek tutarsız sonuçlara yol açabilir için makalesi.</span><span class="sxs-lookup"><span data-stu-id="59b18-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="59b18-113">String.ToUpper ve String.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="59b18-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="59b18-114">Kodu daha anlaşılır olması için her zaman aşırı kullanmanız önerilir `String.ToUpper` ve `String.ToLower` belirtmenize olanak veren yöntemler bir `culture` parametre açıkça.</span><span class="sxs-lookup"><span data-stu-id="59b18-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="59b18-115">Örneğin, aşağıdaki kod bir tanımlayıcı araması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="59b18-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="59b18-116">`key.ToLower` İşlemi kültüre duyarlı varsayılan, ancak bu davranış kodu okuma açık değil.</span><span class="sxs-lookup"><span data-stu-id="59b18-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="59b18-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="59b18-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="59b18-118">İstiyorsanız, `key.ToLower` kültüre duyarsız, olmasını işlemi aşağıdaki gibi açıkça kullanmak için önceki örnekte değiştirmelisiniz `CultureInfo.InvariantCulture` durum değiştirirken.</span><span class="sxs-lookup"><span data-stu-id="59b18-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="59b18-119">Char.ToUpper ve Char.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="59b18-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="59b18-120">Ancak `Char.ToUpper` ve `Char.ToLower` yöntemleri aynı özelliklere sahip `String.ToUpper` ve `String.ToLower` yöntemleri, etkilenen yalnızca kültürler: Türkçe (Türkiye) ve Azerice (Latin, Azerbaycan).</span><span class="sxs-lookup"><span data-stu-id="59b18-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="59b18-121">Yalnızca iki kültürler tek-büyük farklılıklar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="59b18-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="59b18-122">Bu benzersiz servis talebi eşleştirme hakkında daha fazla ayrıntı için "Büyük" bölümüne bakın <xref:System.String> sınıfı konu.</span><span class="sxs-lookup"><span data-stu-id="59b18-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="59b18-123">Kodu daha anlaşılır olması ve tutarlı sonuçlar alınması aşırı açıkça belirtmenize olanak veren bu yöntemlerin her zaman kullanmanız önerilir bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="59b18-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b18-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59b18-124">See Also</span></span>  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="59b18-125">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="59b18-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
