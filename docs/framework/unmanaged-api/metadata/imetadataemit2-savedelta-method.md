---
title: IMetaDataEmit2::SaveDelta Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: ab2f30c485a755d4788926c13c2608e55a716c5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704272"
---
# <a name="imetadataemit2savedelta-method"></a>IMetaDataEmit2::SaveDelta Yöntemi

Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szFile`  
 'ndaki Değişikliklerin kaydedileceği dosya adı.  
  
 `dwSaveFlags`  
 'ndaki Ayrılamadı. Sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
