---
title: IMetaDataAssemblyImport::GetAssemblyRefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76ae1d81db314530ab33a42cb99824da1745dff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps Metodu
Belirtilen meta veri imzayla derleme başvurusu için özellikler kümesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mdar`  
 [in] `mdAssemblyRef` Özellikleri almak istediğiniz derleme başvurusunu gösteren meta veri simgesi.  
  
 `ppbPublicKeyOrToken`  
 [out] Ortak anahtar veya meta veri simgesi için bir işaretçi.  
  
 `pcbPublicKeyOrToken`  
 [out] Döndürülen bir ortak anahtar ya da belirteci bayt sayısı.  
  
 `szName`  
 [out] Derleme basit adı.  
  
 `cchName`  
 [in] Geniş karakter boyutu, `szName`.  
  
 `pchName`  
 [out] Gerçekte döndürülen geniş karakter sayısını gösteren bir işaretçi `szName`.  
  
 `pMetaData`  
 [out] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısı için bir işaretçi.  
  
 `ppbHashValue`  
 [out] Karma değer için bir işaretçi. SHA-1 algoritmasını kullanan karma budur `PublicKey` arfFullOriginator bayrak sürece, başvurulan derleme özelliğinin [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) numaralandırma ayarlanır.  
  
 `pcbHashValue`  
 [out] Döndürülen karma değeri geniş karakter sayısı.  
  
 `pdwAssemblyRefFlags`  
 [out] Bir derlemeye uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi. Bir veya birden çok bayrak değeri birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem başarılı olursa S_OK döndürür; Aksi takdirde, bu Winerror.h'de üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
