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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176077"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map Yöntemi
Meta veri imzalarını kullanarak derlemeler arasındaki ilişkiyi eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkImp`  
 [içinde] İçe aktarılan kod nesnesini temsil eden meta veri belirteci.  
  
 `tkEmit`  
 [içinde] Yayılan kod nesnesini temsil eden meta veri belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirteç yeniden eşlemi birleştirme sırasında gerçekleştiğinde, özgün belirteç içe aktarılan (kaynak) meta veri kapsamında ve yeni belirteç yayılan (hedef) meta veri kapsamında kapsamlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMapToken Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
