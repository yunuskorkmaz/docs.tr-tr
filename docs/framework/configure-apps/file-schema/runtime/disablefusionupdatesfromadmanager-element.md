---
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117452"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> Öğesi
Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
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
|1|Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın. Bu, .NET Framework önceki sürümlerinin davranışına geri döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te başlayarak, varsayılan davranış, <xref:System.AppDomainManager> nesnenin <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> alt sınıflarınızdaki yöntemi uygulamanıza geçirilen nesnenin özelliğini veya yöntemini kullanarak yapılandırma ayarlarını geçersiz kılmasına izin vermesidir <xref:System.AppDomainManager> . Varsayılan uygulama etki alanı için, değiştirdiğiniz ayarlar uygulama yapılandırma dosyası tarafından belirtilen ayarları geçersiz kılar. Diğer uygulama etki alanları için veya yöntemine geçirilen yapılandırma ayarlarını geçersiz kılarlar <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .  
  
 İletilen yapılandırma bilgilerini ortadan kaldırmak için yeni yapılandırma bilgilerini geçirebilir ya da null ( `Nothing` Visual Basic) geçirebilirsiniz.  
  
 Yapılandırma bilgilerini hem özelliğine hem de yöntemine iletmeyin <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> . Yapılandırma bilgilerini her ikisine de geçirirseniz, <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasından yapılandırma bilgilerini geçersiz kıldığından, özelliğe geçirdiğiniz bilgiler göz ardı edilir. <xref:System.AppDomainSetup.ConfigurationFile%2A>Özelliğini kullanırsanız, `Nothing` <xref:System.AppDomainSetup.SetConfigurationBytes%2A> veya yöntemine yapılan çağrıda belirtilen yapılandırma baytlarını ortadan kaldırmak için yöntemine null (Visual Basic) geçirebilirsiniz <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .  
  
 Yapılandırma bilgilerine ek olarak,,,,,,,,, <xref:System.AppDomainSetup> ,,,, ve, yöntemi uygulamanıza geçirilen nesne üzerinde aşağıdaki ayarları değiştirebilirsiniz <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> :,,,,, <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> , <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> , <xref:System.AppDomainSetup.DynamicBase%2A> , <xref:System.AppDomainSetup.LoaderOptimization%2A> ,,, <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> ve <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .  
  
 Öğesini kullanmaya alternatif olarak `<disableFusionUpdatesFromADManager>` , bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak varsayılan davranışı devre dışı bırakabilirsiniz. Kayıt defterinde, veya altında adlı bir DWORD değeri `COMPLUS_disableFusionUpdatesFromADManager` oluşturun `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` ve değeri 1 olarak ayarlayın. Komut satırında, ortam değişkenini `COMPLUS_disableFusionUpdatesFromADManager` 1 olarak ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesini kullanarak Fusion ayarlarını geçersiz kılma yeteneğinin nasıl devre dışı bırakılacağını gösterir `<disableFusionUpdatesFromADManager>` .  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../../deployment/how-the-runtime-locates-assemblies.md)
