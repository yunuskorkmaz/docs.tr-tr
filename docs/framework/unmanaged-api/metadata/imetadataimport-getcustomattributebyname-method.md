---
title: IMetaDataImport::GetCustomAttributeByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: e6921a0f6420546ba1e866e37a7a7cb129a77c67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491465"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName Yöntemi
Adı ve sahibi verilen özel özniteliği alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkObj`  
 'ndaki Özel özniteliğin sahibi olan nesneyi temsil eden bir meta veri belirteci.  
  
 `szName`  
 'ndaki Özel özniteliğin adı.  
  
 `ppData`  
 dışı Özel özniteliğin değeri olan bir veri dizisine yönelik bir işaretçi.  
  
 `pcbData`  
 dışı * ' De döndürülen verilerin bayt cinsinden boyutu `ppData` .  
  
## <a name="remarks"></a>Açıklamalar  
 Aynı sahip için birden çok özel öznitelik tanımlamak geçerlidir; aynı ada bile sahip olabilirler. Ancak `GetCustomAttributeByName` yalnızca bir örnek döndürür. ( `GetCustomAttributeByName` karşılaştığı ilk örneği döndürür.) Özel bir özniteliğin tüm örneklerini bulmak için, [IMetaDataImport:: EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) yöntemini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
