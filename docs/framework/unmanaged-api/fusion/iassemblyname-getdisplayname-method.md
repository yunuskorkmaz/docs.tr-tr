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
ms.openlocfilehash: 38f48f2d95829d2c8111065e5f4ede4e43a16d63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796656"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName Yöntemi
Bu [IAssemblyName](iassemblyname-interface.md) nesnesi tarafından başvurulan derlemenin okunabilir adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szDisplayName`  
 dışı Başvurulan derlemenin adını içeren dize arabelleği.  
  
 `pccDisplayName`  
 [in, out] Bir null Sonlandırıcı `szDisplayName` karakteri de dahil olmak üzere geniş karakter cinsinden boyutu.  
  
 `dwDisplayFlags`  
 'ndaki Özelliklerini`szDisplayName`etkileyen [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Sabit Listeleri](fusion-enumerations.md)
