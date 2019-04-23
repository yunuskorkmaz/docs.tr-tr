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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 534afdd5990435c6b4db5ef8ea27a8065b199496
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183605"
---
# <a name="imetadataemitsetmethodprops-method"></a>IMetaDataEmit::SetMethodProps Yöntemi
Ayarlar veya belirtilen göreli sanal adres, bir yöntemin çağrıda tarafından tanımlanan depolandığı özellik güncelleştirmelerinin [Imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `md`  
 [in] Değiştirilecek yöntemi için belirteç.  
  
 `dwMethodFlags`  
 [in] Üye öznitelikleri.  
  
 `ulCodeRVA`  
 [in] Kod adresi.  
  
 `dwImplFlags`  
 [in] Yöntemi için uygulama bayrakları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
