---
title: IMetaDataImport::GetClassLayout Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52136426be9e8f220d8eb5fc93659f588f007498
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625126"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout Metodu
Belirtilen tür tanımı tarafından başvurulan sınıfın düzen bilgilerini belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Döndürülecek düzeni ile sınıf için TypeDef simgesi.  
  
 `pdwPackSize`  
 [out] 1, 2, 4, 8 veya 16, sınıf paketi boyutunu temsil eden değerlerinden biri.  
  
 `rFieldOffset`  
 [out] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) değerleri.  
  
 `cMax`  
 [in] En büyük boyutunu `rFieldOffset` dizisi.  
  
 `pcFieldOffset`  
 [out] Döndürülen öğe sayısını `rFieldOffset`.  
  
 `pulClassSize`  
 [out] Tarafından temsil edilen sınıf bayt cinsinden boyut `td`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
