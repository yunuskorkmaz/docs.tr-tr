---
description: 'Daha fazla bilgi edinin: ClrCreateManagedInstance Işlevi'
title: ClrCreateManagedInstance İşlevi
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: b6d3b014f54dd563e53cd8a4c48907d01945015f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799937"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance İşlevi

Belirtilen yönetilen türün bir örneğini oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır. Yönetilen türün bir örneğini oluşturmak için COM etkinleştirmesini kullanın veya barındırma kullanın (bkz. [.NET Framework 4 ve 4,5 ' de eklenen clr barındırma arabirimleri](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pTypeName`  
 'ndaki İstenen örnek türünün adına yönelik bir işaretçi.  
  
 `riid`  
 'ndaki `IID` İstenen örnek türü.  
  
 `ppObject`  
 dışı Çağıran tarafından istenen yönetilen tür örneğine yönelik işaretçiye yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanının zaten bir işleme yüklenmiş olması gerekir. Örneğin, işlev çağrılmadan önce [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevine yapılan bir çağrı kullanılarak yüklenebilir `ClrCreateManagedInstance` . Çalışma zamanı yüklü değilse, `ClrCreateManagedInstance` önce çalışma zamanının v 1.0.3705 sürümünü yüklemeye çalışır. Başarısız olursa, çalışma zamanının en son sürümünü yüklemeye çalışır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
- [Hosting](index.md)
