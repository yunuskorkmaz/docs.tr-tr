---
title: "IMetaDataImport::EnumUnresolvedMethods Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4e77453fc11b77b602d4a89f0d90540c06b0a08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods Yöntemi
Geçerli meta veri kapsamında çözümlenmemiş yöntemleri temsil eden MemberDef belirteçleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde out] Numaralayıcı gösteren bir işaretçi. Bu, bu yöntem ilk çağrısı için NULL olmalıdır.  
  
 `rMethods`  
 [out] MemberDef belirteçleri depolamak için kullanılan dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu `rMethods` dizi.  
  
 `pcTokens`  
 [out] Döndürülen MemberDef belirteçleri sayısı `rMethods`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods`başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir belirteçleri vardır. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çözümlenmemiş yöntemi bildirildi, ancak uygulanmadı biridir. Yöntem işaretlenmişse bir yöntemi numaralandırmada dahil `miForwardRef` ve her iki `mdPinvokeImpl` veya `miRuntime` sıfır olarak ayarlanır. Diğer bir deyişle, bir çözümlenmemiş yöntemi olarak işaretlenmiş bir sınıf yöntemdir `miForwardRef` ancak hangi değil (PInvoke ulaşıldı) yönetilmeyen kod uygulanan ve çalışma tarafından dahili olarak uygulanmadı  
  
 Numaralandırma modül kapsamındaki (globals) ya da arabirimleri veya soyut sınıflar tanımlanmış tüm yöntemleri dışlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
