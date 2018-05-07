---
title: ExportNestedTypeForwarder Metodu
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder Metodu
İç içe geçmiş tür için bir tür iletici verilen derleme türü tablosuna ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dışarı aktarmak için derleme kimliği.  
  
 `FileToken`  
 Dosya belirteç veya derleme kimliği türü tanımlayan dosyası.  
  
 `TypeToken`  
 Belirteç türü için.  
  
 `ParentType`  
 Üst tür belirteci.  
  
 `pszTypename`  
 Dışarı aktarmak için tam olarak nitelenmiş tür adı.  
  
 `dwFlags`  
 `ComType` gibi bayrakları `tdPublic` veya `tdNested`.  
  
 `pType`  
 Dışarı aktarma türünde belirteç alır. Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
