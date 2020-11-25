---
title: IMetaDataImport::GetParamProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: a16621f4c9b06f049239dc4e2335d70a167dd756
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729271"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps Metodu

Belirtilen ParamDef belirtecinin başvurduğu parametreye ait meta veri değerlerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tk`  
 'ndaki Meta verilerini döndürecek parametreyi temsil eden ParamDef belirteci.  
  
 `pmd`  
 dışı Parametreyi alan yöntemi temsil eden bir MethodDef belirtecinin işaretçisi.  
  
 `pulSequence`  
 dışı Yöntem bağımsız değişken listesindeki parametresinin sıra konumu.  
  
 `szName`  
 dışı Parametrenin adını tutan bir arabellek.  
  
 `cchName`  
 'ndaki Geniş karakterdeki istenen boyut `szName` .  
  
 `pchName`  
 dışı Geniş karakter olarak döndürülen boyut `szName` .  
  
 `pdwAttr`  
 dışı Parametresiyle ilişkili öznitelik bayraklarının bir işaretçisi. Bu bir değer bit değeridir `CorParamAttr` .  
  
 `pdwCPlusTypeFlag`  
 dışı Parametresinin bir olduğunu belirten bayrak işaretçisi <xref:System.ValueType> .  
  
 `ppValue`  
 dışı Parametresi tarafından döndürülen sabit dize işaretçisi.  
  
 `pcchValue`  
 dışı `ppValue` Geniş karakter veya dize yoksa sıfır olan boyut `ppValue` .  
  
## <a name="remarks"></a>Açıklamalar

İçindeki sıra değerleri, `pulSequence` Parametreler için 1 ile başlar. Dönüş değerinin sıra numarası 0 ' dır.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
