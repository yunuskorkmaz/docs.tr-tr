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
ms.openlocfilehash: 458a90bc47711d9f831805faa8468a49f3e0d305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704009"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps Metodu

Belirtilen FieldDef belirtecinin başvurduğu alanla ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki İlişkili meta verileri almak için alanı temsil eden bir FieldDef belirteci.  
  
 `pClass`  
 dışı Bir TypeDef belirtecinin, alanın ait olduğu sınıfın türünü temsil eden bir işaretçisi.  
  
 `szField`  
 dışı Alanın adı.  
  
 `cchField`  
 'ndaki *SzField* arabelleğinin geniş karakterdeki boyutu.  
  
 `pchField`  
 dışı Döndürülen arabelleğin gerçek boyutu.  
  
 `pdwAttr`  
 dışı Alanın meta verileriyle ilişkili bayraklar.  
  
 `ppvSigBlob`  
 'ndaki Alanı açıklayan ikili meta veri değerine yönelik bir işaretçi.  
  
 `pcbSigBlob`  
 dışı Bayt cinsinden boyut `ppvSigBlob` .  
  
 `pdwCPlusTypeFlag`  
 dışı Alanın değer türünü belirten bayrak.  
  
 `ppValue`  
 dışı Alan için sabit bir değer.  
  
 `pcchValue`  
 dışı Herhangi bir dize yoksa, karakter cinsinden boyut `ppValue` veya sıfır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
