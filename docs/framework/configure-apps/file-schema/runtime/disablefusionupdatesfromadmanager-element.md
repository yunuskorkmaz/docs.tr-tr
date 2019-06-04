---
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c96d5aea150c0dbb55889e9fc26417e7803a155
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487670"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > öğesi
Uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmak çalışma zamanı ana bilgisayarı izin vermek için varsayılan davranışı devre dışı bırakılıp bırakılmadığını belirtir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<disableFusionUpdatesFromADManager >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> Fusion ayarlarını geçersiz kılmak için varsayılan özelliği devre dışı bırakılıp bırakılmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Fusion ayarları geçersiz kılma yeteneği devre dışı bırakmayın. .NET Framework 4 ile başlayarak varsayılan davranışı budur.|  
|1.|Fusion ayarları geçersiz kılma yeteneği devre dışı bırakın. Bu, .NET Framework'ün önceki sürümlerinde, davranıştır döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ile başlayarak izin vermek için varsayılan davranış olduğu <xref:System.AppDomainManager> kullanarak yapılandırma ayarlarını geçersiz kılmak için nesne <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği veya <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi <xref:System.AppDomainSetup> uygulamanız için geçirilen nesne ' ın <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yönteminde, öğesinin <xref:System.AppDomainManager>. Varsayılan uygulama etki alanı için ayarları değiştirmeniz, uygulama yapılandırma dosyasında belirtilen ayarları geçersiz kılar. Diğer uygulama etki alanları için bunlar için geçirilmiş yapılandırma ayarları geçersiz kılar <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemi.  
  
 Yeni yapılandırma bilgilerini geçirmek veya null değeri geçirmeye (`Nothing` Visual Basic'te) geçirilen yapılandırma bilgilerini ortadan kaldırmak için.  
  
 Yapılandırma bilgilerini hem de geçmeyin <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği ve <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi. Yapılandırma bilgilerini hem de geçirirseniz, bilgileri için geçirdiğiniz <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği göz ardı edilir, çünkü <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasına yapılandırma bilgilerini geçersiz kılar. Kullanırsanız <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği, geçirebilirsiniz null (`Nothing` Visual Basic'te) için <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi çağrısında belirtilen herhangi bir yapılandırma bayt ortadan kaldırmak için <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemi.  
  
 Yapılandırma bilgilerine ek olarak, aşağıdaki ayarları değiştirebilirsiniz <xref:System.AppDomainSetup> uygulamanıza geçirilen nesne <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, ve <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Kullanmaya alternatif olarak `<disableFusionUpdatesFromADManager>` öğesini devre dışı bırakabilirsiniz varsayılan davranışı bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak. Kayıt defterindeki adlı bir DWORD değeri oluşturun `COMPLUS_disableFusionUpdatesFromADManager` altında `HKCU\Software\Microsoft\.NETFramework` veya `HKLM\Software\Microsoft\.NETFramework`ve değeri 1 olarak ayarlayın. Komut satırında, ortam değişkenini ayarlamak `COMPLUS_disableFusionUpdatesFromADManager` 1.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Fusion ayarları kullanarak geçersiz kılma yeteneği devre dışı bırakma gösterir `<disableFusionUpdatesFromADManager>` öğesi.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
