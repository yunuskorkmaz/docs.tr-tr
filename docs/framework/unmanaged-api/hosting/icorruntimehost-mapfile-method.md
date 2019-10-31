---
title: ICorRuntimeHost::MapFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: bcf1b49f0576f5dbd73c001f8edff7a9ab29af22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139513"
---
# <a name="icorruntimehostmapfile-method"></a>ICorRuntimeHost::MapFile Yöntemi
Belirtilen dosyayı belleğe eşler. Bu yöntem artık kullanılmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hFile`  
 'ndaki Eşlenecek dosyanın tanıtıcısı.  
  
 `hMapAddress`  
 dışı Dosyanın eşlenmesinin başlayacağı başlangıç belleği adresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
