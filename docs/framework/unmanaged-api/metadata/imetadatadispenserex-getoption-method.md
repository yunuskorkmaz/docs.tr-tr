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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8717a1eafebf24366c35848dbe285943c107ed51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777725"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption Yöntemi
Geçerli meta veri kapsam için belirtilen seçenek değerini alır. Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `optionId`  
 [in] Alınacak seçeneğini belirten bir GUID için bir işaretçi. Desteklenen GUID'lerinin listesi için Açıklamalar bölümüne bakın.  
  
 `pValue`  
 [out] Döndürülen seçeneği değeri. Bu değerin türü, belirtilen seçeneğin türünde bir değişken olacaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki liste, bu yöntem için desteklenen GUID'leri gösterir. Açıklamaları için bkz. [Imetadatadispenserex::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) yöntemi. Varsa `optionId` olduğundan bu listede değil, bu yöntem HRESULT döndürür. `E_INVALIDARG`, hatalı bir parametre belirten.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
