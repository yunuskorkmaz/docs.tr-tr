---
description: 'Şu konuda daha fazla bilgi edinin: CLRDataCreateInstance Işlevi'
title: CLRDataCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- DLLExport
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 923b0c687d2b337eacb475973927452e3b47ad0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747263"
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

 `ICLRDataTarget`Nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır. Uygulama, temsil edilen hedef öğe türüne bağlıdır. Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL  
  
 **Kitaplık:** Corguid. lib  

 **Bütünleştirilmiş kod**: mscordacwks.dll, mscordbi.dll
  
 **.NET Framework sürümleri:** .NET Framework 2,0 tarihinden itibaren kullanılabilir
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
