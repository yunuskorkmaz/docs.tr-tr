---
title: "IMetaDataImport::ResolveTypeRef Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64a783297b27c9d1400670eecb7dfe4cb69c2b96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef Yöntemi
Çözümler bir <xref:System.Type> belirtilen TypeRef belirteç tarafından temsil edilen başvuru.  
  
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
 [in] Başvurulan tür bilgileri döndürmek için TypeRef meta veri simgesi.  
  
 `riid`  
 [in] Döndürmek için IID arabiriminin `ppIScope`. Genellikle, bu IID_IMetaDataImport olacaktır.  
  
 `ppIScope`  
 [out] Başvurulan türünün tanımlandığı modül kapsamı için bir arabirim.  
  
 `ptd`  
 [out] Başvurulan tür temsil eden bir TypeDef belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Birden çok uygulama etki alanları yüklerse, bu yöntem kullanmayın. Yöntemi, uygulama etki alanı sınırları uymaz. Derleme birden fazla sürümünü yüklenir ve aynı ad ile aynı türde içerdikleri, bulduğu ilk türü modül kapsamı yöntemi döndürür.  
  
 `ResolveTypeRef` Diğer modüller tür tanımında yöntemi arar. Tür tanımı bulunursa, `ResolveTypeRef` TypeDef Belirtecin türü için yanı sıra, modül kapsamı için bir arabirim döndürür.  
  
 Türü başvurusu çözümlenemedi AssemblyRef, çözümleme kapsamını varsa `ResolveTypeRef` yöntemi çağrıları ya da ile zaten açılmış olan meta veri kapsamları eşleşmeye arar [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)yöntemi veya [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi. Bunun nedeni, `ResolveTypeRef` yalnızca diskte veya genel derleme önbelleğinde derleme depolandığı AssemblyRef kapsamdan belirleyemiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
