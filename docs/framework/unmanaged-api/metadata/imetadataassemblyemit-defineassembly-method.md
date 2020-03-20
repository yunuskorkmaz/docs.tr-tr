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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177896"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly Yöntemi
Belirtilen derleme `Assembly` için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirteci döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [içinde] Derlemenin yayımcısını tanımlayan ortak anahtar veya derleme nin güçlü bir şekilde adlandırılmadıysa NULL.  
  
 `cbPublicKey`  
 [içinde] `pbPublicKey`Baytboyutu.  
  
 `uHashAlgId`  
 [içinde] Derlemedeki dosyaları şifrelemek için kullanılacak karma algoritmanın tanımlayıcısı veya SHA-1 algoritmasını belirtmek için NULL.  
  
 `szName`  
 [içinde] Derlemenin insan tarafından okunabilen metin adı. Bu değer 1024 karakteri geçmemelidir.  
  
 `pMetaData`  
 [içinde] Derlemenin sürümünü, platformlarını ve yerel bilgilerini içeren bir ASSEMBLYMETADATA örneğine işaretçi.  
  
 `dwAssemblyFlags`  
 [içinde] Derlemenin özelliklerini açıklayan [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerlerinin birleşimi.  
  
 `pmda`  
 [çıkış] Meta veri belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `Assembly` bildirim içinde yalnızca bir meta veri yapısı tanımlanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
