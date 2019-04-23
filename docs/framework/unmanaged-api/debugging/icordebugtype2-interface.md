---
title: ICorDebugType2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 878941f7af71fa5e3de8e38c4a68a66cb964983d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223166"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2 Arabirimi
Tür tanımlayıcısını bir taban türü veya karmaşık türü (kullanıcı tanımlı) almak için Icordebugtype arabirimi genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem||  
|------------|-|  
|[GetTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Alır bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu tür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Icordebugtype arabirimi öğesinin mantıksal uzantısı arabirimidir.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod parçası kullanışını [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi.  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
