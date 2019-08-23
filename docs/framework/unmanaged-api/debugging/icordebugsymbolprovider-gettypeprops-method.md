---
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ea3a201cc94ef7bdf679371ef43ab2641b791
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955545"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider:: GetTypeProps yöntemi
Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tableRva`  
 'ndaki Vtable içindeki göreli bir sanal adres (RVA).  
  
 `cbSignature`  
 'ndaki `signature` Dizinin boyutu. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 dışı dışı Döndürülen `signature` dizinin boyutuna yönelik bir işaretçi.  
  
 `signature`  
 dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 Türün `signature` dizisinin gerekli boyutunu almak için, `cbSignature` bağımsız değişkenini 0 ve `signature` **null**olarak ayarlayın. Yöntemi döndüğünde, `pcbSignature` `signature` dizi için gereken bayt sayısını içerir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
