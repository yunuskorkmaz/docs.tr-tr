---
title: IMetaDataImport::EnumMemberRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08577f15a6fab0e630d40032a23c273ee935faa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992335"
---
# <a name="imetadataimportenummemberrefs-method"></a>IMetaDataImport::EnumMemberRefs Yöntemi
Belirtilen türün üyelerini temsil eden MemberRef belirteçleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi.  
  
 `tkParent`  
 [in] Numaralandırılacak üyeleri olan türü için bir TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.  
  
 `rMemberRefs`  
 [out] Dizi MemberRef belirteçlerini depolamak için kullanılır.  
  
 `cMax`  
 [in] En büyük boyutunu `rMemberRefs` dizisi.  
  
 `pcTokens`  
 [out] Döndürülen MemberRef belirteçleri gerçek sayısını `rMemberRefs`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMemberRefs` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir MemberRef belirteçleri vardır. Bu durumda, `pcTokens` için sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
