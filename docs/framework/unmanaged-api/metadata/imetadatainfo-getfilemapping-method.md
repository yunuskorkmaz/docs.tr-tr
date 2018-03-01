---
title: IMetaDataInfo::GetFileMapping Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f974230dc5ddf2a663f05fc06850f49f1de6e773
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping Metodu
Bellek bölge eşlenmiş dosyayı ve eşleme türü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppvData`  
 [out] Bir işaretçi eşlenmiş dosyayı başlatma.  
  
 `pcbData`  
 [out] Eşlenen bölge boyutu. Varsa `pdwMappingType` olan `fmFlat`, dosya boyutudur.  
  
 `pdwMappingType`  
 [out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) eşleme türünü belirten değer. Her zaman geçerli uygulama ortak dil çalışma zamanı (CLR) döndürür `fmFlat`. Diğer değerler, gelecekte kullanılmak üzere ayrılmıştır. Ancak, diğer değerler gelecek sürümlerde etkinleştirilebilir ya da sürümlerden hizmet için döndürülen değer her zaman doğrulamanız gerekir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Tüm çıktıları doldurulur.|  
|`E_INVALIDARG`|NULL bir bağımsız değişken değeri iletildi.|  
|`COR_E_NOTSUPPORTED`|CLR uygulaması bellek bölge hakkında bilgi sağlayamıyor. Bu durum aşağıdaki nedenlerden ötürü oluşabilir:<br /><br /> -Meta veri kapsamı ile açılmış `ofWrite` veya `ofCopyMemory` bayrağı.<br />-Meta veri kapsamı olmadan açılmış `ofReadOnly` bayrağı.<br />- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi, dosyanın yalnızca meta veri bölümü açmak için kullanıldı.<br />-Dosya taşınabilir yürütülebilir (PE) dosyası değil. **Not:** olması olası gelecekte CLR sürümlerini zayıflar olan ve bu koşullar CLR mantığınız bağlıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek, `ppvData` sadece temel alınan meta veri kapsam açık olduğu sürece noktaları için geçerlidir.  
  
 Bu yöntemin çağırarak bir disk dosya meta verileri belleğe eşlediğinizde çalışmak sırayla [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi, belirtmeniz gerekir `ofReadOnly` bayrağı ve değil belirtmelisiniz `ofWrite` veya `ofCopyMemory` bayrağı.  
  
 Her kapsam için dosya eşleme türünün CLR belirli bir uygulama belirli seçimdir. Kullanıcı tarafından ayarlanamaz. Her zaman geçerli uygulama CLR döndürür `fmFlat` içinde `pdwMappingType`, ancak CLR sürümleri veya gelecek hizmet sürümleri belirli bir sürümü gelecekte değiştirebilirsiniz. Döndürülen değer her zaman kontrol `pdwMappingType`, farklı türler farklı düzenler ve uzaklıkları bulunduğundan.  
  
 Üç parametrelerinden herhangi biri NULL geçirme desteklenmiyor. Yöntem `E_INVALIDARG`, ve çıkışları hiçbiri doldurulur. Eşleme türü veya bölge boyutunu yoksayılıyor anormal program sonlandırma neden olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataInfo Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [CorFileMapping Sabit Listesi](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
