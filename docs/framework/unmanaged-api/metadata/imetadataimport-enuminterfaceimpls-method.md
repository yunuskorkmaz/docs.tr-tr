---
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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492253"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls Yöntemi
Belirtilen tarafından uygulanan tüm arabirimleri numaralandırır `TypeDef` .
  
## <a name="syntax"></a>Söz dizimi  
  
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
|`S_OK`|`EnumInterfaceImpls`başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak bir MethodDef belirteci yok. Bu durumda, `pcImpls` sıfır olarak ayarlanır.|  

## <a name="remarks"></a>Açıklamalar

Sabit listesi, `mdInterfaceImpl` belirtilen tarafından uygulanan her arabirim için bir belirteç koleksiyonu döndürür `TypeDef` . Arabirim belirteçleri, arabirimlerin belirtildiği sırada döndürülür ( `DefineTypeDef` veya üzerinden `SetTypeDefProps` ). Döndürülen `mdInterfaceImpl` belirteçlerin özellikleri, [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)kullanılarak sorgulanabilir.
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
