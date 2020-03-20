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
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179407"
---
# <a name="exportnestedtype-method"></a>ExportNestedType Yöntemi
İç içe geçme türlerini dışa aktarılabilir olarak belirtir. [Dışa Aktarma Türü Yöntemi](exporttype-method.md) iç içe geçen türleri de dışa aktarabilir, ancak bu yöntem daha hızlıdır.  
  
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
 Dışa aktarmak için montaj kimliği.  
  
 `FileToken`  
 Dışa aktarılacak türü tanımlayan dosya belirteci veya derlemesi.  
  
 `TypeToken`  
 Dışa aktarılabilir hale getirilecek türü belirteç.  
  
 `ParentType`  
 Ana tip belirteç.  
  
 `pszTypename`  
 Dışa aktarmak için tam nitelikli tür adı.  
  
 `dwFlags`  
 `ComType`gibi `tdPublic` bayraklar `tdNested`veya . Bu değer [DefineExportedType Yöntemi'ne](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.  
  
 `pType`  
 Dışa aktarılan tür için belirteç alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 alink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
