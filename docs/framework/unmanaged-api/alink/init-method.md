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
ms.openlocfilehash: 25a1c29ab94a785304b83d5b1bcb2d7176742a68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726025"
---
# <a name="init-method"></a>Init Yöntemi

Kullanım için [IALink arabirimini](ialink-interface.md) uygulayan nesneleri hazırlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
