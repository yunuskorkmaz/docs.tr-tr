---
title: ResolveTypeLib Yöntemi
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96a9672ee05cb1fe2573620bd1dea23e57339c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib Yöntemi
Basit bir tür kitaplığı adı, tam yolunu döndürerek çözümler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bstrSimpleName`  
 [in] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) basit tür kitaplığı adını içerir.  
  
 `tlbid`  
 [in] Tür kitaplığı kayıt defterinde atanan GUID.  
  
 `lcid`  
 [in] Tür kitaplığı yerelleştirme kimliği.  
  
 `wMajorVersion`  
 [in] Tür kitaplığı ana sürüm numarası. Örneğin, sürüm *x.y*, ana sürüm numarası *x*.  
  
 `wMinorVersion`  
 [in] Tür kitaplığı ikincil sürüm numarası. Örneğin, sürüm *x.y*, ikincil sürüm numarası *y*.  
  
 `syskind`  
 [in] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) işletim sistemi ortamında belirleyen bayrak. SYS_WIN32 ve SYS_WIN64 bunun ortak değerlerdir.  
  
 `pbstrResolvedTlbName`  
 [out] Bir işaretçi bir [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) adlı tür kitaplığı tam yolunu içeren `bstrSimpleName` parametresi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ResolveTypeLib` Yöntemi çağrılır [LoadTypeLibWithResolver işlevi](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) sırasında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) işleme.  
  
 Bu arabirim özel uygulamaları döndürmelidir bir [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) adlı tür kitaplığı tam yolunu içeren `bstrSimpleName` parametresi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** TlbRef.idl, TlbRef.h  
  
 **Kitaplığı:** TlbRef.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tlbexp Yardımcı İşlevleri](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
