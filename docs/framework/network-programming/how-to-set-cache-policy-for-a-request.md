---
title: 'Nasıl yapılır: İstek için Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- request cache policies
ms.assetid: 39c15e40-586b-4ac9-9cce-146f74b7e545
ms.openlocfilehash: 7b28cf6e27fa6f5a5d255621d8e21e9a565ddbc4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048111"
---
# <a name="how-to-set-cache-policy-for-a-request"></a><span data-ttu-id="296c8-102">Nasıl yapılır: İstek için Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="296c8-102">How to: Set Cache Policy for a Request</span></span>
<span data-ttu-id="296c8-103">Aşağıdaki örnek, bir istek için önbellek ilkesi ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="296c8-103">The following example demonstrates setting a cache policy for a request.</span></span> <span data-ttu-id="296c8-104">Örnek giriş, gibi bir URI `http://www.contoso.com/`'dir.</span><span class="sxs-lookup"><span data-stu-id="296c8-104">The example input is a URI such as `http://www.contoso.com/`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="296c8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="296c8-105">Example</span></span>  
 <span data-ttu-id="296c8-106">Aşağıdaki kod örneği, bir günden daha uzun süredir önbellekte olmayan istenen kaynağın önbellekten kullanılmasına izin veren bir önbellek ilkesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="296c8-106">The following code example creates a cache policy that allows the requested resource to be used from the cache if it has not been in the cache for longer than one day.</span></span> <span data-ttu-id="296c8-107">Örnek, kaynağın önbellekten kullanılıp kullanılmadığını belirten bir ileti görüntüler — Örneğin, `"The response was retrieved from the cache : False."`— ve ardından kaynağı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="296c8-107">The example displays a message that indicates whether the resource was used from the cache—for example, `"The response was retrieved from the cache : False."`—and then displays the resource.</span></span> <span data-ttu-id="296c8-108">İstek, istemci ve sunucu arasındaki herhangi bir önbellekte yerine getirilir.</span><span class="sxs-lookup"><span data-stu-id="296c8-108">A request can be fulfilled by any cache between the client and server.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Cache;  
using System.IO;  
  
namespace Examples.System.Net.Cache  
{  
    public class CacheExample  
    {     
        public static void UseCacheForOneDay(Uri resource)  
        {  
            // Create a policy that allows items in the cache  
            // to be used if they have been cached one day or less.  
            HttpRequestCachePolicy requestPolicy =   
                new HttpRequestCachePolicy (HttpCacheAgeControl.MaxAge,  
                TimeSpan.FromDays(1));  
  
            WebRequest request = WebRequest.Create (resource);  
            // Set the policy for this request only.  
            request.CachePolicy = requestPolicy;  
            HttpWebResponse response = (HttpWebResponse)request.GetResponse();  
            // Determine whether the response was retrieved from the cache.  
            Console.WriteLine ("The response was retrieved from the cache : {0}.",  
               response.IsFromCache);  
            Stream s = response.GetResponseStream ();  
            StreamReader reader = new StreamReader (s);  
            // Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd());  
            reader.Close ();  
            s.Close();  
            response.Close();  
        }  
        public static void Main(string[] args)  
        {  
            if (args == null || args.Length != 1)  
            {  
                Console.WriteLine ("You must specify the URI to retrieve.");  
                return;  
            }  
            UseCacheForOneDay (new Uri(args[0]));  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Cache  
Imports System.IO  
Namespace Examples.System.Net.Cache  
    Public Class CacheExample  
        Public Shared Sub UseCacheForOneDay(ByVal resource As Uri)  
            ' Create a policy that allows items in the cache  
            ' to be used if they have been cached one day or less.  
            Dim requestPolicy As New HttpRequestCachePolicy _  
                  (HttpCacheAgeControl.MaxAge, TimeSpan.FromDays(1))  
            Dim request As WebRequest = WebRequest.Create(resource)  
            ' Set the policy for this request only.  
            request.CachePolicy = requestPolicy  
            Dim response As HttpWebResponse = _  
             CType(request.GetResponse(), HttpWebResponse)  
            ' Determine whether the response was retrieved from the cache.  
            Console.WriteLine("The response was retrieved from the cache : {0}.", _  
                response.IsFromCache)  
            Dim s As Stream = response.GetResponseStream()  
            Dim reader As New StreamReader(s)  
            ' Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd())  
            reader.Close()  
            s.Close()  
            response.Close()  
        End Sub  
        Public Shared Sub Main(ByVal args() As String)  
            If args Is Nothing OrElse args.Length <> 1 Then  
                Console.WriteLine("You must specify the URI to retrieve.")  
                Return  
            End If  
            UseCacheForOneDay(New Uri(args(0)))  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="296c8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="296c8-109">See also</span></span>

- [<span data-ttu-id="296c8-110">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="296c8-110">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="296c8-111">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="296c8-111">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="296c8-112">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="296c8-112">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="296c8-113">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="296c8-113">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="296c8-114">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="296c8-114">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
