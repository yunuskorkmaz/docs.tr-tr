---
description: ': IMetaDataImport2:: GetMethodSpecProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport2::GetMethodSpecProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 77f3f78905d1f7f44af0e9c7a75746b4e5b6e684
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688656"
---
# <a name="imetadataimport2getmethodspecprops-method"></a>IMetaDataImport2::GetMethodSpecProps Yöntemi

Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a>Parametreler  

 `mi`  
 'ndaki Metodun örneklenmesini temsil eden bir MethodSpec belirteci.  
  
 `tkParent`  
 dışı Yöntem tanımını temsil eden MethodDef veya MethodRef belirtecine yönelik bir işaretçi.  
  
 `ppvSigBlob`  
 dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.  
  
 `pcbSigBlob`  
 dışı Bayt cinsinden boyutu `ppvSigBlob` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
