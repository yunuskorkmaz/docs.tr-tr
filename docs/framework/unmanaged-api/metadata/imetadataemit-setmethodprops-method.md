---
title: IMetaDataEmit::SetMethodProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: 57f6de1f7edf7c75a3f96cb2bf9fb98fdbd6f65e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007864"
---
# <a name="imetadataemitsetmethodprops-method"></a>IMetaDataEmit::SetMethodProps Yöntemi
[Imetadatayayma::D efineMethod](imetadataemit-definemethod-method.md)için önceki bir çağrı tarafından tanımlanan bir yöntemin belirtilen göreli sanal adresinde depolanan özelliği ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `md`  
 'ndaki Değiştirilecek metodun belirteci.  
  
 `dwMethodFlags`  
 'ndaki Üye öznitelikleri.  
  
 `ulCodeRVA`  
 'ndaki Kodun adresi.  
  
 `dwImplFlags`  
 'ndaki Yöntemi için uygulama bayrakları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
