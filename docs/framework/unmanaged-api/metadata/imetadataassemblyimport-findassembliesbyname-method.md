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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177794"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
Başvuruları çözmek için ortak dil `szAssemblyName` çalışma zamanı (CLR) tarafından kullanılan standart kuralları kullanarak, belirtilen parametreye sahip bir dizi derleme alır.  
  
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
 [içinde] Verilen derlemeiçin aramak için kök dizin. Bu değer , `null`yalnızca `FindAssembliesByName` derleme için genel montaj önbelleğinde görünecek şekilde ayarlanırsa.  
  
 `szPrivateBin`  
 [içinde] Alt dizinin altında, derlemenin arandığı yarı sütunlu sınırlı alt dizinlerin (örneğin, "bin2") listesi. Bu dizinler, varsayılan sondalama kurallarında belirtilenlere ek olarak incelenir.  
  
 `szAssemblyName`  
 [içinde] Bulmak için derleme adı. Bu dize biçimi için <xref:System.Reflection.AssemblyName>sınıf başvuru sayfasında tanımlanır.  
  
 `ppIUnk`  
 [içinde] Arabirim işaretçileri koymak için [tip IUnknown](/cpp/atl/iunknown) bir dizi. `IMetadataAssemblyImport`  
  
 `cMax`  
 [çıkış] Yerleştirilebilen en fazla arayüz işaretçisi `ppIUnk`sayısı.  
  
 `pcAssemblies`  
 [çıkış] Döndürülen arabirim işaretçilerinin sayısı. Diğer bir deyişle, aslında yerleştirilen arabirim işaretçilerinin `ppIUnk`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`başarıyla döndürülür.|  
|`S_FALSE`|Meclis falan yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derleme adı `FindAssembliesByName` verildiğinde, yöntem derleme başvurularını çözmek için standart kuralları izleyerek derlemeyi bulur. (Daha fazla bilgi [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'a](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)bakın.) `FindAssembliesByName` arayanın, uygulama tabanı ve özel arama yolu gibi derleme çözümleyici bağlamının çeşitli yönlerini yapılandırmasına olanak tanır.  
  
 Yöntem, `FindAssembliesByName` derleme çözümleme mantığını çağırmak için CLR'nin işlemde başlatılmasını gerektirir. Bu nedenle, aramadan `FindAssembliesByName`önce [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT geçen) aramanız ve ardından [CoUninitializeCor'a](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)bir çağrı ile izlemeniz gerekir.  
  
 `FindAssembliesByName`Geçirilen derleme adının montaj bildirimini içeren dosyaya bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) işaretçisi verir. Verilen derleme adı tam olarak belirtilmemişse (örneğin, bir sürüm içermiyorsa), birden çok derleme döndürülebilir.  
  
 `FindAssembliesByName`genellikle derleme zamanında başvurulan bir derleme bulmaya çalışan bir derleyici tarafından kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
