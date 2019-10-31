---
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
ms.openlocfilehash: 014bd4f2b12c84790065f76a67765aaf35e8b2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131678"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference Yöntemi
Bu [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesinin temsil ettiği [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısına yönelik bir işaretçi alır.  
  
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
 dışı Döndürülen `FUSION_INSTALL_REFERENCE` işaretçisi.  
  
 `dwFlags`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `dwFlags` 0 (sıfır) olmalıdır.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved`, null bir başvuru olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IInstallReferenceItem Arabirimi](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE Yapısı](fusion-install-reference-structure.md)
