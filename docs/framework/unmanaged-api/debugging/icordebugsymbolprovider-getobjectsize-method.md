---
description: ': ICorDebugSymbolProvider:: GetObjectSize yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetObjectSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 72720a1af9958fd0ab91276b3967733cec77fee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659717"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a>ICorDebugSymbolProvider:: GetObjectSize yöntemi

Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cbSignature`  
 'ndaki TypeSpec imzasında bayt sayısı.  
  
 Tür Imza  
 'ndaki TypeSpec imzası.  
  
 `pObjectSize`  
 dışı Nesnenin boyutuna yönelik bir işaretçi.  
  
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
