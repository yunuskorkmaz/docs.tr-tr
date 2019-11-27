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
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447921"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 Arabirimi
Genel türlerle çalışma yeteneği sağlamak için öncelikle [ımetadatayayma](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineGenericParam Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.|  
|[DefineMethodSpec Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.|  
|[GetDeltaSaveSize Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Geçerli Düzenle ve devam et oturumunun değişikliklerini ifade etmek için gereken verilerin boyutunun farkını gösteren bir değer alır.|  
|[ResetENCLog Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Düzenle ve devam et günlüğünü sıfırlar ve yeni bir oturum başlatır.|  
|[SaveDelta Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.|  
|[SaveDeltaToMemory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.|  
|[SaveDeltaToStream Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.|  
|[SetGenericParamProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
