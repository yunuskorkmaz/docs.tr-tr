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
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008202"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map Yöntemi
Meta veri imzalarını kullanarak derlemeler arasında bir ilişki eşler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkImp`  
 'ndaki İçeri aktarılan kod nesnesini temsil eden meta veri belirteci.  
  
 `tkEmit`  
 'ndaki Yayınlanan kod nesnesini temsil eden meta veri belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirteç yeniden eşlemesi bir birleştirme sırasında gerçekleştiğinde, özgün belirteç içeri aktarılan (kaynak) meta veri kapsamında kapsamlandırılır ve yeni belirteç, yayılan (hedef) meta veri kapsamında kapsamdadır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMapToken Arabirimi](imaptoken-interface.md)
