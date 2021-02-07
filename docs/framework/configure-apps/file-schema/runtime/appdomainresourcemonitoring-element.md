---
description: 'Daha fazla bilgi edinin: <appDomainResourceMonitoring> öğesi'
title: <appDomainResourceMonitoring> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: aee85386e6d0af2ca4fd30c0ad8fe69bae240315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719298"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomainResourceMonitoring> Öğesi

Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Uygulama etki alanı kaynak izleme istatistikleri toplanır.|  
|`false`|Uygulama etki alanı kaynak izleme istatistikleri toplanmadı.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Uygulama etki alanı kaynak izleme, yönetilen uygulama etki alanı sınıfı, barındırma [ıclartppdomainresourcemonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve Windows için olay Izleme (ETW) ile kullanılabilir. İzleme etkinleştirildiğinde, işlem süresince işlemdeki tüm uygulama etki alanları için istatistikler toplanır.  
  
 Yönetilen koddan izlemeyi etkinleştirmek için <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliğini kullanın.  
  
 Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, uygulama etki alanı kaynak izlemenin nasıl etkinleştirileceği gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
