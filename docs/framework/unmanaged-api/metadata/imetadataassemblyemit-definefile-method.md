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
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176064"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile Yöntemi
Bu derleme `File` tarafından başvurulan derleme için meta veri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirteci döndürür.  
  
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
 [içinde] Tüketilecek dosyanın adı.  
  
 `pbHashValue`  
 [içinde] Derleme ile ilişkili karma verilere işaretçi.  
  
 `cbHashValue`  
 [içinde] `pbHashValue`Baytboyutu.  
  
 `dwFileFlags`  
 [içinde] Özellik ayarlarını `FileFlags` belirten değerlerin bitwise birleşimi.  
  
 `pmdf`  
 [çıkış] Döndürülen `File` belirteç için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta `File` verileri içeren dosya hariç olmak üzere, bu derlemenin yapıldığı sırada bu derlemenin parçası olan her dosya için bir meta veri yapısı tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
