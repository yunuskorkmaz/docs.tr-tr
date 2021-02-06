---
description: ': IMetaDataImport:: EnumInterfaceImpls Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumInterfaceImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 5276d1edb3be0cae76b18a06241dc6b9952e1a72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649422"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls Yöntemi

Belirtilen tarafından uygulanan tüm arabirimleri numaralandırır `TypeDef` .
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi.  
  
 `td`  
 'ndaki MethodDef belirteçleri arabirim uygulamalarını temsil eden TypeDef 'in belirteci NUMARALANDIRILAMAZ.  
  
 `rImpls`  
 dışı MethodDef belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin uzunluk üst sınırı `rImpls` .  
  
 `pcImpls`  
 dışı İçinde döndürülen gerçek belirteç sayısı `rImpls` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak bir MethodDef belirteci yok. Bu durumda, `pcImpls` sıfır olarak ayarlanır.|  

## <a name="remarks"></a>Açıklamalar

Sabit listesi, `mdInterfaceImpl` belirtilen tarafından uygulanan her arabirim için bir belirteç koleksiyonu döndürür `TypeDef` . Arabirim belirteçleri, arabirimlerin belirtildiği sırada döndürülür ( `DefineTypeDef` veya üzerinden `SetTypeDefProps` ). Döndürülen `mdInterfaceImpl` belirteçlerin özellikleri, [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)kullanılarak sorgulanabilir.
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
