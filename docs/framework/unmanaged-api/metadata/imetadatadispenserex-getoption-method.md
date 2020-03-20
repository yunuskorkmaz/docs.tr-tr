---
title: IMetaDataDispenserEx::GetOption Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177725"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption Yöntemi
Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır. Seçenek, geçerli meta veri kapsamına yapılan çağrıların nasıl işleneceğini denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `optionId`  
 [içinde] Alınacak seçeneği belirten bir GUID işaretçisi. Desteklenen GUID'lerin listesi için Açıklamalar bölümüne bakın.  
  
 `pValue`  
 [çıkış] Döndürülen seçeneğin değeri. Bu değerin türü, belirtilen seçeneğin türünün bir varyantı olacaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki liste, bu yöntem için desteklenen GUID'leri gösterir. Açıklamalar için [iMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) yöntemine bakın. Bu `optionId` listede yoksa, bu yöntem yanlış `E_INVALIDARG`bir parametre gösteren HRESULT döndürür.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataReftodefcheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerSeçenekleri  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
