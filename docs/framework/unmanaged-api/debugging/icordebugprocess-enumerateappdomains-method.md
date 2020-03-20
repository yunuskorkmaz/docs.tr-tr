---
title: ICorDebugProcess::EnumerateAppDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: 4489238df05edef384b4073ee738a184ff8809ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178666"
---
# <a name="icordebugprocessenumerateappdomains-method"></a>ICorDebugProcess::EnumerateAppDomains Yöntemi
Bu işlemdeki tüm uygulama etki alanlarını oyalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppAppDomains`  
 [çıkış] Bu işlemde uygulama etki alanları için bir sayısallaştırıcı bir [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) adresine bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem [ICorDebugManagedCallback önce kullanılabilir::CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri arama.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
