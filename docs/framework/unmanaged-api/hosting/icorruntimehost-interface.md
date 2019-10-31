---
title: ICorRuntimeHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: e66e1468a864ec85d88f759c481c7a9707d37f7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139538"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost Arabirimi
Ana bilgisayarın ortak dil çalışma zamanını (CLR) açık olarak başlatıp durdurmasına, uygulama etki alanlarını oluşturup yapılandırmasına, varsayılan etki alanına erişime ve işlemde çalışan tüm etki alanlarını listelemeye olanak tanıyan yöntemler sağlar.  
  
 .NET Framework sürüm 2,0 ' de, bu arabirimin yerini [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)almıştır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Bir etki alanı numaralandırıcısını etki alanı listesinin başına geri döndürür.|  
|[CreateDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Bir uygulama etki alanı oluşturur. Çağıran, <xref:System.AppDomain?displayProperty=nameWithType>türünde bir örneğe <xref:System._AppDomain> türünde bir arabirim işaretçisi alır.|  
|[CreateDomainEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Bir uygulama etki alanı oluşturur. Bu yöntem, çağıranın döndürülen <xref:System._AppDomain> örneğinin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar.|  
|[CreateDomainSetup Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|<xref:System.AppDomainSetup> örneğine `IAppDomainSetup` türünde bir arabirim işaretçisi alır. `IAppDomainSetup`, bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.|  
|[CreateEvidence Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|<xref:System.Security.Principal.IIdentity>türünde bir arabirim işaretçisi alır, bu da konağın [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) veya [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)öğesine geçirilecek güvenlik kanıtı oluşturmasına izin verir.|  
|[CreateLogicalThreadState Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Kullanmayın.|  
|[CurrentDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Geçerli iş parçacığında yüklü olan etki alanını temsil eden <xref:System._AppDomain> türünde bir arabirim işaretçisi alır.|  
|[DeleteLogicalThreadState Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Kullanmayın.|  
|[EnumDomains Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Geçerli işlemdeki etki alanları için bir Numaralandırıcı alır.|  
|[GetConfiguration Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Konağın CLR 'nin geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.|  
|[GetDefaultDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Geçerli işlem için varsayılan etki alanını temsil eden <xref:System._AppDomain> türünde bir arabirim işaretçisi alır.|  
|[LocksHeldByLogicalThread Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Kullanmayın.|  
|[MapFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Belirtilen dosyayı belleğe eşler. Bu yöntem artık kullanılmıyor.|  
|[NextDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.|  
|[Start Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|CLR 'yi başlatır.|  
|[Stop Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.|  
|[SwitchInLogicalThreadState Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Kullanmayın.|  
|[SwitchOutLogicalThreadState Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Kullanmayın.|  
|[UnloadDomain Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Belirtilen uygulama etki alanını geçerli işlemden kaldırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain>
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Çalışma zamanı Konakları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
