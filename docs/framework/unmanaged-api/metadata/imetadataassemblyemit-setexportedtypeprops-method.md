---
title: IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: fa4f1f57cb8fe1ca81bbad6438a88bb43c48e7bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008085"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi
Belirtilen `ExportedType` meta veri yapısını değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ct`  
 'ndaki `ExportedType`Değiştirilecek meta veri yapısını belirten meta veri belirteci.  
  
 `tkImplementation`  
 'ndaki `File` `AssemblyRef` `ExportedType` Bu türün nasıl uygulandığını belirten, veya türündeki belirteç.  
  
 `tkTypeDef`  
 'ndaki `TypeDef`Kod dosyasında başvurulan belirteç.  
  
 `dwExportedTypeFlags`  
 'ndaki Türün özniteliklerini belirten bir bit düzeyinde değer birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ExportedType`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineExportedType](imetadataassemblyemit-defineexportedtype-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
