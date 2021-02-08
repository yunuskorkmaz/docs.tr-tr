---
description: ': ICorProfilerObjectEnum:: Clone yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerObjectEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 59971f6f6e7edab4b4c4f796ee7bea3c4d8b4e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798959"
---
# <a name="icorprofilerobjectenumclone-method"></a>ICorProfilerObjectEnum::Clone Yöntemi

Bu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) arabiriminin bir kopyasına yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppEnum`  
 dışı Arabirim işaretçisinin, bu arabirimin kopyasına işaret eden bir işaretçisi `ICorProfilerObjectEnum` . Kopya kendi numaralandırma durumunu bu bilgisayardan ayrı olarak tutar. Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynı olacaktır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerObjectEnum Arabirimi](icorprofilerobjectenum-interface.md)
