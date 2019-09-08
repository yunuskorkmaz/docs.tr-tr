---
title: Init Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787239"
---
# <a name="init-method"></a>Init Yöntemi
Kullanım için [IALink arabirimini](ialink-interface.md) uygulayan nesneleri hazırlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `pDispenser`  
 Meta veri dağıtıcısının [ımetadatadağıtıserex arabirimi](../metadata/imetadatadispenserex-interface.md) işaretçisi.  
  
 `pErrorHandler`  
 [IMetaDataError arabirimi](../metadata/imetadataerror-interface.md) işaretçisi isteğe bağlı bir hata işleme arabirimine.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
