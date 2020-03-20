---
title: 'Nasıl yapılır: Uygulama için Varsayılan Saat Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 0aaa26f67ef1ef191060e682690fa14de328b812
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048101"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="a3cec-102">Nasıl yapılır: Uygulama için Varsayılan Saat Temelli Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a3cec-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="a3cec-103">Varsayılan zaman tabanlı önbellek ilkesi, önbelleğe alınmış kaynakla önbelleğe alınmış kaynak ve [Internet Engineering Task Force (IETF)](https://www.ietf.org/) web sitesinde bulunan RFC 2616'nın 13 ve 14 bölümlerinde tanımlanan önbellek davranışıyla bir uygulamanın önbellek davranışıtarafından tanımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3cec-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="a3cec-104">Bu, çoğu uygulama için uygun önbellek davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="a3cec-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="a3cec-105">Bir uygulama için varsayılan otomatik ilkeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a3cec-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="a3cec-106">Varsayılan zaman tabanlı ilke nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3cec-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="a3cec-107">İlke nesnesini uygulama etki alanı için varsayılan olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a3cec-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3cec-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3cec-108">Example</span></span>  
 <span data-ttu-id="a3cec-109">Bu bölümdeki iki örnek aynı ilkeleri üretir.</span><span class="sxs-lookup"><span data-stu-id="a3cec-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="a3cec-110">Aşağıdaki örnekte varsayılan zaman tabanlı bir ilke oluşturulur ve uygulama etki alanı için varsayılan olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a3cec-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 <span data-ttu-id="a3cec-111">Aşağıdaki örnekte gösterildiği gibi <xref:System.Net.Cache.RequestCachePolicy> sınıfı kullanarak varsayılan zaman tabanlı önbellek ilkesini de oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a3cec-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3cec-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3cec-112">See also</span></span>

- [<span data-ttu-id="a3cec-113">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="a3cec-113">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="a3cec-114">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="a3cec-114">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="a3cec-115">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="a3cec-115">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="a3cec-116">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="a3cec-116">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="a3cec-117">\<requestCaching> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a3cec-117">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
