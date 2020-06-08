---
title: IMetaDataTables::GetBlob Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: ff97e419c5309fa7cb820cb7e82db96fee34f30c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501280"
---
# <a name="imetadatatablesgetblob-method"></a>IMetaDataTables::GetBlob Metodu
Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ixBlob`  
 'ndaki Alınacak bellek adresi `ppData` .  
  
 `pcbData`  
 dışı Boyutu için bayt cinsinden bir işaretçi `ppData` .  
  
 `ppData`  
 dışı Alınan ikili verilerin işaretçisine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
