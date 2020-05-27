---
title: IMetaDataAssemblyEmit::DefineAssembly Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008189"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly Yöntemi
`Assembly`Belirtilen derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `pbPublicKey`  
 'ndaki Derlemenin yayımcısını tanımlayan ortak anahtar veya derleme kesin olarak adlandırılmamışsa NULL.  
  
 `cbPublicKey`  
 'ndaki Bayt cinsinden boyut `pbPublicKey` .  
  
 `uHashAlgId`  
 'ndaki Derlemedeki dosyaları şifrelemek için kullanılan karma algoritmanın tanımlayıcısı ya da SHA-1 algoritmasını belirtmek için NULL.  
  
 `szName`  
 'ndaki Derlemenin insanların okunabilir metin adı. Bu değerin 1024 karakteri aşmaması gerekir.  
  
 `pMetaData`  
 'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneğine yönelik bir işaretçi.  
  
 `dwAssemblyFlags`  
 'ndaki Derlemenin özelliklerini tanımlayan [CorAssemblyFlags](corassemblyflags-enumeration.md) değerlerinin birleşimi.  
  
 `pmda`  
 dışı Meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `Assembly`Bir bildirim içinde yalnızca bir meta veri yapısı tanımlanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
