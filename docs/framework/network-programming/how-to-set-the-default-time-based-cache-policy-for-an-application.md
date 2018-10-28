---
title: 'Nasıl yapılır: uygulama için varsayılan saat temelli önbellek İlkesi ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: cdb93f802d313c0812bb50236ff5962c44251b4e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182924"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="24df0-102">Nasıl yapılır: uygulama için varsayılan saat temelli önbellek İlkesi ayarlama</span><span class="sxs-lookup"><span data-stu-id="24df0-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="24df0-103">Önbelleğe alınmış kaynak gönderilen üst bilgiler ve 13 ve RFC 2616, kullanılabilir 14 bölümlerde tanımlanan önbellek davranışı tarafından tanımlanan önbellek davranışı bir uygulamanın varsayılan saat temelli önbellek ilkesini sağlayan [Internet Engineering Task Force () IETF)](https://www.ietf.org/) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="24df0-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="24df0-104">Bu, çoğu uygulama için uygun önbellek davranıştır.</span><span class="sxs-lookup"><span data-stu-id="24df0-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="24df0-105">Bir uygulama için varsayılan otomatik İlkesi ayarlama</span><span class="sxs-lookup"><span data-stu-id="24df0-105">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="24df0-106">Varsayılan zaman tabanlı ilke nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24df0-106">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="24df0-107">Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="24df0-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24df0-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="24df0-108">Example</span></span>  
 <span data-ttu-id="24df0-109">Bu bölümdeki iki örneği aynı ilkeler üretir.</span><span class="sxs-lookup"><span data-stu-id="24df0-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="24df0-110">Aşağıdaki örnek, zamana bağlı bir varsayılan ilke oluşturur ve uygulama etki alanı için varsayılan olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24df0-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="24df0-111">Varsayılan saat temelli önbellek İlkesi kullanarak da oluşturabilirsiniz <xref:System.Net.Cache.RequestCachePolicy> aşağıdaki örnekte gösterildiği gibi sınıf:</span><span class="sxs-lookup"><span data-stu-id="24df0-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24df0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24df0-112">See Also</span></span>  
 [<span data-ttu-id="24df0-113">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="24df0-113">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="24df0-114">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="24df0-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="24df0-115">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="24df0-115">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="24df0-116">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="24df0-116">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="24df0-117">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="24df0-117">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
