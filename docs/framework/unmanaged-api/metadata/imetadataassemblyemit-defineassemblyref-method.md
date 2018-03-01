---
title: "IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi"
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
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 123bd37d189477eade72e3b0e74f923fecce57a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi
Oluşturur bir `AssemblyRef` Bu bütünleştirilmiş koduna başvuruyor, derleme için meta verileri içeren yapısını ve ilişkili meta veri simgesi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbPublicKeyOrToken`  
 [in] Başvurulan derlemeyi yayımcısı ortak anahtarı. Yardımcı işlevini [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) Bu parametre olarak geçirmek için ortak anahtar karma almak için kullanılabilir.  
  
 `cbPublicKeyOrToken`  
 [in] Bayt cinsinden boyutu `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Derleme okunabilir metni adı. Bu değer 1024 karakterden uzun olamaz.  
  
 `pMetaData`  
 [in] Başvurulan derlemeyi sürümü, platform ve yerel ayar bilgileri içeren bir ASSEMBLYMETADATA örneği.  
  
 `pbHashValue`  
 [in] Başvurulan derlemesiyle ilişkilendirilmiş veri karması. İsteğe bağlı.  
  
 `cbHashValue`  
 [in] Bayt cinsinden boyutu `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Bit düzeyinde bileşimini [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) yürütme altyapısı davranışını etkilemek değerleri.  
  
 `pmdar`  
 [out] Bir işaretçi döndürülen `AssemblyRef` meta veri simgesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `AssemblyRef` meta veri yapısı bu derlemeye başvuran her derlemesi için tanımlanmalıdır.  
  
 Çalışma zamanında "yerleşik haliyle" bilgi temsil ettiğini bir göstergesi ile derleme çözümleyiciye başvurulan bir derleme ayrıntılarını geçirilir. Derleme Çözümleyicisi sonra ilke uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
