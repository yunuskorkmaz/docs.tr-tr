---
title: ICorDebugFunction::GetILCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetILCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba960246c5aa1057df517d776819817d777402f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode Metodu
Bu ICorDebugFunction nesneyle ilişkili Microsoft Ara dili (MSIL) kodunu temsil eder Icordebugcode örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppCode`  
 [out] Bir işaretçi `ICorDebugCode` örneği veya işlev MSIL derlenmemiş yoksa null.  
  
## <a name="remarks"></a>Açıklamalar  
 Düzenle ve devam et izin veriyorsa bu işlevi üzerinde `GetILCode` yöntemi, bu işlevin düzenlenen ortak dil çalışma zamanı (CLR) kodda sürümüne karşılık gelen MSIL kodu alırsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
