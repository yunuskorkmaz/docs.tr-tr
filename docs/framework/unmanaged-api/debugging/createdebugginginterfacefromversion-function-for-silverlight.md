---
title: Silverlight için CreateDebuggingInterfaceFromVersion İşlevi
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 438af9f191f48a86207c3b343ba428eef2c1fabc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132196"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Silverlight için CreateDebuggingInterfaceFromVersion İşlevi
[CreateVersionStringFromModule işlevinden](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimini (genellikle, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szDebuggeeVersion`  
 'ndaki [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)tarafından döndürülen hedef hata ayıklanan clr 'nin sürüm dizesi.  
  
 `ppCordb`  
 dışı COM nesnesi işaretçisi işaretçisi (`IUnknown`). Bu nesne, döndürülmeden önce bir [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesnesine atacaktır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 `ppCordb` [ICorDebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimini uygulayan geçerli bir nesneye başvurur.  
  
 E_INVALIDARG  
 `szDebuggeeVersion` ya da `ppCordb` null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 CLR hata ayıklaması için gerekli bir bileşen bulunamıyor. Bu, mscordbi. dll veya mscordaccore. dll ' nin hedef CoreCLR. dll ile aynı dizinde bulunamadığı anlamına gelir.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi. dll veya mscordaccore. dll, hedef CoreCLR. dll ile aynı sürümde değil.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 [ICorDebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)döndürülemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen arabirim, hedef işlemdeki bir CLR 'ye ekleme ve CLR 'nin çalıştığı yönetilen kodda hata ayıklama için tesisler sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
