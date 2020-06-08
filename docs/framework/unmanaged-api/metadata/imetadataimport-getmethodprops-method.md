---
title: IMetaDataImport::GetMethodProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 3c7c3525f2f8753241c9a206e4cf5e552bf06efe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503633"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps Yöntemi
Belirtilen MethodDef belirtecinin başvurduğu metotla ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mb`  
 'ndaki Meta verilerini döndürecek yöntemi temsil eden MethodDef belirteci.  
  
 `pClass`  
 dışı Yöntemi uygulayan türü temsil eden bir TypeDef belirtecinin Işaretçisi.  
  
 `szMethod`  
 dışı Metodun adına sahip bir arabelleğin Işaretçisi.  
  
 `cchMethod`  
 'ndaki İstenen boyutu `szMethod` .  
  
 `pchMethod`  
 dışı Geniş karakterdeki boyut Işaretçisi `szMethod` veya kesme durumunda, yöntem adındaki geniş karakterlerin gerçek sayısı.  
  
 `pdwAttr`  
 dışı Yöntemiyle ilişkili bayrakların bir işaretçisi.  
  
 `ppvSigBlob`  
 dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.  
  
 `pcbSigBlob`  
 dışı Bayt cinsinden boyut Işaretçisi `ppvSigBlob` .  
  
 `pulCodeRVA`  
 dışı Metodun göreli sanal adresine yönelik bir işaretçi.  
  
 `pdwImplFlags`  
 dışı Yöntemi için herhangi bir uygulama bayraklarının bir işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
