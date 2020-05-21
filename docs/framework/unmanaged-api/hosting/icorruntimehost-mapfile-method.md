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
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762675"
---
# <a name="icorruntimehostmapfile-method"></a>ICorRuntimeHost::MapFile Yöntemi
Belirtilen dosyayı belleğe eşler. Bu yöntem artık kullanılmıyor.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümü:** 1,0, 1,1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
