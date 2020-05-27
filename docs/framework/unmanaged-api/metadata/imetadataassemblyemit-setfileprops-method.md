---
title: IMetaDataAssemblyEmit::SetFileProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008072"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps Yöntemi
Belirtilen `File` meta veri yapısını değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `file`  
 'ndaki `File`Değiştirilecek meta veri yapısını belirten meta veri belirteci.  
  
 `pbHashValue`  
 'ndaki Dosyayla ilişkili karma verilere yönelik bir işaretçi.  
  
 `cbHashValue`  
 'ndaki Bayt cinsinden boyut `pbHashValue` .  
  
 `dwFileFlags`  
 'ndaki Dosyanın çeşitli özniteliklerini belirten [CorFileFlags](corfileflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `File`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
