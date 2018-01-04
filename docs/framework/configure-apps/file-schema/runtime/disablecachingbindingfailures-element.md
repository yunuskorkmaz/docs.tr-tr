---
title: "&lt;disableCachingBindingFailures&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd86bc2f58bc216f741c32a51925d3f4f8ef47df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disableCachingBindingFailures&gt; öğesi
Derleme yoklama tarafından bulunamadığından oluşan hataları bağlama önbelleğe alma devre dışı bırakılıp bırakılmayacağını belirtir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<disableCachingBindingFailures >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> Derleme yoklama tarafından bulunamadığından oluşan hataları bağlama önbelleğe alma devre dışı bırakılıp bırakılmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Derleme yoklama tarafından bulunamadığından oluşan hataları bağlama önbelleğe alma devre dışı bırakmayın. .NET Framework sürüm 2.0 ile başlayarak varsayılan bağlama davranışı budur.|  
|1.|Derleme yoklama tarafından bulunamadığından oluşan hataları bağlama önbelleğe alma devre dışı bırakın. Bu ayar, .NET Framework sürüm 1.1 bağlama davranışı döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2.0 ile başlayarak, tüm bağlama ve yükleme hatalarını önbelleğe almak için derlemeleri yükleme için varsayılan davranış şeklindedir. Diğer bir deyişle, bir derlemeyi yükleme denemesi başarısız olursa, aynı bütünleştirilmiş kodda yüklemek için sonraki istekleri hemen derleme bulmak için her türlü girişim başarısız. Bu öğe derleme algılama yolu bulunamadı çünkü oluşan hataları bağlama için bu varsayılan davranışı devre dışı bırakır. Bu hatalar throw <xref:System.IO.FileNotFoundException>.  
  
 Bazı bağlama ve hataları yüklenirken bu öğe etkilenmez ve her zaman önbelleğe alınır. Derleme bulundu ancak yüklenemedi çünkü bu hataları oluşuyor. Bunlar throw <xref:System.BadImageFormatException> veya <xref:System.IO.FileLoadException>. Aşağıdaki listede, bu tür hataları bazı örnekleri içerir.  
  
-   Yüklemeye çalışırsanız, bir dosya geçerli bir derleme değil, bozuk dosya doğru derleme ile değiştirilir olsa bile derlemeyi yüklemek için sonraki denemeler başarısız olur.  
  
-   Dosya sistemi tarafından kilitlenmiş bir derlemeyi yüklemeye çalışırsanız, derleme dosya sistemi tarafından bile yayımlandıktan sonra derlemeyi yüklemek için sonraki denemeleri başarısız olur.  
  
-   Yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümleri algılama yolu ancak isteğinde bulunduğunuzu belirli sürümü bunlar arasında değil doğru sürümü yoklama yola taşınsa bile bu sürümü yüklemek için sonraki denemeler başarısız olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derleme yoklama tarafından bulunamadığından oluşan derleme bağlama hataları önbelleğe almayı devre dışı bırakmak gösterilmiştir.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
