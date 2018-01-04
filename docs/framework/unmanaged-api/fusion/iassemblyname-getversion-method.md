---
title: IAssemblyName::GetVersion Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetVersion
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad4084bc758ec8a0b6d97ef211555ccbe78f3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamegetversion-method"></a>IAssemblyName::GetVersion Metodu
Bu tarafından başvurulan derlemenin sürüm bilgisi alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwVersionHi`  
 [out] Yüksek 32 bit sürümü.  
  
 `pdwVersionLow`  
 [out] Düşük 32 bit sürümü.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IAssemblyName Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
