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
ms.openlocfilehash: 0ec28c581b8e6e0aff3a2765720b6e9795be931b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003106"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo İşlevi
Belirtilen tür kitaplığı hakkında bilgi inceleyerek döndürür, [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
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
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** TlbRef.h  
  
 **Kitaplığı:** TlbRef.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tlbexp Yardımcı İşlevleri](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx işlevi](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
