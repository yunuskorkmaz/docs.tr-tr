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
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503906"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost Arabirimi
Ana bilgisayarın ortak dil çalışma zamanını (CLR) açık olarak başlatıp durdurmasına, uygulama etki alanlarını oluşturup yapılandırmasına, varsayılan etki alanına erişime ve işlemde çalışan tüm etki alanlarını listelemeye olanak tanıyan yöntemler sağlar.  
  
 .NET Framework sürüm 2,0 ' de, bu arabirimin yerini [ICLRRuntimeHost](iclrruntimehost-interface.md)almıştır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[CloseEnum Yöntemi](icorruntimehost-closeenum-method.md)|Bir etki alanı numaralandırıcısını etki alanı listesinin başına geri döndürür.|  
|[CreateDomain Yöntemi](icorruntimehost-createdomain-method.md)|Bir uygulama etki alanı oluşturur. Çağıran, türünde bir örneğine türünde bir arabirim işaretçisi alır <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> .|  
|[CreateDomainEx Yöntemi](icorruntimehost-createdomainex-method.md)|Bir uygulama etki alanı oluşturur. Bu yöntem, çağıranın döndürülen örneğin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar <xref:System._AppDomain> .|  
|[CreateDomainSetup Yöntemi](icorruntimehost-createdomainsetup-method.md)|Bir örneğe türün arabirim işaretçisini alır `IAppDomainSetup` <xref:System.AppDomainSetup> . `IAppDomainSetup`, bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.|  
|[CreateEvidence Yöntemi](icorruntimehost-createevidence-method.md)|<xref:System.Security.Principal.IIdentity>Konağın, [CreateDomain](icorruntimehost-createdomain-method.md) veya [CreateDomainEx](icorruntimehost-createdomainex-method.md)'e geçiş için güvenlik kanıtı oluşturmasına olanak tanıyan bir arabirim işaretçisi alır.|  
|[CreateLogicalThreadState Yöntemi](icorruntimehost-createlogicalthreadstate-method.md)|Kullanmayın.|  
|[CurrentDomain Yöntemi](icorruntimehost-currentdomain-method.md)|<xref:System._AppDomain>Geçerli iş parçacığında yüklü olan etki alanını temsil eden türün bir arabirim işaretçisini alır.|  
|[DeleteLogicalThreadState Yöntemi](icorruntimehost-deletelogicalthreadstate-method.md)|Kullanmayın.|  
|[EnumDomains Yöntemi](icorruntimehost-enumdomains-method.md)|Geçerli işlemdeki etki alanları için bir Numaralandırıcı alır.|  
|[GetConfiguration yöntemi](icorruntimehost-getconfiguration-method.md)|Konağın CLR 'nin geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.|  
|[GetDefaultDomain Yöntemi](icorruntimehost-getdefaultdomain-method.md)|<xref:System._AppDomain>Geçerli işlem için varsayılan etki alanını temsil eden türün bir arabirim işaretçisini alır.|  
|[LocksHeldByLogicalThread Yöntemi](icorruntimehost-locksheldbylogicalthread-method.md)|Kullanmayın.|  
|[MapFile Yöntemi](icorruntimehost-mapfile-method.md)|Belirtilen dosyayı belleğe eşler. Bu yöntem artık kullanılmıyor.|  
|[NextDomain Yöntemi](icorruntimehost-nextdomain-method.md)|Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.|  
|[Start yöntemi](icorruntimehost-start-method.md)|CLR 'yi başlatır.|  
|[Stop Yöntemi](icorruntimehost-stop-method.md)|Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.|  
|[SwitchInLogicalThreadState Yöntemi](icorruntimehost-switchinlogicalthreadstate-method.md)|Kullanmayın.|  
|[SwitchOutLogicalThreadState Yöntemi](icorruntimehost-switchoutlogicalthreadstate-method.md)|Kullanmayın.|  
|[UnloadDomain Yöntemi](icorruntimehost-unloaddomain-method.md)|Belirtilen uygulama etki alanını geçerli işlemden kaldırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain>
- [Hosting](index.md)
- [ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)
- [Çalışma zamanı Konakları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)
