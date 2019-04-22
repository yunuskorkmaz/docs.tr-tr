---
title: IMetaDataEmit2 Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87b5b60d75d5d28e100ec75192d0cacf51765927
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200200"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 Arabirimi
Genişletir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) öncelikle genel türlerle çalışma olanağı sağlamak için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineGenericParam Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Genel tür parametresi için bir tanım oluşturur ve o genel tür parametresi için bir belirteç alır.|  
|[DefineMethodSpec Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Bir yöntem genel bir örneğini oluşturur ve tanımı için bir belirteç alır.|  
|[GetDeltaSaveSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Düzenle ve devam et geçerli oturum için değişiklikleri ifade etmek için gerekli olan verilerin boyutu arasındaki fark gösteren bir değer alır.|  
|[ResetENCLog Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Düzenle ve devam et günlük sıfırlar ve yeni bir oturum başlatır.|  
|[SaveDelta Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumdan belirtilen dosyaya kaydeder.|  
|[SaveDeltaToMemory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumdan bellek kaydeder.|  
|[SaveDeltaToStream Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan, belirtilen akışa kaydeder.|  
|[SetGenericParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Belirtilen belirteç tarafından başvurulan genel parametre tanımı için özellik değerlerini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
