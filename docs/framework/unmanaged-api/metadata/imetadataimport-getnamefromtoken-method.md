---
description: ': IMetaDataImport:: GetNameFromToken Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetNameFromToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6195020a2b291a47e908b257896bdba64b0a40d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720858"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken Yöntemi

Belirtilen meta veri belirtecinin başvurduğu nesnenin UTF-8 adını alır. Bu yöntem artık kullanılmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tk`  
 'ndaki Adını döndürmek için nesneyi temsil eden belirteç.  
  
 `pszUtf8NamePtr`  
 dışı Yığında UTF-8 nesne adı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetNameFromToken` artık kullanılmıyor. Alternatif olarak, `GetFieldProps` bir alan veya bir yöntem için gerekli olan belirli bir belirteç türünün özelliklerini almak için bir yöntemi çağırın `GetMethodProps` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:** 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
