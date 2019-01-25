---
title: CreateAssemblyCache İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5869bf22c74a232f20fc49fe81a6a35c9738f1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735035"
---
# <a name="createassemblycache-function"></a>CreateAssemblyCache İşlevi
Yeni bir işaretçi alır [Iassemblycache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) genel derleme önbelleğini temsil eden örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppAsmCache`  
 [out] Döndürülen `IAssemblyCache` işaretçi.  
  
 `dwReserved`  
 [in] Sonra genişletilebilmek için ayrılmış. `dwReserved` 0 (sıfır) olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IAssemblyCache Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)
