---
title: "CreateAssemblyCache İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyCache
helpviewer_keywords: CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b6dfc8cd90b5a37b82b26d4f8e494159dc1fd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblycache-function"></a>CreateAssemblyCache İşlevi
Bir işaretçi yeni bir alır [Iassemblycache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) Genel Derleme Önbelleği temsil eden örneği.  
  
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
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `dwReserved`0 (sıfır) olması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iassemblycache arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [Fusion genel statik işlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)
