---
description: ': IMetaDataInfo:: GetFileMapping yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 82a1a23c50a4d8340804f66966933fc6a11e0f8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688487"
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
 dışı Eşlenen dosyanın başlangıcına yönelik bir işaretçi.  
  
 `pcbData`  
 dışı Eşlenen bölgenin boyutu. `pdwMappingType`İse `fmFlat` , bu dosyanın boyutudur.  
  
 `pdwMappingType`  
 dışı Eşleme türünü gösteren [CorFileMapping](corfilemapping-enumeration.md) değeri. Ortak dil çalışma zamanının (CLR) geçerli uygulanması her zaman döndürülür `fmFlat` . Diğer değerler gelecekte kullanılmak üzere ayrılmıştır. Bununla birlikte, döndürülen değeri her zaman doğrulamanız gerekir, çünkü diğer değerler gelecek sürümlerde veya hizmet sürümlerinde etkinleştirilebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|Tüm çıkışlar doldurulur.|  
|`E_INVALIDARG`|NULL bir bağımsız değişken değeri olarak geçirildi.|  
|`COR_E_NOTSUPPORTED`|CLR uygulama bellek bölgesi hakkında bilgi sağlayamıyor. Bu durum aşağıdaki nedenlerden kaynaklanabilir:<br /><br /> -Meta veri kapsamı `ofWrite` veya `ofCopyMemory` bayrağıyla açıldı.<br />-Meta veri kapsamı bayrak olmadan açıldı `ofReadOnly` .<br />-Dosyanın yalnızca meta veri bölümünü açmak için [ımetadatadağıtıcı:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) yöntemi kullanıldı.<br />-Dosya taşınabilir bir çalıştırılabilir (PE) dosyası değil. **Note:**  Bu koşullar CLR uygulamasına Bağımlıdır ve CLR 'nin gelecek sürümlerinde zayıflatılmış olma olasılığı yüksektir.|  
  
## <a name="remarks"></a>Açıklamalar  

 ' A işaret eden bellek `ppvData` yalnızca temeldeki meta veri kapsamı açık olduğu sürece geçerlidir.  
  
 Bu yöntemin çalışması için, [ımetadatadağıtıcı:: OpenScope](imetadatadispenser-openscope-method.md) metodunu çağırarak, disk üzerindeki bir dosyanın meta verilerini belleğe eşlediğinizde, bayrağını belirtmeniz gerekir `ofReadOnly` ve `ofWrite` veya bayrağını belirtmemelidir `ofCopyMemory` .  
  
 Her kapsam için dosya eşleme türü seçimi, CLR 'nin belirli bir uygulamasına özgüdür. Kullanıcı tarafından ayarlanamaz. CLR 'nin geçerli uygulanması her zaman ' `fmFlat` de döner `pdwMappingType` , ancak bu, clr 'nin gelecekteki sürümlerinde veya belirli bir sürümün gelecekteki hizmet sürümlerinde değişebilir. `pdwMappingType`Farklı türlerin farklı düzenlerine ve uzaklıklara sahip olacağı için döndürülen değeri her zaman denetlemeniz gerekir.  
  
 Üç parametreden herhangi biri için NULL geçirme desteklenmez. Yöntemi döndürülür `E_INVALIDARG` ve çıktıların hiçbiri doldurulmaz. Eşleme türü yok sayılıyor veya bölgenin boyutu olağan dışı program sonlandırmasına neden olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataInfo Arabirimi](imetadatainfo-interface.md)
- [CorFileMapping Numaralandırması](corfilemapping-enumeration.md)
