---
title: Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b5289074724e3afd7356599738eeba648f25ca06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120842"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="c3a06-102">Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="c3a06-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="c3a06-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri herhangi bir parametreyi kabul etmediğinden aşırı yüklemeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3a06-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="c3a06-104">Varsayılan olarak, parametreleri olmayan bu aşırı yüklemeler <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>değerine göre değişiklik yapar.</span><span class="sxs-lookup"><span data-stu-id="c3a06-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c3a06-105">Bu, kültüre göre değişebilen büyük/küçük harfe duyarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="c3a06-106">Büyük/küçük harf duyarlı ya da kültüre duyarsız olmasını isteyip istemediğinizi net hale getirmek için, açıkça bir `culture` parametresi belirtmenizi gerektiren bu yöntemlerin aşırı yüklerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="c3a06-107">Kültüre duyarlı durum değişiklikleri için `culture` parametresi için `CultureInfo.CurrentCulture` belirtin.</span><span class="sxs-lookup"><span data-stu-id="c3a06-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="c3a06-108">Kültüre duyarsız büyük/küçük harf değişiklikleri için `culture` parametresi için `CultureInfo.InvariantCulture` belirtin.</span><span class="sxs-lookup"><span data-stu-id="c3a06-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="c3a06-109">Genellikle, dizeler daha sonra daha kolay arama sağlamak için standart bir büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c3a06-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="c3a06-110">Dizeler bu şekilde kullanıldığında `culture` parametresi için `CultureInfo.InvariantCulture` belirtmelisiniz, çünkü <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> değeri büyük olasılıkla durumun değiştiği zaman ve aramanın gerçekleştiği zaman arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="c3a06-111">Bir güvenlik kararı bir durum değişikliği işlemini temel alıyorsa, sonucun `CultureInfo.CurrentCulture`değerinden etkilenmemesini sağlamak için işlem kültüre duyarsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3a06-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="c3a06-112">Kültüre duyarlı dize işlemlerinin nasıl tutarsız sonuçlar üretediğini gösteren bir örnek için, [dizeler kullanmanın En Iyi yöntemleri](../../../docs/standard/base-types/best-practices-strings.md) olan "geçerli kültürü kullanan dize karşılaştırmaları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c3a06-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="c3a06-113">String.ToUpper ve String.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c3a06-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="c3a06-114">Kod netliği için, `String.ToUpper` ve `String.ToLower` yöntemlerinin her zaman açıkça bir `culture` parametresi belirtmenize olanak tanıyan aşırı yüklemeleri kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="c3a06-115">Örneğin, aşağıdaki kod bir tanımlayıcı araması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="c3a06-116">`key.ToLower` işlemi varsayılan olarak kültüre duyarlıdır, ancak bu davranışın kodu okumasından net değildir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c3a06-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3a06-117">Example</span></span>  
  
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
  
 <span data-ttu-id="c3a06-118">`key.ToLower` işleminin kültüre duyarsız olmasını istiyorsanız, bu durumu değiştirirken `CultureInfo.InvariantCulture` açıkça kullanmak için önceki örneği aşağıdaki şekilde değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c3a06-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="c3a06-119">Char.ToUpper ve Char.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c3a06-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="c3a06-120">`Char.ToUpper` ve `Char.ToLower` yöntemleri `String.ToUpper` ve `String.ToLower` yöntemleriyle aynı özelliklere sahip olsa da, etkilenen tek kültürler Türkçe (Türkiye) ve Azerbaycan dili (Latin, Azerbaycan).</span><span class="sxs-lookup"><span data-stu-id="c3a06-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="c3a06-121">Bunlar tek karakterli büyük/küçük harf farklılığı olan tek iki kültürde.</span><span class="sxs-lookup"><span data-stu-id="c3a06-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="c3a06-122">Bu benzersiz durum eşleştirmesi hakkında daha fazla ayrıntı için <xref:System.String> sınıfı konusunun "büyük küçük harf" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c3a06-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="c3a06-123">Kod netliği ve tutarlı sonuçlar sağlamak için, bu yöntemlerin her zaman açıkça bir `culture` parametresi belirtmenize olanak tanıyan aşırı yüklemeleri kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="c3a06-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a06-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3a06-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c3a06-125">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="c3a06-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
