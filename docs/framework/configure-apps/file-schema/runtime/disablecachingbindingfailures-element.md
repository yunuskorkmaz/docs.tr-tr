---
title: <disableCachingBindingFailures> Öğesi
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
ms.openlocfilehash: c9e608bfd54b641564a9095076455e10dd8653fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176129"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures> Öğesi

Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enabled|Gerekli öznitelik.<br /><br /> Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın. Bu, .NET Framework sürüm 2,0 ' den başlayarak varsayılan bağlama davranışıdır.|  
|1|Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın. Bu ayar 1,1 .NET Framework sürümünün bağlama davranışına geri döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 .NET Framework sürüm 2,0 ' den başlayarak, derlemelerin yüklenmesi için varsayılan davranış tüm bağlama ve yükleme hatalarının önbelleğe alınarak yapılır. Diğer bir deyişle, bir derlemeyi yükleme girişimi başarısız olursa, derlemeyi bulmaya gerek kalmadan, aynı derlemeyi yükleme isteklerinin sonraki istekleri hemen başarısız olur. Bu öğe, derleme yoklama yolunda bulunamadığı için oluşan bağlama hatalarının varsayılan davranışını devre dışı bırakır. Bu arızalar oluşturur <xref:System.IO.FileNotFoundException> .  
  
 Bazı bağlama ve yükleme hatalarının bu öğeden etkilenmemesi ve her zaman önbelleğe alınması gerekir. Bu arızalar, derlemenin bulunduğu ancak yüklenemediği için oluşur. <xref:System.BadImageFormatException>Ya da oluşturur <xref:System.IO.FileLoadException> . Aşağıdaki liste, bu hataların bazı örneklerini içerir.  
  
- Bir dosyayı yüklemeye çalışırsanız, geçerli bir derleme değilse, bozuk dosya doğru derlemeyle değiştirilse bile derlemeyi yükleme girişimleri başarısız olur.  
  
- Dosya sistemi tarafından kilitlenen bir derlemeyi yüklemeye çalışırsanız, derlemeyi yükleme girişimleri, derleme dosya sistemi tarafından serbest bırakıldıktan sonra bile başarısız olur.  
  
- Yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümü yoklama yolunda ise, ancak istediğiniz özel sürüm bunlar arasında değilse, doğru sürüm yoklama yoluna taşınsa bile bu sürümü yüklemeye yönelik sonraki girişimler başarısız olur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, derleme yoklama tarafından bulunamadığı için oluşan derleme bağlama hatalarının önbelleğe alınmasının nasıl devre dışı bırakılacağını gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../../deployment/how-the-runtime-locates-assemblies.md)
