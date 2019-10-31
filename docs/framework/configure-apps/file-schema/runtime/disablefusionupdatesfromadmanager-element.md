---
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117452"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > öğesi
Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
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
|etkinletir|Gerekli öznitelik.<br /><br /> Fusion ayarlarını geçersiz kılabilme özelliğinin devre dışı bırakılıp bırakılmadığını belirtir.|  
  
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
 .NET Framework 4 ' te başlayarak, varsayılan davranış, <xref:System.AppDomainManager> nesnesinin <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğini kullanarak yapılandırma ayarlarını geçersiz kılmasını ve <xref:System.AppDomainSetup> yönteminin uygulamanıza geçirilmiş <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> nesnesinin <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemini kullanmasına izin vermesidir. , <xref:System.AppDomainManager>alt sınıfın. Varsayılan uygulama etki alanı için, değiştirdiğiniz ayarlar uygulama yapılandırma dosyası tarafından belirtilen ayarları geçersiz kılar. Diğer uygulama etki alanları için, <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemine geçirilmiş yapılandırma ayarlarını geçersiz kılar.  
  
 İletilen yapılandırma bilgilerini ortadan kaldırmak için yeni yapılandırma bilgilerini geçirebilir veya null (`Nothing` Visual Basic) geçirebilirsiniz.  
  
 Yapılandırma bilgilerini hem <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğine hem de <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemine iletmeyin. Yapılandırma bilgilerini her ikisine de geçirirseniz, <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğine geçirdiğiniz bilgiler yoksayılır, çünkü <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasından yapılandırma bilgilerini geçersiz kılar. <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğini kullanıyorsanız, <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemine yapılan çağrıda belirtilen yapılandırma baytlarını ortadan kaldırmak için <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemine null (Visual Basic`Nothing`) geçirebilirsiniz.  
  
 Yapılandırma bilgilerine ek olarak, <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yönteminin uygulamanıza geçirilen <xref:System.AppDomainSetup> nesnesi üzerinde aşağıdaki ayarları değiştirebilirsiniz: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>ve <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 `<disableFusionUpdatesFromADManager>` öğesinin kullanılmasına alternatif olarak, bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak varsayılan davranışı devre dışı bırakabilirsiniz. Kayıt defterinde `HKCU\Software\Microsoft\.NETFramework` veya `HKLM\Software\Microsoft\.NETFramework`altında `COMPLUS_disableFusionUpdatesFromADManager` adlı bir DWORD değeri oluşturun ve değeri 1 olarak ayarlayın. Komut satırında `COMPLUS_disableFusionUpdatesFromADManager` ortam değişkenini 1 olarak ayarlayın.  
  
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
