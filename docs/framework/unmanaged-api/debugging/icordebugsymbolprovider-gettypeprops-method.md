---
title: ICorDebugSymbolProvider::GetTypeProps yöntemi
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca23cd58e36b62e471cc7b0b2d0aa743265c2f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482359"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider::GetTypeProps yöntemi
Göreli sanal adres (RVA) içinde bir vtable verilen imza, genel parametrelerinin sayısı gibi bir türün özellikleri hakkında bilgi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tableRva`  
 [in] Bir vtable'da göreli sanal adres (RVA).  
  
 `cbSignature`  
 [in] Boyutu `signature` dizisi. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 [out] [out] Boyut döndürülen işaretçi `signature` dizisi.  
  
 `signature`  
 [out] Tüm genel parametreler TypeSpec'te imzalarını tutan arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 Türün gerekli boyutunu almak için `signature` ayarlayın, dizi `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**. Yöntem döndürüldüğünde `pcbSignature` için gereken bayt sayısını içerir `signature` dizisi.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
