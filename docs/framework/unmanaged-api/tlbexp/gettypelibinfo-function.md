---
title: GetTypeLibInfo İşlevi
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 916d62a2b79a44d92611e735c6f9bbb3e01970e2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782737"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo İşlevi
Belirtilen tür kitaplığı hakkında bilgi inceleyerek döndürür, [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szFile`  
 [in] Tür kitaplığı dosyasının adı.  
  
 `pTypeLibID`  
 [out] Tür kitaplığının GUID.  
  
 `pTypeLibLCID`  
 [out] Tür kitaplığının yerelleştirme kimliği.  
  
 `pTypeLibPlatform`  
 [out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) tür kitaplığı için hedef işletim sistemini tanımlayan bir bayrak. Genel değerler şunlardır: SYS_WIN32 ve SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 [out] Tür kitaplığı sürüm sayısı. Örneğin, sürüm için *x.y*, ana sürüm numarası *x*.  
  
 `pTypeLibMinorVer`  
 [out] Tür kitaplığının ikincil sürüm numarası. Örneğin, sürüm için *x.y*, ikincil sürüm numarası *y*.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetTypeLibInfo` İşlevi çağrıldığında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). Bu araç, bir ortak dil çalışma zamanı (CLR) derlemedeki türleri açıklayan bir tür kitaplığı üretir.  
  
 Herhangi bir parametre null ise, işlev döndürür bir `HRESULT` , `E_POINTER`. Aksi halde `S_OK`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** TlbRef.h  
  
 **Kitaplığı:** TlbRef.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tlbexp Yardımcı İşlevleri](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx işlevi](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
