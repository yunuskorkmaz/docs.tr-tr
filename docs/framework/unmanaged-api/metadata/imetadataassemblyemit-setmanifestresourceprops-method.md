---
title: IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: c46a3bc34ba7efa760e50416e9a6c39779727813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708935"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a>IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi

Belirtilen `ManifestResource` meta veri yapısını değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `mr`  
 'ndaki `ManifestResource` Değiştirilecek meta veri yapısını belirten belirteç.  
  
 `tkImplementation`  
 'ndaki `File` Kaynak sağlayıcısına eşlenen veya türündeki belirteç `AssemblyRef` .  
  
 `dwOffset`  
 'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık.  
  
 `dwResourceFlags`  
 'ndaki Kaynak özniteliklerini belirleyen bayrak değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  

 `ManifestResource`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
