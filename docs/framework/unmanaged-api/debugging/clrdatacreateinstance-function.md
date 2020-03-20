---
title: CLRDataCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179357"
---
# <a name="clrdatacreateinstance-function"></a>CLRDataCreateInstance İşlevi
Belirtilen hedef öğe için bir arabirim nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iid`  
 [içinde] Arabirimin tanımlayıcısı anında alınacak.  
  
 `target`  
 [içinde] Arabirim nesnesini oluşturmak için hedef öğeyi temsil eden kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine işaretçi.  
  
 `iface`  
 [çıkış] Döndürülen arabirim nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Nesne `ICLRDataTarget` hata ayıklama uygulamasının yazarı tarafından uygulanır. Uygulama, temsil edilen hedef öğenin türüne bağlıdır. Hedef öğe bir işlem, bellek dökümü, uzak makine ve benzeri olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** ClrData.idl  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
