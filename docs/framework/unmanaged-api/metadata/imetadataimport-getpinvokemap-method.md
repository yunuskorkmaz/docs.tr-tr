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
ms.openlocfilehash: 8409e56b5ec4dbe47035a0555b6b7ce175b517ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490984"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap Yöntemi
Bir PInvoke çağrısının hedef derlemesini temsil eden bir ModuleRef belirteci alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki İçin PInvoke eşleme meta verilerini almak için FieldDef veya MethodDef belirteci.  
  
 `pdwMappingFlags`  
 dışı Eşleme için kullanılan bayrakların işaretçisi. Bu değer, [Corpınvokemap](corpinvokemap-enumeration.md) numaralandırmasındaki bir bit dır.  
  
 `szImportName`  
 dışı Yönetilmeyen hedef DLL 'in adı.  
  
 `cchImportName`  
 'ndaki Öğesinin geniş karakterdeki boyutu `szImportName` .  
  
 `pchImportName`  
 dışı İçinde döndürülen geniş karakter sayısı `szImportName` .  
  
 `pmrImportDLL`  
 dışı Yönetilmeyen hedef nesne kitaplığını temsil eden bir ModuleRef belirtecinin işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
