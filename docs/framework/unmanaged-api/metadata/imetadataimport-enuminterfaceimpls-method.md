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
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175505"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls Yöntemi
Belirtilen `TypeDef`tarafından uygulanan tüm arabirimleri oyalar.
  
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
 [içinde, dışarı] Sayıya işaretçisi.  
  
 `td`  
 [içinde] Arabirim uygulamalarını temsil eden MethodDef belirteçleri numaralandırılacak Olan TypeDef belirteci.  
  
 `rImpls`  
 [çıkış] MethodDef belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 [içinde] `rImpls` Dizinin maksimum uzunluğu.  
  
 `pcImpls`  
 [çıkış] Döndürülen belirteçlerin gerçek `rImpls`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala çıkarmak için MethodDef belirteçleri yoktur. Bu durumda, `pcImpls` sıfıra ayarlanır.|  

## <a name="remarks"></a>Açıklamalar

Numaralandırma, belirtilen ler tarafından `mdInterfaceImpl` uygulanan her arabirim için bir `TypeDef`belirteç ler koleksiyonunu döndürür. Arabirim belirteçleri, arabirimlerin belirtildiği sırayla `DefineTypeDef` `SetTypeDefProps`döndürülür (üzerinden veya). Döndürülen `mdInterfaceImpl` belirteçlerin özellikleri [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)kullanılarak sorgulanabilir.
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
