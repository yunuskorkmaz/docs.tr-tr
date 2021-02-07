---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir uygulama için varsayılan Time-Based önbellek Ilkesini ayarlama'
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
ms.openlocfilehash: 1ca9504d8a6df20d3824230d5fb96eb0f13636eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662773"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="10ab5-103">Nasıl yapılır: Uygulama için Varsayılan Saat Temelli Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="10ab5-103">How to: Set the Default Time-Based Cache Policy for an Application</span></span>

<span data-ttu-id="10ab5-104">Varsayılan zaman tabanlı önbellek ilkesi, bir uygulamanın önbelleğe alınmış kaynakla gönderilen üstbilgiler ve [Internet Mühendisliği görev zorlaması (IETF)](https://www.ietf.org/) Web sitesinde kullanılabilir olan 2616 13. bölümlerde tanımlanan önbellek davranışı ile tanımlanan önbellek davranışını kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="10ab5-104">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="10ab5-105">Bu, çoğu uygulama için uygun önbellek davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="10ab5-105">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="10ab5-106">Bir uygulamanın varsayılan otomatik ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="10ab5-106">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="10ab5-107">Varsayılan bir zamana dayalı ilke nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10ab5-107">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="10ab5-108">İlke nesnesini, uygulama etki alanı için varsayılan olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="10ab5-108">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ab5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="10ab5-109">Example</span></span>  

 <span data-ttu-id="10ab5-110">Bu bölümdeki iki örnek özdeş ilkeler üretir.</span><span class="sxs-lookup"><span data-stu-id="10ab5-110">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="10ab5-111">Aşağıdaki örnek, varsayılan bir zamana dayalı ilke oluşturur ve bunu uygulama etki alanı için varsayılan olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="10ab5-111">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="10ab5-112">Aşağıdaki örnekte gösterildiği gibi sınıfını kullanarak varsayılan zaman tabanlı önbellek ilkesi de oluşturabilirsiniz <xref:System.Net.Cache.RequestCachePolicy> :</span><span class="sxs-lookup"><span data-stu-id="10ab5-112">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10ab5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10ab5-113">See also</span></span>

- [<span data-ttu-id="10ab5-114">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="10ab5-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="10ab5-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="10ab5-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="10ab5-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="10ab5-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="10ab5-117">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="10ab5-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="10ab5-118">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="10ab5-118">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
