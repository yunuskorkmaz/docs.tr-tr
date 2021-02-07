---
description: ': ICorPublishAppDomain:: GetID Yöntemi hakkında daha fazla bilgi edinin'
title: ICorPublishAppDomain::GetID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: b3de19c053b5fcce2af5e0036ee6174b01700aac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721846"
---
# <a name="icorpublishappdomaingetid-method"></a>ICorPublishAppDomain::GetID Yöntemi

Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)için benzersiz tanımlayıcıyı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `puId`  
 dışı Uygulama etki alanının tanımlayıcısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Tanımlayıcı yalnızca kapsayan işlemin kapsamında benzersizdir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishAppDomain Arabirimi](icorpublishappdomain-interface.md)
