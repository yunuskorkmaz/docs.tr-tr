---
title: IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3361212f9a7f7ff0739e8544419a2b67abc8f457
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214656"
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
  
## <a name="parameters"></a>Parametreler  
 `pma`  
 [in] Belirten bir meta veri belirteci `Assembly` değiştirilecek meta veri yapısı.  
  
 `pbPublicKey`  
 [in] Derlemenin yayımcı ortak anahtarı için bir işaretçi.  
  
 `cbPublicKey`  
 [in] Bayt cinsinden boyutu `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] Derleme dosyalarını karması için kullanılan karma algoritması için tanımlayıcı.  
  
 `szName`  
 [in] Derleme kullanıcı tarafından okunabilen metin adı.  
  
 `pMetaData`  
 [in] Derleme sürümü, platforma ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA işaretçisi.  
  
 `dwAssemblyFlags`  
 [in] Bitsel bir birleşimi [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) derleme çeşitli özniteliklerini belirten değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Oluşturmak için bir `Assembly` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
