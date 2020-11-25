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
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727919"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName Yöntemi

Bu [IAssemblyName](iassemblyname-interface.md) nesnesi tarafından başvurulan derlemenin okunabilir adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in, out] `szDisplayName` Bir null Sonlandırıcı karakteri de dahil olmak üzere geniş karakter cinsinden boyutu.  
  
 `dwDisplayFlags`  
 'ndaki Özelliklerini etkileyen [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi `szDisplayName` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Numaralandırmaları](fusion-enumerations.md)
