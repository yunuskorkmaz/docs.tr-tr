---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: Getpınvokemap yöntemi'
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
ms.openlocfilehash: fcf45f4741709423aa48dcf895dfc4be276e19fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649448"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap Yöntemi

Bir PInvoke çağrısının hedef derlemesini temsil eden bir ModuleRef belirteci alır.  
  
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
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
