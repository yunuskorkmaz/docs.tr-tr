---
description: ': IMetaDataImport:: EnumUnresolvedMethods yöntemi hakkında daha fazla bilgi'
title: IMetaDataImport::EnumUnresolvedMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: e894ecdde91a2263783234d73fa50d890a13e413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799336"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods Yöntemi

Geçerli meta veri kapsamındaki çözümlenmemiş yöntemleri temsil eden MemberDef belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi. Bu yöntemin ilk çağrısı için bu NULL olmalıdır.  
  
 `rMethods`  
 dışı MemberDef belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rMethods` .  
  
 `pcTokens`  
 dışı İçinde döndürülen MemberDef belirteçleri sayısı `rMethods` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak belirteç yok. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Çözümlenmemiş bir yöntem, tanımlanan ancak uygulanmayan bir yöntemdir. Yöntem işaretlenmişse `miForwardRef` ve ya da `mdPinvokeImpl` sıfır olarak ayarlandıysa, bir yöntem numaralandırmaya dahil edilir `miRuntime` . Diğer bir deyişle, çözümlenmemiş bir yöntem, `miForwardRef` yönetilmeyen kodda uygulanmayan, ancak bir çalışma zamanının kendisi tarafından dahili olarak uygulanan bir sınıf yöntemidir  
  
 Sabit listesi, modül kapsamında (genel) veya arabirimlerde ya da soyut sınıflarda tanımlanmış tüm yöntemleri dışlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
