---
title: ICorPublishProcess::IsManaged Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790534"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged Yöntemi
Bu [ICorPublishProcess](icorpublishprocess-interface.md) tarafından başvurulan işlemin yönetilen koda sahip olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbManaged`  
 dışı İşlemin yönetilen koda sahip olup olmadığını gösteren bir Boole değeri işaretçisi. İşlemin yönetilen kodu varsa değer `true`. Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli `ICorPublishProcess` sürümü yalnızca yönetilen koda sahip işlemlere erişime izin verdiğinden, `IsManaged` her zaman `true`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishProcess Arabirimi](icorpublishprocess-interface.md)
