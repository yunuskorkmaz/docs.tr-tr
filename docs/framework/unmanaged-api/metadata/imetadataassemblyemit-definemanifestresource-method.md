---
title: "IMetaDataAssemblyEmit::DefineManifestResource Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineManifestResource
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a435c946e13950faad7545e3da78ce373ee7fa0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szName`  
 [in] Kaynağın adı.  
  
 `tkImplementation`  
 [in] Meta veri simgesi türü `mdtFile` veya `mdtAssemblyRef` kaynak sağlayıcıya eşler. Bir NULL değer, meta veriler katıştırılmış dosya kaynak sağlayıcısı olarak gösterir.  
  
 `dwOffset`  
 [in] Dosyası içinde kaynak başına uzaklığı. Tek başına dosyalarında kaynaklar için bu her zaman sıfır olacak. PE (taşınabilir yürütülebilir) dosyasında katıştırılmış kaynak, kaynak cor.h üstbilgi dosyasında belirtilen konumda başlatır BLOB uzaklığı budur.  
  
 `dwResourceFlags`  
 [in] Kaynak tanımı için özellik ayarlarını belirtin bayrağı değerlerin Bitsel bir birleşimi.  
  
 `pmdmr`  
 [out] Döndürülen meta veri simgesi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ManifestResource` meta veri yapısı, her derlemenin dosyaları uygulanan her bir kaynak için tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
