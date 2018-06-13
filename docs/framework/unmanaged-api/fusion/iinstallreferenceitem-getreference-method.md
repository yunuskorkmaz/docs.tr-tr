---
title: IInstallReferenceItem::GetReference Metodu
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6c64b98f3b5ab0445b076b0d3bacfaa398e26f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429774"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference Metodu
Bir işaretçi alır [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) bu tarafından temsil edilen yapısı [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppRefData`  
 [out] Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.  
  
 `dwFlags`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `dwFlags` 0 (sıfır) olması gerekir.  
  
 `pvReserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `pvReserved` bir null başvuru olması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IInstallReferenceItem Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [FUSION_INSTALL_REFERENCE Yapısı](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
