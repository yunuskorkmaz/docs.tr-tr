---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 02cc62a421058f83e28ce945ae9e76745f768988
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791562"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a>ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi
TypeSpec imzasına karşılık gelen statik alan sembollerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki `typeSig` dizisindeki bayt sayısı.  
  
 `typeSig`  
 'ndaki `typespec` imzasını içeren bir bayt dizisi.  
  
 `cRequestedSymbols`  
 'ndaki İstenen simgelerin sayısı.  
  
 `pcFetchedSymbols`  
 dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.  
  
 `pSymbols`  
 dışı İstenen statik alan sembollerini içeren [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetInstanceFieldSymbols Yöntemi](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
