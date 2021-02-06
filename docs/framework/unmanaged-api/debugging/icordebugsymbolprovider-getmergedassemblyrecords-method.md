---
description: ': ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: f12bb3a49d7b49f9f8916c9d04417340502d44ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659887"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a>ICorDebugSymbolProvider:: GetMergedAssemblyRecords yöntemi

Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cRequestedRecords`  
 'ndaki İstenen sembol kaydı sayısı.  
  
 `pcFetchedRecords`  
 dışı Yöntemi tarafından alınan sembol kayıtlarının sayısına yönelik bir işaretçi.  
  
 `pRecords`  
 [Icordebugmergedassemblyrecord](icordebugmergedassemblyrecord-interface.md) nesnelerinin dizisine yönelik bir işaretçi.  
  
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
