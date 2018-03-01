---
title: "Silverlight için CreateDebuggingInterfaceFromVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c38171c5887bb207b3692e9fa92aa2be2bc72a27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Silverlight için CreateDebuggingInterfaceFromVersion İşlevi
Sunucudan döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesi kabul [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür (genellikle [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szDebuggeeVersion`  
 [in] Tarafından döndürülen hedef ayıklayıcı CLR sürüm dizesi [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Bir COM nesnesi için bir işaretçi işaretçisine (`IUnknown`). Bu nesne için cast bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , döndürülmeden önce nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 `ppCordb`arabirimini uygulayan geçerli bir nesneye başvuruyor [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi.  
  
 E_INVALIDARG  
 Ya da `szDebuggeeVersion` veya `ppCordb` null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 CLR hata ayıklama için gerekli bir bileşeni bulunamıyor. Bu, mscordbi.dll veya mscordaccore.dll CoreCLR.dll hedefi olarak aynı dizinde bulunamadığını anlamına gelir.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi.dll veya mscordaccore.dll CoreCLR.dll hedef aynı sürümde değil.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 İade edilemiyor bir [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen arabirimi bir hedef işlemde bir CLR ekleme ve CLR çalıştıran yönetilen kodda hata ayıklama için olanakları sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
