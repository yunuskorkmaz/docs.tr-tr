---
title: "ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 923f7f4178d3c310b51ebb7e7df06040ba69f9c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a>ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi
Sağlanan işaretçi bütünleştirilmiş listesinde başvurduğu olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pName`  
 [in] Arabirim işaretçisi aranacak derleme. Geçerli değerler türünü `IAssemblyName` veya `IReferenceIdentity`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Dize listede görüntülenir.|  
|S_FALSE|Dize, listede görünmez.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Ortak dil çalışma zamanı, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrassemblyıdentitymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Iclrassemblyreferencelist arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Ihostassemblymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Ihostassemblystore arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
