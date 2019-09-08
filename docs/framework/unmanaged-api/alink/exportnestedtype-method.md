---
title: ExportNestedType Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777268"
---
# <a name="exportnestedtype-method"></a>ExportNestedType Yöntemi
İç içe geçmiş türleri verilebilir olarak belirtir. [ExportType Yöntemi](exporttype-method.md) iç içe geçmiş türleri de dışa aktarabilir, ancak bu yöntem daha hızlıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dışarı aktarılacak derlemenin KIMLIĞI.  
  
 `FileToken`  
 Dışarı aktarılabilir hale getirilme türünü tanımlayan dosya belirteci veya dosya derlemesi.  
  
 `TypeToken`  
 Dışarı aktarılabilir hale getirilme türünün tür belirteci.  
  
 `ParentType`  
 Üst tür belirteci.  
  
 `pszTypename`  
 Dışarı aktarılacak tam tür adı.  
  
 `dwFlags`  
 `ComType``tdPublic` veya`tdNested`gibi bayraklar. Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.  
  
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
