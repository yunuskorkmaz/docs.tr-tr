---
title: IMetaDataImport::EnumMembers Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8d871f2ecbd96d5bda781b2ae11b94efd409442
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128407"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers Yöntemi
Belirtilen türün üyelerini temsil eden MemberDef belirteçleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi.  
  
 `cl`  
 [in] Numaralandırılacak üyeleri olan türü temsil eden bir tür tanımı belirteci.  
  
 `rMembers`  
 [out] Dizi MemberDef belirteçleri tutmak için kullanılır.  
  
 `cMax`  
 [in] En büyük boyutunu `rMembers` dizisi.  
  
 `pcTokens`  
 [out] Döndürülen MemberDef belirteçleri gerçek sayısını `rMembers`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir MemberDef belirteçleri vardır. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Koleksiyonlar bir sınıfın üyelerinin sıralanırken `EnumMembers` yalnızca üyeleri döndürür (alanlar ve yöntemler, ancak **değil** özellikleri veya olayları) doğrudan sınıf üzerinde tanımlanan. Bile sınıfı, bu devralınan üyeleri için bir uygulama sağlar sınıfını devralan herhangi bir üye döndürmez. Devralınan üyeleri listeleme için arayan açıkça devralma zincirini yol gerekir. Devralma zincirini kurallarını özgün metaverileri gereğince yayılan derleyici ve dil bağlı olarak farklılık gösterebileceğini unutmayın.
 
 Özellikler ve olaylar değil numaralandırılan tarafından `EnumMembers`. Bu listeleme için kullanın [EnumProperties](imetadataimport-enumproperties-method.md) veya [EnumEvents](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
