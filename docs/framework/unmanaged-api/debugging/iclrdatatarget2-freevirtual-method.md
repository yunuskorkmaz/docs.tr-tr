---
title: ICLRDataTarget2::FreeVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181408"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual Yöntemi
Ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri hedef işlemin adres alanında önceden ayrılmış olan belleği boşaltmak için tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `addr`  
 [in] A `CLRDATA_ADDRESS` belleğin boşaltılması için başlangıç adresini belirten bir değer.  
  
 `size`  
 [in] Serbest bırakılacak belleğin bayt cinsinden boyutu.  
  
 `typeFlags`  
 [in] Bellek boşaltma denetleyen bayraklar. Win32 bkz `VirtualFree` işlevi.  
  
## <a name="remarks"></a>Açıklamalar  
 `FreeVirtual` Yöntemi Win32 için mantıksal kapsayıcı olarak hizmet veren `VirtualFree` işlevi.  
  
 Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
