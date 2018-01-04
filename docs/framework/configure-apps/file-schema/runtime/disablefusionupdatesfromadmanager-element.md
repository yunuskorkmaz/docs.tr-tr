---
title: "&lt;disableFusionUpdatesFromADManager&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d3a1214b4aecf56c9a6440e31459573a5922676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disableFusionUpdatesFromADManager&gt; öğesi
Uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmak çalışma zamanı konak izin vermek için varsayılan davranışı devre dışı olup olmadığını belirtir.  
  
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
|Etkin|Gerekli öznitelik.<br /><br /> Fusion ayarlarını geçersiz kılmak için varsayılan özelliği devre dışı olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Fusion ayarlarını geçersiz kılma yeteneği devre dışı bırakmayın. Sürümünden itibaren varsayılan davranış budur [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1.|Fusion ayarlarını geçersiz kılma yeteneği devre dışı bırakın. Bu, .NET Framework'ün önceki sürümlerinde davranışını geri döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayan [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], varsayılan davranış izin vermektir <xref:System.AppDomainManager> kullanarak yapılandırma ayarlarını geçersiz kılmak için nesne <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği veya <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi <xref:System.AppDomainSetup> uygulamanız için geçirilen nesnesi <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yönteminde, alt <xref:System.AppDomainManager>. Varsayılan uygulama etki alanı için ayarları değiştirmeniz uygulama yapılandırma dosyasında belirtilen ayarları geçersiz kılar. Diğer uygulama etki alanları için bunlar için geçirilmiş yapılandırma ayarları geçersiz kılar <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemi.  
  
 Yeni yapılandırma bilgilerini geçirin veya null geçirin (`Nothing` Visual Basic'te) geçirildi yapılandırma bilgilerini ortadan kaldırmak için.  
  
 Yapılandırma bilgilerini hem de geçmeyin <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği ve <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi. Yapılandırma bilgilerini hem de geçerse, bilgileri için geçirdiğiniz <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği göz ardı edilir, çünkü <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasındaki yapılandırma bilgilerini geçersiz kılar. Kullanırsanız <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliği, iletebilir null (`Nothing` Visual Basic'te) için <xref:System.AppDomainSetup.SetConfigurationBytes%2A> çağrısında belirtilen bir yapılandırma bayt ortadan kaldırmak için yöntemi <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemi.  
  
 Yapılandırma bilgilerine ek olarak, aşağıdaki ayarları değiştirebilirsiniz <xref:System.AppDomainSetup> uygulamanıza geçirilen nesne <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, ve <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Kullanmaya alternatif olarak `<disableFusionUpdatesFromADManager>` öğesini devre dışı bırakabilirsiniz varsayılan davranışı bir kayıt defteri ayarı oluşturarak veya bir ortam değişkeni ayarlayarak. Kayıt defterinde adlı bir DWORD değeri oluşturun `COMPLUS_disableFusionUpdatesFromADManager` altında `HKCU\Software\Microsoft\.NETFramework` veya `HKLM\Software\Microsoft\.NETFramework`ve değerini 1 olarak ayarlayın. Komut satırında, ortam değişkenini `COMPLUS_disableFusionUpdatesFromADManager` 1.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanarak Fusion ayarlarını geçersiz kılma yeteneği devre dışı bırakma gösterir `<disableFusionUpdatesFromADManager>` öğesi.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
