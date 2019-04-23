---
title: IAssemblyName::GetDisplayName Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 323c883b4010f3ddd4c575e5d5fc40a3419e57c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214370"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName Yöntemi
Okunabilir bu başvurduğu derlemenin adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szDisplayName`  
 [out] Başvurulan derlemenin adını içeren dize arabelleği.  
  
 `pccDisplayName`  
 [out içinde] Boyutu `szDisplayName` geniş karakter, bir sonlandırıcı null karakter de dahil olmak üzere.  
  
 `dwDisplayFlags`  
 [in] Bitsel bir birleşimi [asm_dısplay_flags](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) özelliklerini etkileyen değerleri `szDisplayName`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Fusion Sabit Listeleri](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
