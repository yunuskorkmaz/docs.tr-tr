---
title: CreateCordbObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: d21e0d3d0370ec7c1b223be29099f6b99822463b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132115"
---
# <a name="createcordbobject-function"></a>CreateCordbObject İşlevi
Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iDebuggerVersion`  
 'ndaki Hedef işlemin hata ayıklayıcı sürümü. Bu parametre, uzaktan hata ayıklama için CorDebugVersion_2_0 olmalıdır.  
  
 `ppCordb`  
 dışı [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimine verilecek ve döndürülen bir nesne işaretçisinin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.  
  
 E_INVALIDARG  
 `ppCordb` null veya `iDebuggerVersion` CorDebugVersion_2_0 değil.  
  
 E_OUTOFMEMORY  
 `ppCordb` için yeterli bellek ayrılamıyor  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 Diğer sorunlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `ppCordb` döndürülen [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi, tüm yönetilen hata ayıklama Hizmetleri için en üst düzey hata ayıklama arabirimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
