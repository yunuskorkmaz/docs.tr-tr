---
title: "IMetaDataImport::EnumMethodSemantics Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d5ec79701f73b8beb7759d72b972fc347a339c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics Yöntemi
Özellikleri ve belirtilen yöntem ilgili özellik değişikliği olayları numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde out] Numaralayıcı gösteren bir işaretçi. Bu, bu yöntem ilk çağrısı için NULL olmalıdır.  
  
 `mb`  
 [in] Numaralandırma kapsamını sınırlar MethodDef belirteci.  
  
 `rEventProp`  
 [out] Özellikleri ve olayları depolamak için kullanılan dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu `rEventProp` dizi.  
  
 `pcEventProp`  
 [out] Olay veya döndürülen özellikleri sayısı `rEventProp`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`başarıyla döndürüldü.|  
|`S_FALSE`|Olayları veya Numaralandırılacak özellikleri yok. Bu durumda, `pcEventProp` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Birçok ortak dil çalışma zamanı türleri tanımlama *özelliği* `Changed` olayları ve `On` *özelliği* `Changed` ilgili özellikleri için yöntemleri. Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türünü tanımlayan bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemi. Ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> özelliği çağrıları <xref:System.Windows.Forms.Control.OnFontChanged%2A> sırayla başlatır yöntemi <xref:System.Windows.Forms.Control.FontChanged> olay. Çağrısıyla sonlandırmalısınız `EnumMethodSemantics` için MethodDef kullanarak <xref:System.Windows.Forms.Control.OnFontChanged%2A> başvurularını almak için <xref:System.Windows.Forms.Control.Font%2A> özelliği ve <xref:System.Windows.Forms.Control.FontChanged> olay.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
