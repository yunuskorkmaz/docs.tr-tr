---
title: IMetaDataImport::GetParamProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
