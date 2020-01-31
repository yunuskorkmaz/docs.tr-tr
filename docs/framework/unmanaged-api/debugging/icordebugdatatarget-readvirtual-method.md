---
title: ICorDebugDataTarget::ReadVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
ms.openlocfilehash: 20cea94961a250c3981d892910da1dcee20a060b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783733"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual Yöntemi
Belirtilen adresten başlayarak bir ardışık bellek bloğunu alır ve sağlanan arabellekte döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki İstenen belleğin başlangıç adresi.  
  
 `pbuffer`  
 dışı Belleğin depolanacağı arabellek.  
  
 `bytesRequested`  
 'ndaki Hedef adresten alınacak bayt sayısı.  
  
 `pBytesRead`  
 dışı Hedef adresten gerçekten okunan bayt sayısı. Bu, `bytesRequested`daha az olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 İlk bayt (belirtilen başlangıç adresinde) okunurken, çağrının başarılı döndürmesi gerekir (null ile sonlandırılmış dizeler gibi, kendi kendine tanımlayan uzunlukla veri yapılarının etkili şekilde okunmasını desteklemek için).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget Arabirimi](icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
