---
title: IMetaDataImport::GetClassLayout Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 36c0ffef2d984604be4ae19899e8f3f912cee123
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491478"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout Metodu
Belirtilen TypeDef belirtecinin başvurduğu sınıfa ait düzen bilgisini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki Döndürülecek düzen ile sınıfın TypeDef belirteci.  
  
 `pdwPackSize`  
 dışı Sınıfın paket boyutunu temsil eden 1, 2, 4, 8 veya 16 değerlerinden biri.  
  
 `rFieldOffset`  
 dışı [COR_FIELD_OFFSET](cor-field-offset-structure.md) değerleri dizisi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rFieldOffset` .  
  
 `pcFieldOffset`  
 dışı İçinde döndürülen öğelerin sayısı `rFieldOffset` .  
  
 `pulClassSize`  
 dışı Tarafından temsil edilen sınıfın bayt cinsinden boyutu `td` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
