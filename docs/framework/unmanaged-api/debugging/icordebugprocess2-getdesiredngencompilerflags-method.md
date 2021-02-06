---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: GetDesiredNGENCompilerFlags yöntemi'
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: ddc1c3a958ef42ab51d0ae06fd7ff29b13829c3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650221"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu

Ortak dil çalışma zamanının (CLR) Bu işleme yüklenecek doğru ön derlenmiş (yerel) görüntüyü seçmek için kullandığı geçerli derleyici bayrağı ayarlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwFlags`  
 dışı Yüklenecek doğru önceden derlenmiş görüntüyü seçmek için kullanılan [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 CLR 'nin yüklenecek doğru önceden derlenmiş görüntüyü seçerken kullanacağı bayrakları ayarlamak için [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
