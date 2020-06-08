---
title: IMetaDataImport::GetMemberProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503646"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps Metodu
Belirtilen <xref:System.Type> meta veri belirtecinin başvurduğu üyenin adı, ikili imzası ve göreli sanal adresi de dahil olmak üzere, belirtilen üye tanımı için meta verilerde depolanan bilgileri alır. Bu basit bir yardımcı yöntemdir: *MB* bir MethodDef Ise **GetMethodProps** çağrılır; *MB* bir fieldDef Ise, **GetFieldProps** çağırılır. Ayrıntılar için diğer yöntemlere bakın.
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 'ndaki İlişkili meta verileri almak için üyeye başvuran belirteç.  
  
 `pClass`  
 dışı Üyenin sınıfını temsil eden meta veri belirtecinin işaretçisi.  
  
 `szMember`  
 dışı Üyenin adı.  
  
 `cchMember`  
 'ndaki Arabelleğin geniş karakterdeki boyutu `szMember` .  
  
 `pchMember`  
 dışı Döndürülen adın geniş karakterdeki boyutu.  
  
 `pdwAttr`  
 dışı Üyeye uygulanan bayrak değerleri.  
  
 `ppvSigBlob`  
 dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.  
  
 `pcbSigBlob`  
 dışı Bayt cinsinden boyut `ppvSigBlob` .  
  
 `pulCodeRVA`  
 dışı Üyenin göreli sanal adresine yönelik bir işaretçi.  
  
 `pdwImplFlags`  
 dışı Üyeyle ilişkili herhangi bir yöntem uygulama bayrağı.  
  
 `pdwCPlusTypeFlag`  
 dışı Bir işareti olan bayrak <xref:System.ValueType> . Bu `ELEMENT_TYPE_*` değerlerden biridir.
  
 `ppValue`  
 dışı Bu üye tarafından döndürülen sabit dize değeri.  
  
 `pcchValue`  
 dışı Karakter cinsinden boyut `ppValue` veya dize yoksa sıfır `ppValue` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
