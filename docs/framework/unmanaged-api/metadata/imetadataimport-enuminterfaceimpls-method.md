---
title: IMetaDataImport::EnumInterfaceImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c94960478e6b2eb4e7b8f1e9592b0831af3ec686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603774"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls Yöntemi
Arabirim uygulamalarına temsil eden MethodDef belirteçleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi.  
  
 `td`  
 [in] Arabirim uygulamaları gösteren, MethodDef sıralanması belirteçleridir TypeDef belirteç.  
  
 `rImpls`  
 [out] Dizi MethodDef simgeleri depolamak için kullanılır.  
  
 `cMax`  
 [in] En büyük boyutunu `rImpls` dizisi.  
  
 `pcImpls`  
 [out] Döndürülen belirteç gerçek sayısını `rImpls`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir MethodDef belirteçleri vardır. Bu durumda, `pcImpls` sıfır olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
