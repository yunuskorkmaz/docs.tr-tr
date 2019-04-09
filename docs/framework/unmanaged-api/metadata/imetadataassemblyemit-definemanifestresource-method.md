---
title: IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186725"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapı ve ilişkili meta veri belirteci döndürür.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `szName`  
 [in] Kaynak adı.  
  
 `tkImplementation`  
 [in] Türü bir meta veri belirteci `mdtFile` veya `mdtAssemblyRef` kaynak sağlayıcıya eşler. Bir NULL değer, dosyanın meta verileri, katıştırılmış kaynak sağlayıcısı olduğunu gösterir.  
  
 `dwOffset`  
 [in] Kaynak dosyası içinde başlangıcına uzaklık. Tek başına dosyalarındaki kaynaklar için bu her zaman sıfır olacaktır. Bir PE (taşınabilir çalıştırılabilir) dosyasında katıştırılmış kaynak, bir uzaklık cor.h üstbilgi dosyasında belirtilen konumda başlatan BLOB kaynağının budur.  
  
 `dwResourceFlags`  
 [in] Kaynak tanımı özellik ayarlarını belirten bayrağı değerlerinin Bitsel bir birleşimi.  
  
 `pmdmr`  
 [out] Döndürülen meta veri belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ManifestResource` meta veri yapısı, her derlemenin dosyalarının uygulanan her bir kaynak için tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
