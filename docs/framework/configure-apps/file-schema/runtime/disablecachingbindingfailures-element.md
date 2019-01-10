---
title: '&lt;disableCachingBindingFailures&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78ca269dacc33fb441310ad00ba2548826f5403e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610521"
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disableCachingBindingFailures&gt; öğesi
Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakılıp bırakılmayacağını belirtir.  
  
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
|Etkin|Gerekli öznitelik.<br /><br /> Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakılıp bırakılmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakmayın. .NET Framework sürüm 2.0 ile başlayarak varsayılan bağlama davranışı budur.|  
|1.|Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakın. Bu ayar, .NET Framework sürüm 1.1 bağlama davranışını geri döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 2.0 ile başlayarak, tüm bağlama ve yükleme hatalarını önbelleğe almak için derlemeleri yüklemek için varsayılan davranış şeklindedir. Diğer bir deyişle, bir derlemeyi yüklemek için bir deneme başarısız olursa, aynı derlemenin yüklemek için sonraki istekleri hemen derlemeyi bulmak için her türlü girişim başarısız. Bu öğe Derleme yoklama yolu bulunamadı nedeniyle oluşabilecek hataları bağlama için bu varsayılan davranışı devre dışı bırakır. Bu hatalar throw <xref:System.IO.FileNotFoundException>.  
  
 Bazı bağlama ve yükleme hatalarını bu öğe tarafından etkilenmez ve her zaman önbelleğe alınır. Derleme bulundu, ancak yüklenemedi çünkü bu hatalar oluşur. Oluştururlar <xref:System.BadImageFormatException> veya <xref:System.IO.FileLoadException>. Aşağıdaki listede, bu tür hataları bazı örnekleri içerir.  
  
-   Yüklemeye çalışırsanız, bir dosya geçerli bir derleme değil, hatalı dosya doğru derleme ile değiştirilir bile derlemesini yüklemek için sonraki denemeler başarısız olur.  
  
-   Dosya sistemi tarafından kilitlenmiş bir derlemeyi yüklemeye çalışırsanız, derleme bile dosya sistemi tarafından serbest bırakıldıktan sonra derlemeyi yüklemek için sonraki denemeler başarısız olur.  
  
-   Araştırma yolu doğru sürümü taşınsa dahi yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümleri olan algılama yolu, ancak istediğiniz belirli bir sürüm bunlar arasında değil, bu sürümü yüklemek için sonraki denemeler başarısız olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, derleme yoklama işlemi tarafından bulunamadığı için oluşan bir derleme bağlama hataları önbelleğe almayı devre dışı bırakmak gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
