---
title: "ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd2d6ac2967b4314a57aa30bbb34ff3d354a6365
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi
Yönetilmeyen bir kesme noktası belirtilen yerel görüntü uzaklığı ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` nesne yerel görüntü uzaklığını belirtir.  
  
 `bufsize`  
 [in] Bayt olarak boyutu, `buffer` dizi.  
  
 `buffer`  
 [out] Kesme noktası tarafından değiştirilir işlem kodu içeren bir dizi.  
  
 `bufLen`  
 [out] Döndürülen bayt sayısı için bir işaretçi `buffer` dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel görüntü uzaklık ortak dil çalışma zamanı içinde (CLR) ise, kesme yoksayılacak. Bu kesme hata ayıklayıcı ayarlandığında, bant dışı kesme göndermeyi önlemek CLR sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
