---
title: ExportType Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 84c41e467c57afd2562e7aa8dd72ce4796249667
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438573"
---
# <a name="exporttype-method"></a>ExportType Yöntemi
Bir türün verilebilir olduğunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dışarı aktarılacak derlemenin KIMLIĞI.  
  
 `FileToken`  
 Dışarı aktarılabilir türü tanımlayan dosyanın dosya belirteci veya derleme KIMLIĞI.  
  
 `TypeToken`  
 Dışarı aktarılabilir yapılacak tür belirteci.  
  
 `pszTypename`  
 Dışarı aktarılabilir hale getirmek için tam tür adı.  
  
 `dwFlags`  
 `tdPublic` veya `tdNested`gibi bayrakları `ComType`. Bu parametre [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.  
  
 `pType`  
 İçe aktarılmış tür için belirteç alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
