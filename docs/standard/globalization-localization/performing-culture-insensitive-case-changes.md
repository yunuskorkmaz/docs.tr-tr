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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04601ac0e6b1bc3289be36ce3e1a144ce57ccefb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683047"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="e156f-102">Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="e156f-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="e156f-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, Ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri herhangi bir parametre kabul eden aşırı yükler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e156f-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="e156f-104">Varsayılan olarak, bu aşırı yüklemeler parametresiz değerine göre servis talebi değişiklikleri gerçekleştirmek <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e156f-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e156f-105">Bu, kültüre göre değişebilen büyük küçük harfe duyarlı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="e156f-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="e156f-106">Temizleyin, kültüre duyarlı veya kültüre duyarsız büyük/küçük harf değişikliklerini isteyip istemediğinizi hale getirmek için açıkça belirtmek ihtiyaç duyduğunuz bu yöntemleri aşırı kullanmalısınız bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e156f-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="e156f-107">Kültüre duyarlı büyük/küçük harf değişikliklerini belirtin `CultureInfo.CurrentCulture` için `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e156f-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="e156f-108">Kültüre duyarsız büyük/küçük harf değişikliklerini belirtin `CultureInfo.InvariantCulture` için `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e156f-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="e156f-109">Genellikle, dizeleri daha kolay aramasını daha sonra etkinleştirmek için bir standart küçük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e156f-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="e156f-110">Dizeleri bu şekilde kullanıldığında belirtmeniz gerekir `CultureInfo.InvariantCulture` için `culture` parametresi, çünkü değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> durumu değişti zaman arasında arama gerçekleşen zaman değiştirebilir miyim.</span><span class="sxs-lookup"><span data-stu-id="e156f-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="e156f-111">Bir güvenlik kararı bir büyük/küçük harf değiştirme işlemi alıyorsa, işlemi kültüre sonucu değerinden etkilenmemesini sağlamak için duyarlı olmalıdır `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="e156f-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="e156f-112">"Dize karşılaştırmaları geçerli kültürü kullanan" bölümüne bakın [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md) kültüre duyarlı dize işlemleri gösteren bir örnek tutarsız sonuçlar üretebileceğini için makalesi.</span><span class="sxs-lookup"><span data-stu-id="e156f-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="e156f-113">String.ToUpper ve String.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e156f-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="e156f-114">Kod netliği için her zaman aşırı yüklemesini kullanmanız önerilir `String.ToUpper` ve `String.ToLower` belirtmenize olanak tanıyan yöntemler bir `culture` parametre açıkça.</span><span class="sxs-lookup"><span data-stu-id="e156f-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="e156f-115">Örneğin, aşağıdaki kod, bir tanımlayıcı arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e156f-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="e156f-116">`key.ToLower` İşlem varsayılan, ancak bu davranış kültüre duyarlı kod okumasını açık değil.</span><span class="sxs-lookup"><span data-stu-id="e156f-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e156f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e156f-117">Example</span></span>  
  
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
  
 <span data-ttu-id="e156f-118">İsterseniz `key.ToLower` işlemin kültüre duyarsız, olması için önceki örnekte açıkça kullanacak şekilde değiştirmelisiniz `CultureInfo.InvariantCulture` durum değiştirirken.</span><span class="sxs-lookup"><span data-stu-id="e156f-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="e156f-119">Char.ToUpper ve Char.ToLower Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e156f-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="e156f-120">Ancak `Char.ToUpper` ve `Char.ToLower` yöntemleri aynı özelliklere sahip `String.ToUpper` ve `String.ToLower` yöntemleri, etkilenen tek bir kültür Türkçe (Türkiye) ve Azerice (Latin, Azerbaycan) verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e156f-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="e156f-121">Bu, yalnızca iki kültürler tek karakterli büyük/küçük harf farkları vardır.</span><span class="sxs-lookup"><span data-stu-id="e156f-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="e156f-122">Bu benzersiz büyük/küçük harf eşleştirme hakkında daha fazla ayrıntı için "Büyük/küçük harf" bölümüne bakın. <xref:System.String> sınıf konusuna.</span><span class="sxs-lookup"><span data-stu-id="e156f-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="e156f-123">Kod netliği ve tutarlı sonuçlar alınması için her zaman bu yöntemlerin açıkça belirtmenize olanak tanıyan aşırı kullanmanız önerilir bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e156f-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e156f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e156f-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e156f-125">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="e156f-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
