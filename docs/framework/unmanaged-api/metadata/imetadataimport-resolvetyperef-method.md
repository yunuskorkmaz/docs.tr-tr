---
title: IMetaDataImport::ResolveTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c69c67c5c9d996bd746d82ea86caf4a396c0b10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625243"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef Yöntemi
Çözümlenen bir <xref:System.Type> belirtilen TypeRef belirteci tarafından temsil edilen bir başvuru.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tr`  
 [in] Başvurulan tür bilgilerini döndürmek için TypeRef meta veri belirteci.  
  
 `riid`  
 [in] Döndürmek için bir IID arabirimi `ppIScope`. Genelde bu IID_IMetaDataImport olacaktır.  
  
 `ppIScope`  
 [out] Başvurulan tür tanımlandığı modül kapsamı için bir arabirim.  
  
 `ptd`  
 [out] Başvurulan tür temsil eden bir tür tanımı belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Birden çok uygulama etki alanları yüklerse, bu yöntemi kullanmayın. Yöntemi, uygulama etki alanı sınırları uymaz. Bir derlemenin birden çok sürümü yüklü olan ve aynı ad ile aynı türde içerdikleri bulduğu ilk türünde modül kapsamı yöntemi döndürür.  
  
 `ResolveTypeRef` Diğer modül türü tanımında yöntemi arar. Tür tanımını bulunursa `ResolveTypeRef` TypeDef belirteç türünün yanı sıra, bu modül kapsamı için bir arabirim döndürür.  
  
 Tür başvurusu çözümlenemedi için AssemblyRef, çözüm kapsamını varsa `ResolveTypeRef` yöntemi çağrılarıyla ya da zaten açılmış olan meta veri kapsamlardaki bir eşleşme arar [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)yöntemi veya [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi. Bunun nedeni, `ResolveTypeRef` yalnızca diskte veya genel derleme önbelleğinde derleme depolandığı AssemblyRef kapsamından belirlenemiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
