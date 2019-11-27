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
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436182"
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
 dışı Eşlenen bölgenin boyutu. `pdwMappingType` `fmFlat`, bu dosyanın boyutudur.  
  
 `pdwMappingType`  
 dışı Eşleme türünü gösteren [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) değeri. Ortak dil çalışma zamanının (CLR) geçerli uygulanması her zaman `fmFlat`döndürür. Diğer değerler gelecekte kullanılmak üzere ayrılmıştır. Bununla birlikte, döndürülen değeri her zaman doğrulamanız gerekir, çünkü diğer değerler gelecek sürümlerde veya hizmet sürümlerinde etkinleştirilebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Tüm çıkışlar doldurulur.|  
|`E_INVALIDARG`|NULL bir bağımsız değişken değeri olarak geçirildi.|  
|`COR_E_NOTSUPPORTED`|CLR uygulama bellek bölgesi hakkında bilgi sağlayamıyor. Bu durum aşağıdaki nedenlerden kaynaklanabilir:<br /><br /> -Meta veri kapsamı `ofWrite` veya `ofCopyMemory` bayrağıyla açıldı.<br />-Meta veri kapsamı `ofReadOnly` bayrağı olmadan açıldı.<br />-Dosyanın yalnızca meta veri bölümünü açmak için [ımetadatadağıtıcı:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi kullanıldı.<br />-Dosya taşınabilir bir çalıştırılabilir (PE) dosyası değil. **Note:**  Bu koşullar CLR uygulamasına Bağımlıdır ve CLR 'nin gelecek sürümlerinde zayıflatılmış olma olasılığı yüksektir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ppvData`, işaret eden bellek yalnızca temeldeki meta veri kapsamı açık olduğu sürece geçerlidir.  
  
 Bu yöntemin çalışması için, [ımetadatadağıtıcı:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metodunu çağırarak disk üzerindeki bir dosyanın meta verilerini belleğe eşlediğinizde `ofReadOnly` bayrağını belirtmeniz gerekir ve `ofWrite` veya `ofCopyMemory` bayrağını belirtmemelidir.  
  
 Her kapsam için dosya eşleme türü seçimi, CLR 'nin belirli bir uygulamasına özgüdür. Kullanıcı tarafından ayarlanamaz. CLR 'nin geçerli uygulanması her zaman `pdwMappingType``fmFlat` döndürür, ancak bu, CLR 'nin gelecekteki sürümlerinde veya belirli bir sürümün gelecekteki hizmet sürümlerinde değişebilir. Farklı türlerin farklı düzenlerine ve uzaklıklara sahip olacağı için `pdwMappingType`döndürülen değeri her zaman denetlemeniz gerekir.  
  
 Üç parametreden herhangi biri için NULL geçirme desteklenmez. Yöntemi `E_INVALIDARG`döndürür ve çıktıların hiçbiri doldurulmaz. Eşleme türü yok sayılıyor veya bölgenin boyutu olağan dışı program sonlandırmasına neden olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataInfo Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping Sabit Listesi](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
