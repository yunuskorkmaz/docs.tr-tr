---
description: ': ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 379d943743bb1fe21edbcca2265b4d8613d4f4b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659900"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a>ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi

TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cbSignature`  
 'ndaki Dizideki bayt sayısı `typeSig` .  
  
 `typeSig`  
 'ndaki İmzayı içeren bir bayt dizisi `typespec` .  
  
 `cRequestedSymbols`  
 'ndaki İstenen simgelerin sayısı.  
  
 `pcFetchedSymbols`  
 dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.  
  
 `pSymbols`  
 dışı İstenen örnek alanı sembollerini içeren bir [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetStaticFieldSymbols Yöntemi](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
