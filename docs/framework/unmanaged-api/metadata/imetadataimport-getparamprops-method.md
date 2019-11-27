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
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437131"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps Metodu
Belirtilen ParamDef belirtecinin başvurduğu parametreye ait meta veri değerlerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `szName`geniş karakterdeki istenen boyut.  
  
 `pchName`  
 dışı `szName`geniş karakterdeki döndürülen boyut.  
  
 `pdwAttr`  
 dışı Parametresiyle ilişkili öznitelik bayraklarının bir işaretçisi. Bu, `CorParamAttr` değerlerinin bir bit dır.  
  
 `pdwCPlusTypeFlag`  
 dışı Parametrenin <xref:System.ValueType>olduğunu belirten bayrak işaretçisi.  
  
 `ppValue`  
 dışı Parametresi tarafından döndürülen sabit dize işaretçisi.  
  
 `pcchValue`  
 dışı Geniş karakterdeki `ppValue` boyutu veya `ppValue` bir dize yoksa sıfır.  
  
## <a name="remarks"></a>Açıklamalar

`pulSequence` dizi değerleri parametreler için 1 ile başlar. Dönüş değerinin sıra numarası 0 ' dır.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
