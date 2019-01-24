---
title: ICorDebugModule::GetToken Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f87724bda78c1948ae7e1ddfa3d586fe5b7e14e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575742"
---
# <a name="icordebugmodulegettoken-method"></a>ICorDebugModule::GetToken Metodu
Bu modül için tablo girişi için belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pToken`  
 [out] Bir işaretçi `mdModule` modülün meta verilerinin başvuran belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirteç geçirilebilir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [Imetadataımport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), ve [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veriler](../../../../docs/framework/unmanaged-api/metadata/index.md)
