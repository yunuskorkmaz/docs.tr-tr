---
title: IMetaDataImport2::GetPEKind Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c938ef8783a122dec2a5f5bd3775661d68fba62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449409"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind Metodu
Alır taşınabilir yürütülebilir (PE) kodda yapısını tanımlayan bir değer, geçerli meta veri kapsamda tanımlanan genellikle bir DLL veya EXE dosyası dosyasında.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwPEKind`  
 [out] Değerini gösteren bir işaretçi [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) PE dosya tanımlar numaralandırması.  
  
 `pdwMachine`  
 [out] Makine mimarisi tanımlayan bir değer için bir işaretçi. Olası değerler için sonraki bölüme bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından başvurulan değer `pdwMachine` parametresi şunlardan biri olabilir.  
  
|Değer|Makine mimarisi|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel IPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|X64|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [CorPEKind Sabit Listesi](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
