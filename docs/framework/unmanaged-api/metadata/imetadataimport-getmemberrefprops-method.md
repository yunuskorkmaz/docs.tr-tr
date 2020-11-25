---
title: IMetaDataImport::GetMemberRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: 3237b67f8f711e9ef213d6fc66f1513c534fbdeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733210"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps Yöntemi

Belirtilen belirteç tarafından başvurulan üyeyle ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,
   [out] mdToken           *ptk,
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pbSig
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `mr`  
 'ndaki İçin ilişkili meta verileri döndürecek MemberRef belirteci.  
  
 `ptk`  
 dışı Üyeyi bildiren sınıfı temsil eden bir TypeDef veya TypeRef, ya da üyeyi bildiren modül sınıfını temsil eden bir ModuleRef belirteci ya da üyeyi temsil eden bir MethodDef.  
  
 `szMember`  
 dışı Üyenin adı için bir dize arabelleği.  
  
 `cchMember`  
 'ndaki Geniş karakterdeki istenen boyut `szMember` .  
  
 `pchMember`  
 dışı Geniş karakter olarak döndürülen boyut `szMember` .  
  
 `ppvSibBlob`  
 dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.  
  
 `pbSig`  
 dışı Bayt cinsinden boyut `ppvSigBlob` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
