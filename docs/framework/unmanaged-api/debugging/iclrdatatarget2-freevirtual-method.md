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
ms.openlocfilehash: 0a36af5b411673081e74aa243ec8e0f8f876f238
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860478"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual Yöntemi
Daha önce hedef işlemin adres alanında ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `addr`  
 'ndaki Boşaltılacak `CLRDATA_ADDRESS` belleğin başlangıç adresini belirten bir değer.  
  
 `size`  
 'ndaki Boşaltılacak belleğin bayt cinsinden boyutu.  
  
 `typeFlags`  
 'ndaki Belleğin boşaltımı kontrol eden bayraklar. Bkz. Win32 `VirtualFree` işlevi.  
  
## <a name="remarks"></a>Açıklamalar  
 `FreeVirtual` Yöntemi, Win32 `VirtualFree` işlevi için bir mantıksal sarmalayıcı görevi görür.  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget2 Arabirimi](iclrdatatarget2-interface.md)
- [AllocVirtual Yöntemi](iclrdatatarget2-allocvirtual-method.md)
