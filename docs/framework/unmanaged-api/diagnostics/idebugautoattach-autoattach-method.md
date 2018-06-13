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
ms.openlocfilehash: e5c95423a6918da7cc043f8d46de13d166b8d895
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426191"
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
  
#### <a name="parameters"></a>Parametreler  
 `guidPort`  
 [in] Her zaman `GUID_NULL`.  
  
 `dwPid`  
 [in] İşlem kimliği, normalde ile alınan `GetCurrentProcessId` işlevi.  
  
 `dwProgramType`  
 [in] Program türü: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, veya `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] Program Kimliği  
  
 `pszSessionId`  
 [in] Debug fiilini tarafından geçirilen dize.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugAutoAttach Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
