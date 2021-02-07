---
description: ': Imetadatayayma:: SaveToStream yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SaveToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 104aa0b0dfcd0f4f9e8b87b4633880f6423f92d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706662"
---
# <a name="imetadataemitsavetostream-method"></a>IMetaDataEmit::SaveToStream Yöntemi

Geçerli kapsamdaki tüm meta verileri belirtilen öğesine kaydeder `IStream` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pIStream`  
 'ndaki Kaydedilecek yazılabilir akış.  
  
 `dwSaveFlags`  
 'ndaki Ayrılamadı. Sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
