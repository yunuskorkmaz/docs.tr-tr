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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77164f9d8a1641ba37fa504d09d77ec6aecc3db5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965821"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Silverlight için CreateDebuggingInterfaceFromVersion İşlevi
Öğesinden döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)ve karşılık gelen bir hata ayıklayıcı arabirim döndürür (genelde [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szDebuggeeVersion`  
 [in] Hedef hata ayıklanan tarafından döndürülen CLR sürüm dizesi [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Bir COM nesnesine bir işaretçi işaretçisi (`IUnknown`). Bu nesne için atayın bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) döndürülmeden önce nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 `ppCordb` uygulayan geçerli bir nesneye başvuruda [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi.  
  
 E_INVALIDARG  
 Ya da `szDebuggeeVersion` veya `ppCordb` null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 CLR hata ayıklama için gerekli olan bir bileşeni bulunamıyor. Bu, mscordbi.dll ya da mscordaccore.dll CoreCLR.dll hedef ile aynı dizinde bulunamadığını anlamına gelir.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi.dll ya da mscordaccore.dll CoreCLR.dll hedefi olarak aynı sürüm değil.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Döndürülemiyor bir [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen arabirim için bir hedef işlemde bir CLR ekleme ve CLR çalışan yönetilen kodda hata ayıklama özellikleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
