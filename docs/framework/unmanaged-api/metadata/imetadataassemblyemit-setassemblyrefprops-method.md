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
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008098"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi
Belirtilen `AssemblyRef` meta veri yapısını değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `AssemblyRef`Değiştirilecek meta veri yapısını belirten meta veri belirteci.  
  
 `pbPublicKeyOrToken`  
 'ndaki Başvurulan derlemenin yayımcısının ortak anahtarı.  
  
 `cbPublicKeyOrToken`  
 'ndaki Bayt cinsinden boyut `pbPublicKeyOrToken` .  
  
 `szName`  
 'ndaki Derlemenin insanların okunabilir metin adı.  
  
 `pMetaData`  
 'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneğine yönelik bir işaretçi.  
  
 `pbHashValue`  
 'ndaki Derlemeyle ilişkili karma verileri işaretçisi.  
  
 `cbHashValue`  
 'ndaki Bayt cinsinden boyut `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 'ndaki Başvurulan derlemenin özniteliklerini belirten, [AssemblyRefFlags](assemblyrefflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `AssemblyRef`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
