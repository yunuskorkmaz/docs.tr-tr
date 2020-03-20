---
title: IMetaDataInfo::GetFileMapping Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175271"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping Yöntemi
Eşlenen dosyanın bellek bölgesini ve eşleme türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppvData`  
 [çıkış] Eşlenen dosyanın başlangıcına işaretçi.  
  
 `pcbData`  
 [çıkış] Eşlenen bölgenin boyutu. `pdwMappingType` Varsa, `fmFlat`bu dosyanın boyutudur.  
  
 `pdwMappingType`  
 [çıkış] Eşleme türünü gösteren [bir CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) değeri. Ortak dil çalışma zamanı (CLR) geçerli `fmFlat`uygulama her zaman döndürür. Diğer değerler ileride kullanılmak üzere ayrılmıştır. Ancak, diğer değerler gelecekteki sürümlerde veya hizmet sürümlerinde etkinleştirilebileceğinden, döndürülen değeri her zaman doğrulamanız gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Tüm çıktılar doldurulur.|  
|`E_INVALIDARG`|NULL bağımsız değişken değeri olarak geçirildi.|  
|`COR_E_NOTSUPPORTED`|CLR uygulaması bellek bölgesi hakkında bilgi sağlayamaz. Bu aşağıdaki nedenlerle olabilir:<br /><br /> - Meta veri kapsamı `ofWrite` veya `ofCopyMemory` bayrak ile açıldı.<br />- Meta veri kapsamı `ofReadOnly` bayrak olmadan açıldı.<br />- Dosyanın yalnızca meta veri bölümünü açmak için [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi kullanılmıştır.<br />- Dosya taşınabilir bir yürütülebilir (PE) dosya değildir. **Not:**  Bu koşullar CLR uygulamasına bağlıdır ve CLR'nin gelecekteki sürümlerinde zayıflamış olma olasılığı yüksektir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca temel `ppvData` meta veri kapsamı açık olduğu sürece işaret eden bellek geçerlidir.  
  
 Bu yöntemin işe yaraması için, bir disk dosyasının meta verilerini [IMetaDataDispenser'ı](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) arayarak belleğe eşlediğinizde::OpenScope yöntemi, `ofReadOnly` bayrağı belirtmeniz gerekir ve bayrağı `ofWrite` belirtmemelisiniz. `ofCopyMemory`  
  
 Her kapsam için dosya eşleme türü seçimi CLR belirli bir uygulamaya özgüdür. Kullanıcı tarafından ayarlanamaz. CLR'nin geçerli uygulaması `fmFlat` her `pdwMappingType`zaman , ancak bu CLR'nin gelecekteki sürümlerinde veya belirli bir sürümün gelecekteki hizmet sürümlerinde değişebilir. Farklı türlerde farklı düzenler `pdwMappingType`ve uzaklıklar olacağından, iade edilen değeri her zaman denetlemeniz gerekir.  
  
 Üç parametreden herhangi biri için NULL'u geçmek desteklenmez. Yöntem döndürür `E_INVALIDARG`ve çıktıların hiçbiri doldurulur. Eşleme türünü veya bölgenin boyutunu yok saymak anormal program sonlandırmaneden olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataInfo Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping Sabit Listesi](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
