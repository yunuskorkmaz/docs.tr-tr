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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081800"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping Yöntemi
Eşleşen dosya ve tür eşlemesi bellek bölgesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppvData`  
 [out] Eşleşen dosya başlangıcı için bir işaretçi.  
  
 `pcbData`  
 [out] Eşleştirilmiş bölge boyutu. Varsa `pdwMappingType` olduğu `fmFlat`, dosyanın boyutu budur.  
  
 `pdwMappingType`  
 [out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) eşleme türünü belirten değer. Ortak dil çalışma zamanı (CLR) her zaman geçerli uygulamasını döndürür `fmFlat`. Diğer değerleri, gelecekte kullanılmak üzere ayrılmıştır. Ancak, diğer değerleri gelecek sürümlerde etkinleştirilmemiş olabilir veya yayınlar hizmet için döndürülen değer her zaman doğrulamanız gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Tüm çıktıların doldurulur.|  
|`E_INVALIDARG`|NULL bir bağımsız değişken değeri geçirildi.|  
|`COR_E_NOTSUPPORTED`|CLR uygulamasındaki bellek bölge bilgileri sağlayamaz. Bu durum aşağıdaki nedenlerden dolayı oluşabilir:<br /><br /> -Meta veri kapsamı ile açılmış `ofWrite` veya `ofCopyMemory` bayrağı.<br />-Meta veri kapsamı olmadan açılmış `ofReadOnly` bayrağı.<br />- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi yalnızca dosya meta veri bölümü açmak için kullanıldı.<br />-Dosya taşınabilir çalıştırılabilir (PE) dosyası değil. **Not:**  Bu koşullar CLR uygulamasının bağlıdır ve gelecek sürümleri CLR'nin zayıflar muhtemeldir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek, `ppvData` noktalarına, temel alınan meta veri kapsamı yalnızca açık olduğu sürece geçerlidir.  
  
 Bu yöntemi çağırarak bir diskteki dosyanın meta verilerini belleğe eşlediğinizde, iş için sırayla [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi belirtmelisiniz `ofReadOnly` bayrağı ve değil belirtmelisiniz `ofWrite` veya `ofCopyMemory` bayrağı.  
  
 Her kapsam için dosya eşleme türü seçimi, CLR'nin belirli bir uygulamaya özeldir. Kullanıcı tarafından ayarlanamaz. Her zaman geçerli uygulama CLR döndürür `fmFlat` içinde `pdwMappingType`, ancak gelecekte CLR'nin sürümünü veya gelecek hizmet sürümlerini belirli bir sürümü değiştirebilirsiniz. Döndürülen değer her zaman iade etmelisiniz `pdwMappingType`, farklı alan farklı düzenler ve ofsetleri olduğundan.  
  
 Herhangi bir üç parametre için NULL geçirme desteklenmiyor. Yöntem döndürür `E_INVALIDARG`, ve çıkışları hiçbiri doldurulur. Eşleme türü veya bölgenin boyutunu yoksayılıyor anormal program sonlandırmada neden olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataInfo Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping Numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
