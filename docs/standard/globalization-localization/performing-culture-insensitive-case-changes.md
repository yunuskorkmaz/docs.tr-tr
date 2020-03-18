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
ms.openlocfilehash: 7b2dee03619e24c5a2845699a06e88abab0c594b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160137"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="2298d-102">Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="2298d-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="2298d-103">, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemler herhangi bir parametre kabul etmez aşırı yükleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2298d-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="2298d-104">Varsayılan olarak, parametreleri olmayan bu aşırı yükler, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>'nin değerini temel alan büyük/küçük harf değişiklikleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2298d-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2298d-105">Bu, kültüre göre değişebilen büyük/küçük harf duyarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="2298d-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="2298d-106">Büyük/küçük harf değişikliklerinin kültüre duyarlı mı yoksa kültüre duyarlı mı olmasını istediğinizi açıklığa kavuşturmak için, `culture` bir parametreyi açıkça belirtmenizi gerektiren bu yöntemlerin aşırı yüklerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2298d-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="2298d-107">Kültüre duyarlı servis talebi `CultureInfo.CurrentCulture` değişiklikleri `culture` için parametreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="2298d-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="2298d-108">Kültüre duyarlı örnek değişiklikler `CultureInfo.InvariantCulture` için `culture` parametreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="2298d-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="2298d-109">Genellikle, dizeleri daha sonra daha kolay arama sağlamak için standart bir servis talebi dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="2298d-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="2298d-110">Dizeleri bu şekilde kullanıldığında, `CultureInfo.InvariantCulture` `culture` parametre için belirtmeniz gerekir, <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> çünkü değer büyük/küçük harfin değiştirilme süresi ile aramanın oluştuğu saat arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2298d-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="2298d-111">Bir güvenlik kararı bir servis talebi değiştirme işlemine dayanıyorsa, sonucun değerinden etkilenmediğinden emin `CultureInfo.CurrentCulture`olmak için işlem kültüre duyarsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2298d-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="2298d-112">Kültüre duyarlı dize işlemlerinin tutarsız sonuçlar üretebileceğini gösteren bir örnek için [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md) makalesinin "Geçerli Kültürü Kullanan Dize Karşılaştırmaları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2298d-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="2298d-113">String.ToUpper ve String.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="2298d-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="2298d-114">Kod netliği için, bir `String.ToUpper` `String.ToLower` `culture` parametreyi açıkça belirtmenize olanak tanıyan yöntemlerin ve yöntemlerin her zaman aşırı yüklerini kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="2298d-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="2298d-115">Örneğin, aşağıdaki kod tanımlayıcı bir arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2298d-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="2298d-116">İşlem `key.ToLower` varsayılan olarak kültüre duyarlıdır, ancak bu davranış kodu okumaktan net değildir.</span><span class="sxs-lookup"><span data-stu-id="2298d-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2298d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="2298d-117">Example</span></span>  
  
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
  
 <span data-ttu-id="2298d-118">İşlemin `key.ToLower` kültüre duyarsız olmasını istiyorsanız, servis talebi `CultureInfo.InvariantCulture` değiştirilirken aşağıdaki örneği açıkça kullanmak için aşağıdaki örneği değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2298d-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="2298d-119">Char.ToUpper ve Char.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="2298d-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="2298d-120">Metodlar `Char.ToUpper` `Char.ToLower` ve `String.ToLower` metotlar ile aynı özelliklere sahip olmakla birlikte, etkilenen kültürler sadece Türk (Türkiye) ve Azeri (Latince, Azerbaycan) 'dır. `String.ToUpper`</span><span class="sxs-lookup"><span data-stu-id="2298d-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="2298d-121">Bunlar tek karakterli kasa farklılıkları olan iki kültürdür.</span><span class="sxs-lookup"><span data-stu-id="2298d-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="2298d-122">Bu benzersiz servis talebi eşleme hakkında daha fazla bilgi <xref:System.String> için sınıf konusundaki "Kasa" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2298d-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="2298d-123">Kod netliği ve tutarlı sonuçlar sağlamak için, bir `culture` parametreyi açıkça belirtmenize olanak tanıyan bu yöntemlerin aşırı yüklerini her zaman kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="2298d-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2298d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2298d-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2298d-125">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="2298d-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
