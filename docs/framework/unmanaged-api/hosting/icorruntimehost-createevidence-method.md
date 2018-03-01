---
title: "ICorRuntimeHost::CreateEvidence Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 754b254fb9a41ab8bb900fdb5d0c10a126b804c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence Yöntemi
Arabirim işaretçisi türü alır <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, geçirilecek güvenlik bulgu oluşturmak için ana sağlayan [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) veya [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pEvidence`  
 [out] Arabirim işaretçisi bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> güvenlik bulgu oluşturmak için kullanılan örnek. Bu işaretçinin yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` gösteren bir işaretçi almak için bu arabirimdeki bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlem başarılı oldu.|  
|S_FALSE|İşlemi tamamlayamadı.|  
|E_FAIL|Bilinmeyen, geri dönülemez bir hata oluştu. Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz. Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, yerel koddan doldurulamaz boş bir koleksiyon döndürür. Kullanmanız gereken <xref:System.Security.Policy.Evidence> yöntemi yerine.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümü:** 1.0, 1.1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
