---
title: ExportNestedTypeForwarder Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41c0984e4439b89ddee2b55bbca7a098075d6bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 `ComType`gibi bayrakları `tdPublic` veya `tdNested`.  
  
 `pType`  
 Dışarı aktarma türünde belirteç alır. Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
