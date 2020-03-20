---
title: 'Nasıl yapılır: İstek için Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- request cache policies
ms.assetid: 39c15e40-586b-4ac9-9cce-146f74b7e545
ms.openlocfilehash: 4ad74d69391da0e815faf9c278f2d9bea03937d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180759"
---
# <a name="how-to-set-cache-policy-for-a-request"></a><span data-ttu-id="f4bca-102">Nasıl yapılır: İstek için Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f4bca-102">How to: Set Cache Policy for a Request</span></span>
<span data-ttu-id="f4bca-103">Aşağıdaki örnek, bir istek için önbellek ilkesi ayarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4bca-103">The following example demonstrates setting a cache policy for a request.</span></span> <span data-ttu-id="f4bca-104">Örnek giriş gibi bir URI `http://www.contoso.com/`olduğunu.</span><span class="sxs-lookup"><span data-stu-id="f4bca-104">The example input is a URI such as `http://www.contoso.com/`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4bca-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4bca-105">Example</span></span>  
 <span data-ttu-id="f4bca-106">Aşağıdaki kod örneği, önbellekte bir günden uzun süre yoksa istenen kaynağın önbellekten kullanılmasına izin veren bir önbellek ilkesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4bca-106">The following code example creates a cache policy that allows the requested resource to be used from the cache if it has not been in the cache for longer than one day.</span></span> <span data-ttu-id="f4bca-107">Örnekte, kaynağın önbellekten `"The response was retrieved from the cache : False."`kullanılıp kullanılmadığını belirten bir ileti görüntülenir ve sonra kaynağı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f4bca-107">The example displays a message that indicates whether the resource was used from the cache—for example, `"The response was retrieved from the cache : False."`—and then displays the resource.</span></span> <span data-ttu-id="f4bca-108">İstek istemci ve sunucu arasındaki herhangi bir önbellek tarafından yerine getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f4bca-108">A request can be fulfilled by any cache between the client and server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4bca-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4bca-109">See also</span></span>

- [<span data-ttu-id="f4bca-110">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="f4bca-110">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="f4bca-111">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="f4bca-111">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="f4bca-112">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="f4bca-112">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="f4bca-113">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="f4bca-113">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="f4bca-114">\<requestCaching> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="f4bca-114">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
