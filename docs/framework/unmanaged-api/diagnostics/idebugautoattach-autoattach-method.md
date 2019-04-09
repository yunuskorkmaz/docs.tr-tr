---
title: IDebugAutoAttach::AutoAttach Yöntemi
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5064e66708044d82e3a097c8235b5b28a3412200
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077140"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach Yöntemi
Hata ayıklayıcı sunucu çağrılan otomatik gerçekleştirir ekleyin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `guidPort`  
 [in] Her zaman `GUID_NULL`.  
  
 `dwPid`  
 [in] İşlem kimliği, normalde alınan `GetCurrentProcessId` işlevi.  
  
 `dwProgramType`  
 [in] Program türü: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, veya `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] Program Kimliği  
  
 `pszSessionId`  
 [in] Debug fiilini tarafından geçirilen dize.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDebugAutoAttach Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
