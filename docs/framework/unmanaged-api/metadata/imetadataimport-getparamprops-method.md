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
ms.openlocfilehash: 95850448504fd863f2726a7fb7574436476a6dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449331"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps Metodu
Meta veri değerleri belirtilen ParamDef tarafından başvurulan parametresi için belirteç alır.  
  
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
 [out] Parametresi alan yöntemi temsil eden bir MethodDef belirteci için bir işaretçi.  
  
 `pulSequence`  
 [out] Sıralı konumu parametresi yöntemi bağımsız değişken listesi.  
  
 `szName`  
 [out] Parametrenin adını tutmak için arabellek.  
  
 `cchName`  
 [in] Geniş karakterler istenen boyutta `szName`.  
  
 `pchName`  
 [out] Geniş karakterler döndürülen boyutu `szName`.  
  
 `pdwAttr`  
 [out] Parametresi ile ilişkili herhangi bir öznitelik bayrağı için bir işaretçi.  
  
 `pdwCPlusTypeFlag`  
 [out] Parametre belirten bir bayrak için bir işaretçi bir <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Parametresi tarafından döndürülen bir sabit dize için bir işaretçi.  
  
 `pcchValue`  
 [out] Boyutunu `ppValue` geniş karakterler ya da sıfır `ppValue` bir dize tutmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
