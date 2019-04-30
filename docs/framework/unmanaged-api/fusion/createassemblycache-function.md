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
ms.openlocfilehash: bf78ded62f11b336d9f5fe0f3a205275ae37189b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669994"
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
  
## <a name="parameters"></a>Parametreler  
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
