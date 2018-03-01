---
title: IMetaDataAssemblyImport::GetFileProps Metodu
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
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55984c4adaf291e3b962514cdc3bea964d1c91bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps Metodu
Belirtilen meta veri imzayla dosyasının özelliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mdf`  
 [in] `mdFile` Özellikleri almak istediğiniz dosyayı temsil eden meta veri simgesi.  
  
 `szName`  
 [out] Dosyanın basit adı.  
  
 `cchName`  
 [in] Geniş karakter boyutu, `szName`.  
  
 `pchName`  
 [out] Gerçekte döndürülen geniş karakter sayısı `szName`.  
  
 `ppbHashValue`  
 [out] Karma değer için bir işaretçi. Dosyanın SHA-1 algoritmasını kullanarak karma budur.  
  
 `pcbHashValue`  
 [out] Döndürülen karma değeri geniş karakter sayısı.  
  
 `pdwFileFlags`  
 [out] Bir dosyaya uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi. Bir veya birden çok bayrak değeri birleşimidir [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
