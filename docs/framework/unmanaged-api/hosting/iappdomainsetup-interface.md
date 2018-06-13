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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcbc446eabcfcbc28c830f8860bde726c8eb6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434774"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup Arabirimi
Yapılandırmak konak izin verme özellikler sağlayan bir <xref:System.AppDomain?displayProperty=nameWithType> türü çağırmadan önce [Icorruntimehost::createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) oluşturmak için yöntemi.  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Alır veya uygulamayı içeren dizinin adını ayarlar.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Uygulamanın adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Alır veya bir alanın adı belirli uygulamaya gölge kopyalanan dosyaların nerede ayarlar.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Alır veya ayarlar uygulamanın yapılandırma dosyasının adı.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Alır veya dinamik olarak üretilen dosyaları nerede depolanır ve erişilen dizin adını ayarlar.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Alır veya bu etki alanı ile ilişkili lisans dosyasının yolunu ayarlar.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Alır veya ayarlar ile bir araya dizinler listesinde <xref:System.AppDomainSetup.ApplicationBase%2A> özel derlemeler için araştırma için dizin.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|İçerir veya dışlar bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> uygulama için arama yolundan.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Alır veya gölge kopyalar olması için derlemeleri içeren dizin adlarını ayarlar.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Alır veya ayarlar gölge kopyalama veya açık olup olmadığını belirten bir dize. Geçerli değerler "true" veya "false".|  
  
## <a name="remarks"></a>Açıklamalar  
 `IAppDomainSetup` Arabirimi karşılık gelen yönetilen <xref:System.IAppDomainSetup> arabirim, hangi <xref:System.AppDomainSetup> yazın uygular. Bkz: <xref:System.IAppDomainSetup?displayProperty=nameWithType> özelliklerini ayrıntılı açıklamaları için.  
  
 `IAppDomainSetup` eklenebilir derleme bağlama bilgilerini temsil eden bir <xref:System.AppDomain> örneği oluşturulduktan önce. Örneğin, bir ana bilgisayar ayarlayabilirsiniz <xref:System.AppDomainSetup.ApplicationBase%2A> Yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları bir kök dizin oluşturmak için özellik.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
