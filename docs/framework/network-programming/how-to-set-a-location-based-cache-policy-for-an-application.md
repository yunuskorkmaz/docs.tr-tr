---
title: "Nasıl yapılır: bir uygulama için bir konum temelli önbellek İlkesi ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9d54a34b5d7cf40a6eaa9d777b9b05a1be34f177
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Nasıl yapılır: bir uygulama için bir konum temelli önbellek İlkesi ayarlama
Konum temelli önbellek ilkeleri açıkça istenen kaynak konumunu temelinde önbelleğe alma davranışını tanımlamak bir uygulama sağlar. Bu konuda, önbellek ilkesini programlı olarak ayarlama gösterilir. Yapılandırma dosyalarını kullanarak bir uygulama için ilke ayarlama hakkında daha fazla bilgi için bkz: [ \<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Bir uygulama için bir konum temelli önbellek ilkesini ayarlamak için  
  
1.  Oluşturma bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi.  
  
2.  Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>İstenen kaynaklar bir önbellekten alır ilkesini ayarlamak için  
  
-   İstenen kaynaklar kullanılabiliyorsa bir önbellekten alır ve aksi durumda, önbelleği düzeyini ayarlayarak istekleri sunucuya gönderir bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>. Uzak önbellekleri da dahil, sunucu ve istemci arasındaki tüm önbelleği tarafından bir istek yerine getirilmesi.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Kaynak sağlama tüm önbellek önleyen bir ilke ayarlamak için  
  
-   Önbelleği düzeyini ayarlayarak istenen kaynaklar sağladığını herhangi önbellek engelleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>. Bu ilke düzeyi varsa ve bunlar da kaynak kaldırmalısınız uzak önbellekleri gösterir kaynak yerel önbellekten kaldırır.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>İstenen kaynaklar yalnızca yerel önbellekte varsa döndüren bir ilkesini ayarlamak için  
  
-   İstenen kaynaklar yalnızca yerel önbellekteki önbelleği düzeyini ayarlayarak olmaları durumunda döndüren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>. İstenen kaynak önbelleğinde değilse, bir <xref:System.Net.WebException> özel durumu oluşur.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Yerel önbelleğe kaynakları sağladığını önleyen bir ilke ayarlamak için  
  
-   Önbelleği düzeyini ayarlayarak istenen kaynaklar sağladığını yerel önbelleği engelleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. İstenen kaynak Ara cache içinde olduğundan ve başarıyla yeniden doğrulanır, Ara önbelleği istenen kaynak sağlayabilirsiniz.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>İstenen kaynakları sağladığını gelen tüm önbellek önleyen bir ilke ayarlayın  
  
-   Önbelleği düzeyini ayarlayarak istenen kaynaklar sağladığını herhangi önbellek engelleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>. Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Kaynak sunucuda önbelleğe alınmış kopyadan yeni değilse, istenen kaynak sağlamak bir önbellek izin veren bir İlkesi ayarlamak için  
  
-   Kaynak sunucuda önbelleği düzeyini ayarlayarak önbelleğe alınmış kopyadan yeni değilse, istenen kaynak sağlamak tüm önbellek izin veren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
