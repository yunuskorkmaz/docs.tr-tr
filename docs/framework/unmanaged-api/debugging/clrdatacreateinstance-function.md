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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274271"
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
 'ndaki Oluşturulacak arabirimin tanımlayıcısı.  
  
 `target`  
 'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.  
  
 `iface`  
 dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRDataTarget` Nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır. Uygulama, temsil edilen hedef öğe türüne bağlıdır. Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** ClrData. IDL  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
