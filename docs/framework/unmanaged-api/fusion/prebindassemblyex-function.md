---
title: PreBindAssemblyEx İşlevi
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa2d174200db76f5c7a6db43e14bb6904604226
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796333"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx İşlevi
Bir derlemenin ilke sonrası görünen adını alır.  
  
 Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppCtx`  
 'ndaki Uygulama bağlamını tanımlar.  
  
 `pName`  
 'ndaki Derleme adını tanımlar.  
  
 `pAsmParent`  
 'ndaki Üst derlemeyi tanımlar. Bu parametre yoksayıldı.  
  
 `pwzRuntimeVersion`  
 'ndaki Çalışma zamanı sürümünü tanımlar.  
  
 `ppNamePostPolicy`  
 dışı İlke sonrası görünen adını içerir.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved`null bir başvuru olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `ppNamePostPolicy` Output parametresi yalnızca işlev HRESULT FUSION_E_REF_DEF_MISMATCH döndürürse ayarlanır. Aksi halde, null olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
