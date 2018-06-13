---
title: IMapToken::Map Yöntemi
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2633bfadaabf208a2b86fda83375c3a136b93b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448178"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map Yöntemi
Meta veri imzaları kullanarak derlemeler arasında bir ilişki eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tkImp`  
 [in] İçeri aktarılan kod nesnesini temsil eden meta veri simgesi.  
  
 `tkEmit`  
 [in] Verilmiş kod nesnesini temsil eden meta veri simgesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirteç eşleme yeniden birleştirme sırasında ortaya çıktığında, özgün belirteç alınan (kaynak) meta veri kapsamda kapsamlıdır ve yeni belirteci verilmiş (hedef) meta veri kapsamda kapsamlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMapToken Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
