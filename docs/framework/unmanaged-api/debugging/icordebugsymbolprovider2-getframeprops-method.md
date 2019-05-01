---
title: ICorDebugSymbolProvider2::GetFrameProps yöntemi
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b20d78abbfa1db43047872a596289028833de37d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994129"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2::GetFrameProps yöntemi
Bir yöntemi ve üst çerçevenin bir kod göreli sanal adres verilen göreli sanal adres başlangıç yöntemi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `codeRva`  
 [in] Bir kod göreli sanal adres.  
  
 `pCodeStartRva`  
 [out] Göreli sanal adres yöntemin başlangıç için bir işaretçi.  
  
 `pParentFrameStartRva`  
 [out] Çerçeve göreli sanal adres başlangıç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
