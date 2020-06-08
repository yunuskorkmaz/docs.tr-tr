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
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493051"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 Arabirimi
Genel türlerle çalışma yeteneği sağlamak için öncelikle [ımetadatayayma](imetadataemit-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[DefineGenericParam Yöntemi](imetadataemit2-definegenericparam-method.md)|Genel tür parametresi için bir tanım oluşturur ve bu genel tür parametresine bir belirteç alır.|  
|[DefineMethodSpec Yöntemi](imetadataemit2-definemethodspec-method.md)|Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.|  
|[GetDeltaSaveSize Metodu](imetadataemit2-getdeltasavesize-method.md)|Geçerli Düzenle ve devam et oturumunun değişikliklerini ifade etmek için gereken verilerin boyutunun farkını gösteren bir değer alır.|  
|[ResetENCLog Yöntemi](imetadataemit2-resetenclog-method.md)|Düzenle ve devam et günlüğünü sıfırlar ve yeni bir oturum başlatır.|  
|[SaveDelta Yöntemi](imetadataemit2-savedelta-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.|  
|[SaveDeltaToMemory Yöntemi](imetadataemit2-savedeltatomemory-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.|  
|[SaveDeltaToStream Yöntemi](imetadataemit2-savedeltatostream-method.md)|Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.|  
|[SetGenericParamProps Yöntemi](imetadataemit2-setgenericparamprops-method.md)|Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
