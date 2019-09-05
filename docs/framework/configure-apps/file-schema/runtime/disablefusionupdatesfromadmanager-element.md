---
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b65711ad8c404d1c4f54a6197faf598e2215226f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252658"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > öğesi
Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enabled|Gerekli öznitelik.<br /><br /> Fusion ayarlarını geçersiz kılabilme özelliğinin devre dışı bırakılıp bırakılmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın. Bu, .NET Framework 4 ' ün başladığı varsayılan davranıştır.|  
|1\.|Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın. Bu, .NET Framework önceki sürümlerinin davranışına geri döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te başlayarak, varsayılan <xref:System.AppDomainManager> davranış, nesnenin, uygulamanıza geçirilen <xref:System.AppDomainSetup> nesnenin <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğini veya <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemini kullanarak yapılandırma ayarlarını geçersiz kılmasına izin vermesidir , kendi<xref:System.AppDomainManager>alt sınıfdaki <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi. Varsayılan uygulama etki alanı için, değiştirdiğiniz ayarlar uygulama yapılandırma dosyası tarafından belirtilen ayarları geçersiz kılar. Diğer uygulama etki alanları için <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemine geçirilen yapılandırma ayarlarını geçersiz kılarlar.  
  
 İletilen yapılandırma bilgilerini ortadan kaldırmak için yeni yapılandırma bilgilerini geçirebilir ya da`Nothing` null (Visual Basic) geçirebilirsiniz.  
  
 Yapılandırma bilgilerini hem <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğine <xref:System.AppDomainSetup.SetConfigurationBytes%2A> hem de yöntemine iletmeyin. Yapılandırma bilgilerini her ikisine de geçirirseniz, <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasından yapılandırma bilgilerini geçersiz kıldığından, özelliğe geçirdiğiniz bilgiler göz ardı edilir. <xref:System.AppDomainSetup.ConfigurationFile%2A> Özelliğini kullanırsanız, <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomainSetup.SetConfigurationBytes%2A> `Nothing` yöntemine<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yapılan çağrıda belirtilen yapılandırma baytlarını ortadan kaldırmak için yöntemine null (Visual Basic) geçirebilirsiniz.  
  
 Yapılandırma <xref:System.AppDomainSetup> bilgilerine ek olarak, <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.ApplicationBase%2A> yöntemiuygulamanızageçirilennesne<xref:System.AppDomainSetup.DisallowBindingRedirects%2A> üzerinde aşağıdaki ayarları değiştirebilirsiniz:,,,, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> ,,<xref:System.AppDomainSetup.LoaderOptimization%2A>, ,,<xref:System.AppDomainSetup.PrivateBinPath%2A>, ,<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, ve<xref:System.AppDomainSetup.ShadowCopyFiles%2A>. <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>  
  
 `<disableFusionUpdatesFromADManager>` Öğesini kullanmaya alternatif olarak, bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak varsayılan davranışı devre dışı bırakabilirsiniz. Kayıt defterinde, veya `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework`altında adlı bir DWORD değeri oluşturun ve değeri 1 olarak ayarlayın. Komut satırında, ortam değişkenini `COMPLUS_disableFusionUpdatesFromADManager` 1 olarak ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `<disableFusionUpdatesFromADManager>` öğesini kullanarak Fusion ayarlarını geçersiz kılma yeteneğinin nasıl devre dışı bırakılacağını gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../deployment/how-the-runtime-locates-assemblies.md)
