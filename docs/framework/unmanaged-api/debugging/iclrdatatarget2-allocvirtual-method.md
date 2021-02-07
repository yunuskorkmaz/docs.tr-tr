---
description: 'Daha fazla bilgi edinin: ICLRDataTarget2:: AllocVirtual Yöntemi'
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
ms.openlocfilehash: d81474e4067599178285b6fa876919298617919d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729347"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual Yöntemi

Bu hedef işlemin adres alanına bellek ayırmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `addr`  
 'ndaki `CLRDATA_ADDRESS` Ayrılacak belleğin istenen başlangıç adresini belirten bir değer.  
  
 `size`  
 'ndaki Ayrılacak belleğin bayt cinsinden boyutu.  
  
 `typeFlags`  
 'ndaki Bellek ayırmayı denetleyen bayraklar. Bkz. Win32 `VirtualAlloc` işlevi.  
  
 `protectFlags`  
 'ndaki Ayrılan bellek için koruma öznitelikleri. Bkz. Win32 `VirtualAlloc` işlevi.  
  
 `virt`  
 dışı `CLRDATA_ADDRESS` Ayrılan belleğin gerçek başlangıç adresini belirten bir değer işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `AllocVirtual`Yöntemi, Win32 işlevi için bir mantıksal sarmalayıcı görevi görür `VirtualAlloc` .  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget2 Arabirimi](iclrdatatarget2-interface.md)
- [FreeVirtual Yöntemi](iclrdatatarget2-freevirtual-method.md)
