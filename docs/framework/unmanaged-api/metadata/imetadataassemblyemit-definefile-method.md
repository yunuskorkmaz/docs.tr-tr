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
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440211"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile Yöntemi
Bu derleme tarafından başvurulan derleme için meta verileri içeren bir `File` meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `pbHashValue`bayt cinsinden boyutu.  
  
 `dwFileFlags`  
 'ndaki Özellik ayarlarını belirten `FileFlags` değerlerinin bit düzeyinde birleşimi.  
  
 `pmdf`  
 dışı Döndürülen `File` belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derlemenin oluşturulduğu zaman, meta verileri içeren dosya hariç olmak üzere, bu derlemenin parçası olan her bir dosya için bir `File` meta veri yapısının tanımlanması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
