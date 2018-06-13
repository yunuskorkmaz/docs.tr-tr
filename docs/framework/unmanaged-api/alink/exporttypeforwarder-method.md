---
title: ExportTypeForwarder Metodu
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b28c18d55b91d6315003229295ab0e6781be183
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406311"
---
# <a name="exporttypeforwarder-method"></a>ExportTypeForwarder Metodu
Tür iletici verilen derleme türü tablosuna ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tkAssemblyRef`  
 Tür iletici başvurduğu derlemesine başvuru.  
  
 `pszTypename`  
 Dışarı aktarmak için tam olarak nitelenmiş tür adı.  
  
 `dwFlags`  
 `ComType` gibi bayrakları `tdPublic` veya `tdNested`. Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Dışarı aktarılan tür belirtecini alır. Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
