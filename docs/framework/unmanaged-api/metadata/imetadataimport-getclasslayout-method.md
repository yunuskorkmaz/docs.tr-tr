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
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175414"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout Metodu
Belirtilen TypeDef belirteci tarafından başvurulan sınıfın düzen bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [içinde] Döndürülecek düzene sahip sınıfın TypeDef belirteci.  
  
 `pdwPackSize`  
 [çıkış] Sınıfın paket boyutunu temsil eden 1, 2, 4, 8 veya 16 değerlerinden biri.  
  
 `rFieldOffset`  
 [çıkış] [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) değerleri dizisi.  
  
 `cMax`  
 [içinde] `rFieldOffset` Dizinin en büyük boyutu.  
  
 `pcFieldOffset`  
 [çıkış] Döndürülen öğe `rFieldOffset`sayısı.  
  
 `pulClassSize`  
 [çıkış] Sınıfın baytboyutu tarafından `td`temsil edilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
