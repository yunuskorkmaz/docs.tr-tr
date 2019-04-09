---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols yöntemi
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18bfab7a666a4c715b2236f5101bcceacb5b2fed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072694"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a>ICorDebugSymbolProvider::GetStaticFieldSymbols yöntemi
TypeSpec'te imza karşılık gelen statik alan simgelerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cbSignature`  
 [in] Bayt sayısı `typeSig` dizisi.  
  
 `typeSig`  
 [in] İçeren bir bayt dizisi `typespec` imzası.  
  
 `cRequestedSymbols`  
 [in] İstenen sembolleri sayısı.  
  
 `pcFetchedSymbols`  
 [out] Yöntemi tarafından alınan simgelerin sayısını bir işaretçi.  
  
 `pSymbols`  
 [out] Bir işaretçi bir [Icordebugstaticfieldsymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) istenen statik alan simgeleri içeren bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetInstanceFieldSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
