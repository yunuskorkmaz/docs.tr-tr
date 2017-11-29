---
title: "IMapToken::Map Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e3a9701bab27764803442a3cd0c24c4e412deaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imaptoken arabirimi](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
