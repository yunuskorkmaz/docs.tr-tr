---
title: ICorDebugModule2::GetJITCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
ms.openlocfilehash: 6af5bc22616be196be7fdb0d417800d631d87506
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213653"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a>ICorDebugModule2::GetJITCompilerFlags Metodu
Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwFlags`  
 dışı JıT derlemesini denetleyen [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırması değerine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
