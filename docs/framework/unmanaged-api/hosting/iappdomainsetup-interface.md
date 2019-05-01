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
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970033"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup Arabirimi
Yapılandırmak konak izin verme özellikleri sağlar bir <xref:System.AppDomain?displayProperty=nameWithType> çağırmadan önce türü [Icorruntimehost::createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) oluşturmak için yöntemi.  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Alır veya ayarlar uygulamasını içeren dizinin adı.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Uygulamanın adını alır veya ayarlar.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Alır veya bir alanın adını belirli uygulamayı gölge kopyalanan dosyaların nerede ayarlar.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Alır veya bir uygulama yapılandırma dosyası adını ayarlar.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Alır veya ayarlar dinamik olarak oluşturulan dosyaların nerede depolanır ve erişilebilir bir dizinin adı.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Alır ya da bu etki alanı ile ilişkili lisans dosyasının yolunu ayarlar.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Alır veya birlikte dizinler listesini ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> özel derlemeler için araştırma için dizin.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|İçerir veya dışlar bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> uygulama için arama yolu.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Alır veya gölge kopyalar derlemeler içeren dizin adlarını ayarlar.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Alır veya ayarlar gölge kopyalama hakkında açık olup olmadığını gösteren bir dize. Geçerli değerler "true" veya "false".|  
  
## <a name="remarks"></a>Açıklamalar  
 `IAppDomainSetup` Arabirimi karşılık gelen yönetilen <xref:System.IAppDomainSetup> arabirim, hangi <xref:System.AppDomainSetup> yazın uygular. Bkz: <xref:System.IAppDomainSetup?displayProperty=nameWithType> özelliklerini ayrıntılı açıklamaları için.  
  
 `IAppDomainSetup` eklenebilir derleme bağlama bilgilerini temsil eden bir <xref:System.AppDomain> örneği oluşturulduktan önce. Örneğin, bir konak ayarlayabilirsiniz <xref:System.AppDomainSetup.ApplicationBase%2A> Yönetilen derlemeler için ortak dil çalışma zamanı (CLR) araştırmalarını bir kök dizin oluşturmak için özellik.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
