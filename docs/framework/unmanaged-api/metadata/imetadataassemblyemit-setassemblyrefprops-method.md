---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 984ec5dea757971081ce05c858788473a0f616e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775280"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi
Belirtilen değiştirir `AssemblyRef` meta veri yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ar`  
 [in] Belirten bir meta veri belirteci `AssemblyRef` değiştirilecek meta veri yapısı.  
  
 `pbPublicKeyOrToken`  
 [in] Başvurulan derlemenin yayımcı ortak anahtarı.  
  
 `cbPublicKeyOrToken`  
 [in] Bayt cinsinden boyutu `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Derleme kullanıcı tarafından okunabilen metin adı.  
  
 `pMetaData`  
 [in] Derleme sürümü, platforma ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA örneğine bir işaretçi.  
  
 `pbHashValue`  
 [in] Bütünleştirilmiş kod ile ilişkili veri karması için bir işaretçi.  
  
 `cbHashValue`  
 [in] Bayt cinsinden boyutu `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Bitsel bir birleşimi [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) başvurulan derleme özniteliklerini belirten değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Oluşturmak için bir `AssemblyRef` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
