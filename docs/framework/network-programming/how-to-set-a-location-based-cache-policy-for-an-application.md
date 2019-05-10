---
title: 'Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1bbbb558134e5f11537de0efef594be2b964cdcb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647380"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama
Konum temelli önbellek ilkeleri açıkça istenen kaynak konumunu temel alarak önbelleğe alma davranışını tanımlamak bir uygulama sağlar. Bu konuda önbellek ilkesini programlı olarak ayarlama gösterilir. Yapılandırma dosyalarını kullanarak bir uygulama için bir ilke ayarlama hakkında daha fazla bilgi için bkz. [ \<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Bir uygulama için bir konum temelli önbellek İlkesi ayarlama  
  
1. Oluşturma bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesne.  
  
2. Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Bir önbellekten istenen kaynaklara götüren bir ilke ayarlamak için  
  
- Bir önbellekten kullanılabilir durumdaysa istenen kaynakları alır ve aksi takdirde, önbelleği düzeyini ayarlayarak istekleri sunucuya gönderir, bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>. Bir istek istemci ve uzak önbellekler dahil sunucusu arasındaki tüm önbelleği tarafından getirilmesi.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Tüm önbelleği kaynakları sağlama dan engelleyen bir ilke ayarlamak için  
  
- Önbelleği düzeyini ayarlayarak istenen kaynaklara sağladığı tüm önbelleği önleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>. Varsa ve bunlar da kaynak kaldırmalısınız uzak önbelleklere gösterir. Bu ilke düzeyi kaynak yerel önbellekten kaldırır.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>İstenen kaynaklara yalnızca yerel önbellek üzerinde olduklarında döndüren bir ilke ayarlamak için  
  
- İstenen kaynaklara yalnızca yerel önbellek üzerinde önbelleği düzeyini ayarlayarak olmaları durumunda döndüren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>. İstenen kaynak önbellekte değilse bir <xref:System.Net.WebException> özel durumu oluşturulur.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Yerel önbellek kaynakları sağlama dan engelleyen bir ilke ayarlamak için  
  
- Yerel önbellek, önbellek düzeyini ayarlayarak istenen kaynaklara sağlama önleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. İstenen kaynak Ara bir önbellekte ve başarıyla yeniden doğrulanır, istenen kaynak Ara önbellek sağlayabilirsiniz.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Kaynaklar istenen tüm önbelleği sağlayarak dan engelleyen bir ilke ayarlama  
  
- Önbelleği düzeyini ayarlayarak istenen kaynaklara sağladığı tüm önbelleği önleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>. Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Kaynak sunucuda önbelleğe alınmış kopyayı yeni değil, istenen kaynakları sağlamak tüm önbelleği izin veren bir ilke ayarlamak için  
  
- Kaynak sunucuda önbelleği düzeyini ayarlayarak önbelleğe alınmış kopyayı yeni değil, istenen kaynakları sağlamak tüm önbelleği izin veren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
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

- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
