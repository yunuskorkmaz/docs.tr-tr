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
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176051"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi
Belirtilen `AssemblyRef` meta veri yapısını değiştirir.  
  
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
 [içinde] Değiştirilecek `AssemblyRef` meta veri yapısını belirten meta veri belirteci.  
  
 `pbPublicKeyOrToken`  
 [içinde] Başvurulan derlemenin yayımcısının ortak anahtarı.  
  
 `cbPublicKeyOrToken`  
 [içinde] `pbPublicKeyOrToken`Baytboyutu.  
  
 `szName`  
 [içinde] Derlemenin insan tarafından okunabilen metin adı.  
  
 `pMetaData`  
 [içinde] Derlemenin sürümünü, platformlarını ve yerel bilgilerini içeren bir ASSEMBLYMETADATA örneğine işaretçi.  
  
 `pbHashValue`  
 [içinde] Derleme ile ilişkili karma verilere işaretçi.  
  
 `cbHashValue`  
 [içinde] `pbHashValue`Baytboyutu.  
  
 `dwAssemblyRefFlags`  
 [içinde] Başvurulan derlemenin özniteliklerini belirten [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) değerlerinin bityişli bir birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta `AssemblyRef` veri yapısı oluşturmak için [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
