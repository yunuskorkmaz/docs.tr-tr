---
title: "IMetaDataAssemblyEmit::DefineAssembly Yöntemi"
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
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly Yöntemi
Oluşturur bir `Assembly` için belirtilen derlemeyi meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbPublicKey`  
 [in] Derleme güçlü olarak adlandırılmamış, derleme ya da NULL yayımcıyı tanımlayan ortak anahtarı.  
  
 `cbPublicKey`  
 [in] Bayt cinsinden boyutu `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] Derleme veya NULL SHA-1 algoritmasını belirtmek için dosyaları şifrelemek için kullanılacak karma algoritma tanımlayıcısı.  
  
 `szName`  
 [in] Derleme okunabilir metni adı. Bu değer 1024 karakterden uzun olamaz.  
  
 `pMetaData`  
 [in] Bir işaretçi ASSEMBLYMETADATA örneğine derleme için sürüm, platform ve yerel ayar bilgilerini içerir.  
  
 `dwAssemblyFlags`  
 [in] Bir birleşimini [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) derleme özelliklerini açıklayan değerleri.  
  
 `pmda`  
 [out] Meta veri simgesi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca bir `Assembly` meta veri yapısı içinde bir bildirim tanımlanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
