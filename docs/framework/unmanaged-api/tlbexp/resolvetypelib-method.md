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
ms.openlocfilehash: ce0f11547d4b16516b7c78d1b1947f5c4bc831a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798804"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib Yöntemi
Tam nitelikli yolunu döndürerek bir tür kitaplığının basit adını çözer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bstrSimpleName`  
 'ndaki Tür kitaplığının basit adını içeren bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) .  
  
 `tlbid`  
 'ndaki Kayıt defterindeki tür kitaplığına atanan GUID.  
  
 `lcid`  
 'ndaki Tür kitaplığının yerelleştirme KIMLIĞI.  
  
 `wMajorVersion`  
 'ndaki Tür kitaplığının ana sürüm numarası. Örneğin, *x. y*sürümü için ana sürüm numarası *x*olur.  
  
 `wMinorVersion`  
 'ndaki Tür kitaplığının ikincil sürüm numarası. Örneğin, *x. y*sürümü için, ikincil sürüm numarası *y*' dir.  
  
 `syskind`  
 'ndaki İşletim ortamını tanımlayan bir [Syskind](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı. Ortak değerler SYS_WIN32 ve SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 dışı `bstrSimpleName` Parametresinde adlı tür kitaplığının tam yolunu içeren bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi, [Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md) işleme sırasında [LoadTypeLibWithResolver işlevi](loadtypelibwithresolver-function.md) tarafından çağrılır. `ResolveTypeLib`  
  
 Bu arabirimin özel uygulamaları, `bstrSimpleName` parametresinde adlı tür kitaplığının tam yolunu içeren bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** TlbRef. IDL, TlbRef. h  
  
 **Kitaplığı** TlbRef. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tlbexp Yardımcı İşlevleri](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
