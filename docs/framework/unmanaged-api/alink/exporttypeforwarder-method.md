---
description: 'Daha fazla bilgi edinin: ExportTypeForwarder yöntemi'
title: ExportTypeForwarder Yöntemi
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
ms.openlocfilehash: 59fb74c83f6d30dda87d908353795fb218190022
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637995"
---
# <a name="exporttypeforwarder-method"></a>ExportTypeForwarder Yöntemi

Verilen derlemenin tür tablosuna bir tür ileticisi ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `tkAssemblyRef`  
 Tür ileticinin başvurduğu derlemeye başvuru.  
  
 `pszTypename`  
 Dışarı aktarılacak tam tür adı.  
  
 `dwFlags`  
 `ComType` veya gibi bayraklar `tdPublic` `tdNested` . Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.  
  
 `pType`  
 , Dışarıya aktarılmış türün belirtecini alır. Bu yalnızca iç içe geçmiş türleri yayma için gereklidir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
