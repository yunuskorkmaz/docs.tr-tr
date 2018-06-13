---
title: ICLRDataTarget2::AllocVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46532592057f4fa6d9883d46dcef2f8f9e5f7228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406350"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual Yöntemi
Bu hedef işlem adres alanındaki bellek ayıramadı ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `addr`  
 [in] A `CLRDATA_ADDRESS` ayrılacak bellek istenen başlangıç adresini belirten değer.  
  
 `size`  
 [in] Ayrılacak belleğin bayt cinsinden boyutu.  
  
 `typeFlags`  
 [in] Bellek ayırma kontrol bayraklar. Win32 bkz `VirtualAlloc` işlevi.  
  
 `protectFlags`  
 [in] Ayrılan belleğin koruması öznitelikleri. Win32 bkz `VirtualAlloc` işlevi.  
  
 `virt`  
 [out] Bir işaretçi bir `CLRDATA_ADDRESS` ayrılmış bellek gerçek başlangıç adresini belirten değer.  
  
## <a name="remarks"></a>Açıklamalar  
 `AllocVirtual` Yöntemi Win32 için mantıksal bir kapsayıcı olarak hizmet veren `VirtualAlloc` işlevi.  
  
 Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [FreeVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
