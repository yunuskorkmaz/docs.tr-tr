---
title: IMetaDataAssemblyEmit::DefineFile Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008150"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile Yöntemi
`File`Bu derleme tarafından başvurulan derleme için meta verileri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szName`  
 'ndaki Tüketilecek dosyanın adı.  
  
 `pbHashValue`  
 'ndaki Derlemeyle ilişkili karma verileri işaretçisi.  
  
 `cbHashValue`  
 'ndaki Bayt cinsinden boyut `pbHashValue` .  
  
 `dwFileFlags`  
 'ndaki `FileFlags`Özellik ayarlarını belirten değerlerin bit tabanlı birleşimi.  
  
 `pmdf`  
 dışı Döndürülen belirtece yönelik bir işaretçi `File` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `File` derlemenin oluşturulduğu zaman, meta verileri içeren dosya hariç olmak üzere, bu derlemenin parçası olan her bir dosya için bir meta veri yapısının tanımlanması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
