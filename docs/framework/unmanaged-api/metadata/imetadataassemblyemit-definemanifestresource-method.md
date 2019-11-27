---
title: IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432056"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
Belirtilen bildirim kaynağı için meta verileri içeren bir `ManifestResource` yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szName`  
 'ndaki Kaynağın adı.  
  
 `tkImplementation`  
 'ndaki Kaynak sağlayıcısına eşlenen `mdtFile` veya `mdtAssemblyRef` türünde bir meta veri belirteci. NULL değer, meta verilerin katıştırıldığı dosyanın kaynak sağlayıcısı olduğunu gösterir.  
  
 `dwOffset`  
 'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık. Tek başına dosyalardaki kaynaklar için bu her zaman sıfır olur. Kaynak bir PE (taşınabilir yürütülebilir) dosyasına katıştırılmışsa, bu, Cor. h üstbilgi dosyasında belirtilen konumda başlayan kaynak BLOBUN bir denklüdür.  
  
 `dwResourceFlags`  
 'ndaki Kaynak tanımı için özellik ayarlarını belirten bayrak değerlerinin bit düzeyinde birleşimi.  
  
 `pmdmr`  
 dışı Döndürülen meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ManifestResource` meta veri yapısının her bir derleme dosyasında uygulanan her kaynak için tanımlanması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
