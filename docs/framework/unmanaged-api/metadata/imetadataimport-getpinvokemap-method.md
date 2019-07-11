---
title: IMetaDataImport::GetPinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1be6079ed382b8ab27d0aec16bd725f5c5b9cb5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778896"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap Yöntemi
Bir ModuleRef PInvoke çağrısına hedef derleme temsil etmek için belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [in] PInvoke eşleme meta verilerini almak için fieldDef simgesi veya MethodDef belirteci.  
  
 `pdwMappingFlags`  
 [out] Eşleme için kullanılan bayraklar işaretçisi. Gelen bir bit maskesi değerdir [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) sabit listesi.  
  
 `szImportName`  
 [out] Yönetilmeyen DLL hedef adı.  
  
 `cchImportName`  
 [in] Geniş karakter cinsinden boyutu `szImportName`.  
  
 `pchImportName`  
 [out] Döndürülen geniş karakter sayısını `szImportName`.  
  
 `pmrImportDLL`  
 [out] Yönetilmeyen hedef nesne kitaplığı temsil eden bir ModuleRef belirteci için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
