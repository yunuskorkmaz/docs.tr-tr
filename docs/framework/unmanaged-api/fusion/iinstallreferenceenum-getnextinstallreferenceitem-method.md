---
title: IInstallReferenceEnum::GetNextInstallReferenceItem Metodu
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
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f3a1b745c3ee28c126e328b1a3fa9e283f98d99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a>IInstallReferenceEnum::GetNextInstallReferenceItem Metodu
Bir işaretçi sonraki alır [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) bu konuda yer alan nesne [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppRefItem`  
 [out] Döndürülen `IInstallReferenceItem` işaretçi.  
  
 `dwFlags`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `dwFlags`0 (sıfır) olması gerekir.  
  
 `pvReserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `pvReserved`bir null başvuru olması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IInstallReferenceItem Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [IInstallReferenceEnum Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
