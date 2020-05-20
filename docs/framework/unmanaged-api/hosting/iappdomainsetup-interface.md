---
title: IAppDomainSetup Arabirimi
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617067"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup Arabirimi
Konağın, <xref:System.AppDomain?displayProperty=nameWithType> kendisini oluşturmak Için [ICorRuntimeHost:: CreateDomainEx](icorruntimehost-createdomainex-method.md) metodunu çağırmadan önce bir tür yapılandırmasına izin veren özellikler sağlar.  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Uygulamayı içeren dizinin adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Uygulamanın adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Dosyaların gölge kopyalandığı uygulamaya özgü bir alanın adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Bir uygulama için yapılandırma dosyasının adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Dinamik olarak oluşturulan dosyaların depolandığı ve eriştiği dizinin adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Bu etki alanıyla ilişkili lisans dosyasının yolunu alır veya ayarlar.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Özel derlemeler için araştırmanın diziniyle birlikte birleştirilmiş dizinlerin listesini alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> .|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Uygulamanın arama yolundan dahil edilen veya hariç olmayan bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> .|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Gölge kopya oluşturulacak derlemeleri içeren dizinlerin adlarını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Gölge kopyalamanın açık veya kapalı olup olmadığını gösteren bir dize alır veya ayarlar. Geçerli değerler "true" veya "false" şeklindedir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IAppDomainSetup`Arabirim, <xref:System.IAppDomainSetup> türün uyguladığı yönetilen arabirime karşılık gelir <xref:System.AppDomainSetup> . <xref:System.IAppDomainSetup?displayProperty=nameWithType>Özelliklerinin ayrıntılı açıklamaları için bkz..  
  
 `IAppDomainSetup`oluşturma işleminden önce bir örneğe eklenebilen derleme bağlama bilgilerini temsil eder <xref:System.AppDomain> . Örneğin, bir ana bilgisayar, <xref:System.AppDomainSetup.ApplicationBase%2A> yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları olan kök dizin oluşturmak için özelliğini ayarlayabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Barındırma Arabirimleri](hosting-interfaces.md)
