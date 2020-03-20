---
title: IMetaDataImport::GetFieldProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177242"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps Metodu
Belirtilen FieldDef belirteci tarafından başvurulan alanla ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 [içinde] İlişkili meta verileri almak için alanı temsil eden bir FieldDef belirteci.  
  
 `pClass`  
 [çıkış] Alanın ait olduğu sınıfın türünü temsil eden bir TypeDef belirteci.  
  
 `szField`  
 [çıkış] Alanın adı.  
  
 `cchField`  
 [içinde] *szField*için arabellek geniş karakterler boyutu.  
  
 `pchField`  
 [çıkış] Döndürülen arabelleğe gerçek boyutu.  
  
 `pdwAttr`  
 [çıkış] Alanın meta verileriyle ilişkili bayraklar.  
  
 `ppvSigBlob`  
 [içinde] Alanı açıklayan ikili meta veri değeri için bir işaretçi.  
  
 `pcbSigBlob`  
 [çıkış] `ppvSigBlob`Baytboyutu.  
  
 `pdwCPlusTypeFlag`  
 [çıkış] Alanın değer türünü belirten bir bayrak.  
  
 `ppValue`  
 [çıkış] Alan için sabit bir değer.  
  
 `pcchValue`  
 [çıkış] Karakterdeki boyut `ppValue`, veya dize yoksa sıfır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
