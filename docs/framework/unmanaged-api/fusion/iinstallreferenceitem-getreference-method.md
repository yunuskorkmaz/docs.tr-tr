---
description: 'Şu konuda daha fazla bilgi edinin: IInstallReferenceItem:: GetReference Yöntemi'
title: IInstallReferenceItem::GetReference Yöntemi
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
ms.openlocfilehash: 88f5ca21b6f3494031e1cd232f71253e39d9e648
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800126"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference Yöntemi

Bu [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesi tarafından temsil edilen [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısına yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppRefData`  
 dışı Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.  
  
 `dwFlags`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `dwFlags` 0 (sıfır) olmalıdır.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved` null bir başvuru olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IInstallReferenceItem Arabirimi](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE Yapısı](fusion-install-reference-structure.md)
