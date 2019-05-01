---
title: IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba99d84686974b425bcdee0bbf4770e4843e1351
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992582"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
Belirtilen meta veri imzası bildirim kaynak özelliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdmr`  
 [in] Bir `mdManifestResource` özelliklerini alınacağı kaynak temsil eden belirteci.  
  
 `szName`  
 [out] Kaynak adı.  
  
 `cchName`  
 [in] Geniş karakter, boyutunu, `szName`.  
  
 `pchName`  
 [out] Gerçekte döndürülen geniş karakter sayısı için bir işaretçi `szName`.  
  
 `ptkImplementation`  
 [out] Bir işaretçi bir `mdFile` belirteç veya `mdAssemblyRef` içeren kaynak dosya veya derleme, sırasıyla temsil eden belirteç.  
  
 `pdwOffset`  
 [out] Kaynak dosyası içinde başlangıcına uzaklık belirten bir değer için bir işaretçi.  
  
 `pdwResourceFlags`  
 [out] Bir kaynağa uygulanan meta verileri açıklayan bayrakları için bir işaretçi. Bir veya daha fazla flags değeri birleşimidir [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
