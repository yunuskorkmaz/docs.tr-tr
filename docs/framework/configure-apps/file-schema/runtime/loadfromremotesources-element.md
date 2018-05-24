---
title: '&lt;loadFromRemoteSources&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acd66cdff9f2c68e7d665b1fd236b18eeb9b4bac
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt; öğesi
Uzak kaynaklardan derlemeler tam güven verilip verilmeyeceğini belirtir.  
  
> [!NOTE]
>  Hata iletisinde Visual Studio Proje hata listesi veya bir derleme hatası nedeniyle bu konuya yönelik olup [nasıl yapılır: Visual Studio'da Web bir derleme kullanma](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<loadFromRemoteSources >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Uzak kaynaktan yüklenen bir derlemeyi tam güven verilip verilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Tam güven uzak kaynaklardan gelen uygulamalara vermeyin. Bu varsayılandır.|  
|`true`|Tam güven uzak kaynaklardan gelen uygulamalara verin.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uzak bir konumdan bir derlemeyi yüklenen .NET Framework sürüm 3.5 ve önceki sürümlerinde derleme kısmen güvenilen yüklü değildi bölgenin bağlı verme kümesi ile çalışır. Örneğin, bir Web sitesinden bir derlemeyi yüklerse Internet bölgeye yüklendi ve Internet izin kümesi verildi. Diğer bir deyişle, bir Internet korumalı alanda yürütülür. Bu derleme çalıştırmayı denerseniz [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve sonraki sürümlerinde, bir özel durum; bir korumalı alan açıkça derleme için oluşturmalısınız (bkz [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), ya da tam güvende çalıştırma.  
  
 `<loadFromRemoteSources>` Belirtmenizi .NET Framework'ün kısmen güvenilen olarak önceki sürümlerinde çalışır derlemeler tam olarak çalıştırılacak olan öğesi sağlar güvenilen [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve sonraki sürümler. Varsayılan olarak, uzaktan derlemeleri çalıştırmayın [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra. Uzak bir derleme çalıştırmak için ya da tam olarak güvenilir olarak çalıştırmak veya bir korumalı oluşturmanız gerekir <xref:System.AppDomain> çalıştırmak için.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], yerel ağ paylaşımlarında derlemeler, varsayılan tam güven çalıştırılır; etkinleştirmeniz gerekmez `<loadFromRemoteSources>` öğesi.  
  
> [!NOTE]
>  Bir uygulamanın web sunucusundan kopyalanan, yerel bilgisayarda bulunsa bile, Windows tarafından bir web uygulaması olacak şekilde işaretlenir. Dosya özelliklerini değiştirerek bu ataması değiştirebilir veya kullanabilirsiniz `<loadFromRemoteSources>` öğesi derleme vermek için tam güven. Alternatif olarak, kullandığınız <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> işletim sistemi Web'den yüklenen olarak işaretlenmiş yerel bir derlemeyi yüklemeye yöntemi.  
  
 `enabled` Yalnızca kod erişim güvenliği (CAS) devre dışı bırakıldığında bu öğe etkilidir için öznitelik. Varsayılan olarak, CAS ilkesini devre dışı durumda [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve sonraki sürümler. Ayarlarsanız `enabled` için `true`, uzak uygulamalarını tam güven verilmiştir.  
  
 Varsa `<loadFromRemoteSources>` `enabled` ayarlanmazsa `true`, aşağıdaki koşullar altında bir özel durum:  
  
-   Korumalı alan geçerli etki alanının içinde davranışını öğesinden farklı bir davranıştır [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]. Bu, CA ilke devre dışı bırakılması ve korumalı olmaması için geçerli etki alanı gerektirir.  
  
-   Yüklenmekte olan derleme gelen değil `MyComputer` bölgesi.  
  
> [!NOTE]
>  Alabilirsiniz bir <xref:System.IO.FileLoadException> bağlantılı klasörlerden barındıran bilgisayarda bir dosyayı yüklemeye çalıştığınızda Windows Virtual PC uygulamasında. Bir dosya üzerinden bağlı bir klasörden yüklemeye çalıştığınızda bu hatayı da oluşabilir [Uzak Masaüstü Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Hizmetleri). Özel durum önlemek için ayarlandığından `enabled` için `true`.  
  
 Ayarı `<loadFromRemoteSources>` öğesine `true` bu özel durumlar gelen engeller. Ortak dil çalışma zamanı için korumalı alan güvenlik için yüklenen derlemeleri güvenmek değil, belirtmenize olanak sağlar ve bunlar olarak yürütün olmasına izin verilmesi gerektiğini tam güven.  
  
> [!IMPORTANT]
>  Derleme tam güvende çalıştırmamanız gerekir, bu yapılandırma öğesi ayarlı değil. Bunun yerine, bir korumalı oluşturun <xref:System.AppDomain> , derlemesi yüklenemedi.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe uygulama yapılandırma dosyasında genellikle kullanılır, ancak bağlam bağlı olarak diğer yapılandırma dosyalarını, kullanılabilir. Daha fazla bilgi için bkz: [daha fazla örtük kullanan CA ilke: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) .NET güvenlik günlüğündeki.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek uygulamaları için tam güven uzak kaynaktan nasıl gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CA ilke daha örtük kullanır: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [Nasıl yapılır: korumalı alanda kısmen güvenilen kodu çalıştırma](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
