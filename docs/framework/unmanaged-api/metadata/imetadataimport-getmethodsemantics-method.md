---
title: IMetaDataImport::GetMethodSemantics Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437451"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics Metodu
Belirtilen MethodDef belirtecinin başvurduğu yöntem ile eşleştirilen özellik ve belirtilen EventProp belirteci tarafından başvurulan olay arasındaki ilişkiyi belirten bayrakları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 'ndaki İçin anlamsal rol bilgilerini almak üzere yöntemini temsil eden bir MethodDef belirteci.  
  
 `tkEventProp`  
 'ndaki Yöntemin rolünün alınacağı eşleştirilmiş özelliği ve olayı temsil eden bir belirteç.  
  
 `pdwSemanticsFlags`  
 dışı İlişkili anlambilim bayraklarının işaretçisi. Bu değer [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) numaralandırmasındaki bir bit dır.  
  
## <a name="remarks"></a>Açıklamalar  
 [Imetadatayayma::D efineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) yöntemi, yöntemin anlambilim bayraklarını ayarlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
