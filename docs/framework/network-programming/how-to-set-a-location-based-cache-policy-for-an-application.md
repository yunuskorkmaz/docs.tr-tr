---
title: 'Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180775"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama
Konum tabanlı önbellek ilkeleri, bir uygulamanın istenen kaynağın konumuna bağlı olarak önbelleğe alma davranışını açıkça tanımlamasına olanak sağlar. Bu konu, önbellek ilkesini programlı bir şekilde ayarlamayı gösterir. Yapılandırma dosyalarını kullanarak bir uygulama nın ilkesini ayarlama hakkında bilgi için isteğe> [ \<Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)bakın.  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Bir uygulama için konum tabanlı önbellek ilkesi ayarlamak için  
  
1. Bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesne oluşturun.  
  
2. İlke nesnesini uygulama etki alanı için varsayılan olarak ayarlayın.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Önbellekten istenen kaynakları alan bir ilke ayarlamak için  
  
- Varsa önbellekten istenen kaynakları alan ve aksi takdirde önbellek düzeyini ayarlayarak istekleri sunucuya <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>gönderen bir ilke oluşturun. İstek, istemci ve sunucu arasındaki uzak önbellekler de dahil olmak üzere herhangi bir önbellek tarafından yerine getirilebilir.  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Önbelleğin kaynak sağlamasını engelleyen bir ilke ayarlamak için  
  
- Önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>'ye ayarlayarak herhangi bir önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke oluşturun Bu ilke düzeyi, varsa kaynağı yerel önbellekten kaldırır ve uzak önbelleğe almalarına da kaynak kaldırmaları gerektiğini gösterir.  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>İstenen kaynakları yalnızca yerel önbellekteyse döndüren bir ilke ayarlamak için  
  
- İstenen kaynakları yalnızca önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>'ne ayarlayarak yerel önbellekteyse döndüren bir ilke oluşturun İstenen kaynak önbellekte değilse, <xref:System.Net.WebException> bir özel durum atılır.  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Yerel önbelleğin kaynak sağlamasını engelleyen bir ilke ayarlamak için  
  
- Önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>'ye ayarlayarak yerel önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke oluşturun İstenen kaynak ara önbellekteyse ve başarıyla yeniden doğrulanırsa, ara önbellek istenen kaynağı sağlayabilir.  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Herhangi bir önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke ayarlamak için  
  
- Önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>'ye ayarlayarak herhangi bir önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke oluşturun Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Sunucudaki kaynak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına izin veren bir ilke ayarlamak için  
  
- Sunucudaki kaynak önbellek düzeyini ayarlayarak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>izin veren bir ilke oluşturun.  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
