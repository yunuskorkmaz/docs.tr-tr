---
title: IMetaDataEmit2::GetDeltaSaveSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493116"
---
# <a name="imetadataemit2getdeltasavesize-method"></a>IMetaDataEmit2::GetDeltaSaveSize Metodu
Geçerli Düzenle ve devam et oturumunun sonucu olan meta veri boyutundaki herhangi bir değişikliği gösteren bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fSave`  
 'ndaki [CorSaveSize](corsavesize-enumeration.md) değerlerinden biri, istenen duyarlık düzeyini gösterir. .NET Framework sürüm 2,0 için, bu parametre yok sayılır.  
  
 `pdwSaveSize`  
 dışı Meta verilerin boyutundaki değişiklik.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
