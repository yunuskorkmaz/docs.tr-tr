---
title: 'ICorDebugSymbolProvider:: GetCodeRange yöntemi'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: f61a98dbd5a65207a46e033d54f9d5f60adac201
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709134"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider:: GetCodeRange yöntemi

Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `codeRva`  
 'ndaki Bir yöntemde göreli sanal adres (RVA).  
  
 `pCodeStartAddress`  
 dışı Metodun başlangıç adresine yönelik bir işaretçi.  
  
 `pCodeSize`  
 Yöntem kodu boyutuna yönelik bir işaretçi (yöntemin kodunun bayt sayısı).  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
