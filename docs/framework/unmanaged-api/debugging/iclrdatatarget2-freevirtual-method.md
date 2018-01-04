---
title: "ICLRDataTarget2::FreeVirtual Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.FreeVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6c52291d08af4c9537de6ca17d80f28870a6bc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual Yöntemi
Hedef işlemin adres alanında daha önce ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `addr`  
 [in] A `CLRDATA_ADDRESS` boşaltılacak belleğin başlangıç adresini belirten değer.  
  
 `size`  
 [in] Boşaltılacak belleğin bayt cinsinden boyutu.  
  
 `typeFlags`  
 [in] Bellek boşaltma kontrol bayraklar. Win32 bkz `VirtualFree` işlevi.  
  
## <a name="remarks"></a>Açıklamalar  
 `FreeVirtual` Yöntemi Win32 için mantıksal bir kapsayıcı olarak hizmet veren `VirtualFree` işlevi.  
  
 Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [AllocVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
