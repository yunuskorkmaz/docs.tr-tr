---
title: IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448297"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
Başvuruları çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kuralları kullanarak, belirtilen `szAssemblyName` parametresine sahip derlemelerin dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szAppBase`  
 'ndaki Verilen derlemenin aranacağı kök dizin. Bu değer `null`olarak ayarlandıysa, `FindAssembliesByName` yalnızca derleme için genel derleme önbelleğinde görünür.  
  
 `szPrivateBin`  
 'ndaki Derlemenin aranacağı kök dizin altında, noktalı virgülle ayrılmış alt dizinlerin (örneğin, "bin; bin2") bir listesi. Bu dizinler, varsayılan yoklama kurallarında belirtienlere ek olarak araştırlanır.  
  
 `szAssemblyName`  
 'ndaki Bulunacak derlemenin adı. Bu dizenin biçimi <xref:System.Reflection.AssemblyName>için sınıf başvurusu sayfasında tanımlanmıştır.  
  
 `ppIUnk`  
 'ndaki `IMetadataAssemblyImport` arabirim işaretçilerine yerleştirilecek [IUnknown](/cpp/atl/iunknown) türünde bir dizi.  
  
 `cMax`  
 dışı `ppIUnk`yerleştirilebilecek en fazla arabirim işaretçisi sayısı.  
  
 `pcAssemblies`  
 dışı Döndürülen arabirim işaretçilerinin sayısı. Diğer bir deyişle, gerçekten `ppIUnk`yer alan arabirim işaretçilerinin sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` başarıyla döndürüldü.|  
|`S_FALSE`|Hiçbir derleme yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme adı verildiğinde `FindAssembliesByName` yöntemi, derleme başvurularını çözümlemek için standart kuralları izleyerek derlemeyi bulur. (Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`, çağıranın uygulama temeli ve özel arama yolu gibi bütünleştirilmiş kod çözümleyici bağlamının çeşitli yönlerini yapılandırmasına izin verir.  
  
 `FindAssembliesByName` yöntemi, derleme çözümleme mantığını çağırmak için CLR 'nin işlemde başlatılmasını gerektirir. Bu nedenle, `FindAssembliesByName`çağrılmadan önce [Coınitialeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (geçirme COINITEE_DEFAULT) yöntemini çağırmanız ve sonra [Counınitializecor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)çağrısı ile izlemeniz gerekir.  
  
 `FindAssembliesByName`, geçirilen derleme adı için derleme bildirimini içeren dosyaya bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) işaretçisi döndürür. Verilen derleme adı tam olarak belirtilmemişse (örneğin, bir sürüm içermiyorsa), birden çok derleme döndürülebilir.  
  
 `FindAssembliesByName`, derleme zamanında başvurulan bir derlemeyi bulmayı deneyen bir derleyici tarafından yaygın olarak kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
