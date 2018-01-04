---
title: "IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aab505700b669cae071420117abd71332f49d8b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi
Belirtilen değiştirir `Assembly` meta veri yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pma`  
 [in] Belirtir meta veri simgesi `Assembly` değiştirilecek meta veri yapısı.  
  
 `pbPublicKey`  
 [in] Derleme publisher'ın ortak anahtar için bir işaretçi.  
  
 `cbPublicKey`  
 [in] Bayt cinsinden boyutu `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] Derleme dosyalarını karması için kullanılan karma algoritma tanımlayıcısı.  
  
 `szName`  
 [in] Derleme okunabilir metni adı.  
  
 `pMetaData`  
 [in] Derleme sürümü, platform ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA gösteren bir işaretçi.  
  
 `dwAssemblyFlags`  
 [in] Bit düzeyinde bileşimini [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) derlemenin çeşitli öznitelikler belirten değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Oluşturmak için bir `Assembly` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
