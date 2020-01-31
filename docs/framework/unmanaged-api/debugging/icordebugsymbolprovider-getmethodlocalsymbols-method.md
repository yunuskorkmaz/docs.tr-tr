---
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 41fc8e94ec8a5c8794674bebb32494bb3806e69d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791612"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a>ICorDebugSymbolProvider:: GetMethodLocalSymbols yöntemi
Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nativeRVA`  
 'ndaki Metodun yerel göreli sanal adresi.  
  
 `cRequestedSymbols`  
 'ndaki İstenen yerel semboller sayısı.  
  
 `pcFetchedSymbols`  
 dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.  
  
 `pcFetchedSymbols`  
 dışı Metodun yerel sembollerini içeren [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetMethodParameterSymbols Yöntemi](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
