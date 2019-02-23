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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 697a59d80e152fb78164491c2a0eaaa8707f8914
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745926"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps Metodu
Meta veri değerleri tarafından belirtilen ParamDef başvurulan parametresi için belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `tk`  
 [in] Meta verileri döndürmek için parametre temsil eden bir ParamDef belirteci.  
  
 `pmd`  
 [out] Yönteminin parametresi alan temsil eden bir MethodDef belirteç için bir işaretçi.  
  
 `pulSequence`  
 [out] Sıralı konumu parametresi yöntemi bağımsız değişken listesi.  
  
 `szName`  
 [out] Parametrenin adını tutan bir arabellek.  
  
 `cchName`  
 [in] Geniş karakter cinsinden istenen boyuta `szName`.  
  
 `pchName`  
 [out] Geniş karakter cinsinden döndürülen boyutu `szName`.  
  
 `pdwAttr`  
 [out] Parametresi ile ilişkili herhangi bir öznitelik bayrağı için bir işaretçi. Bu, bir bit maskesi, `CorParamAttr` değerleri.  
  
 `pdwCPlusTypeFlag`  
 [out] Parametre belirten bir bayrak için bir işaretçi bir <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Parametresi tarafından döndürülen bir sabit dize işaretçisi.  
  
 `pcchValue`  
 [out] Boyutu `ppValue` geniş karakterler ya da sıfır `ppValue` bir dize tutmaz.  
  
## <a name="remarks"></a>Açıklamalar

Sıralı değerleri `pulSequence` parametreleri için 1 ile başlar. Dönüş değeri bir sıra numarası 0 sahiptir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
