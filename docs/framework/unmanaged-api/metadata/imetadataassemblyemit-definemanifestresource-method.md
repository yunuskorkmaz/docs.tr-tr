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
ms.openlocfilehash: 026f5efe195cdb34999b65c5f47de6f68d30e11a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008137"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
`ManifestResource`Belirtilen bildirim kaynağı için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `mdtFile`Kaynak sağlayıcısına eşlenen veya türü bir meta veri belirteci `mdtAssemblyRef` . NULL değer, meta verilerin katıştırıldığı dosyanın kaynak sağlayıcısı olduğunu gösterir.  
  
 `dwOffset`  
 'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık. Tek başına dosyalardaki kaynaklar için bu her zaman sıfır olur. Kaynak bir PE (taşınabilir yürütülebilir) dosyasına katıştırılmışsa, bu, Cor. h üstbilgi dosyasında belirtilen konumda başlayan kaynak BLOBUN bir denklüdür.  
  
 `dwResourceFlags`  
 'ndaki Kaynak tanımı için özellik ayarlarını belirten bayrak değerlerinin bit düzeyinde birleşimi.  
  
 `pmdmr`  
 dışı Döndürülen meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Her bir `ManifestResource` derleme dosyasında uygulanan her kaynak için bir meta veri yapısı tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
