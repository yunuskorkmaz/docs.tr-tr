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
ms.openlocfilehash: d8ea7df9396e9199d04ad5609daa9d2b01761f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798897"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo İşlevi
[Tlibattr](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) yapısını inceleyerek belirtilen tür kitaplığıyla ilgili bilgileri döndürür.  
  
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
 'ndaki Tür kitaplığının dosya adı.  
  
 `pTypeLibID`  
 dışı Tür kitaplığının GUID 'SI.  
  
 `pTypeLibLCID`  
 dışı Tür kitaplığının yerelleştirme KIMLIĞI.  
  
 `pTypeLibPlatform`  
 dışı Tür kitaplığı için hedef işletim sistemini tanımlayan bir [Syskind](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı. Ortak değerler SYS_WIN32 ve SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 dışı Tür kitaplığının ana sürüm numarası. Örneğin, *x. y*sürümü için ana sürüm numarası *x*olur.  
  
 `pTypeLibMinorVer`  
 dışı Tür kitaplığının ikincil sürüm numarası. Örneğin, *x. y*sürümü için, ikincil sürüm numarası *y*' dir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevi Tlbexp [. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır. `GetTypeLibInfo` Bu araç, ortak dil çalışma zamanı (CLR) derlemesindeki türleri açıklayan bir tür kitaplığı oluşturur.  
  
 Herhangi bir parametre null ise, işlev ' ı döndürür `HRESULT`. `E_POINTER` Aksi takdirde, döndürür `S_OK`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** TlbRef. h  
  
 **Kitaplığı** TlbRef. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tlbexp Yardımcı İşlevleri](index.md)
- [LoadTypeLibEx Işlevi](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
