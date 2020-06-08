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
ms.openlocfilehash: d2693a94f02214df6d7265b26e3d70d91adcf8a7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503841"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
`szAssemblyName`Başvuruları çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kuralları kullanarak belirtilen parametreye sahip derlemelerin dizisini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Verilen derlemenin aranacağı kök dizin. Bu değer olarak ayarlandıysa `null` , `FindAssembliesByName` yalnızca derleme için genel derleme önbelleğinde görünür.  
  
 `szPrivateBin`  
 'ndaki Derlemenin aranacağı kök dizin altında, noktalı virgülle ayrılmış alt dizinlerin (örneğin, "bin; bin2") bir listesi. Bu dizinler, varsayılan yoklama kurallarında belirtienlere ek olarak araştırlanır.  
  
 `szAssemblyName`  
 'ndaki Bulunacak derlemenin adı. Bu dizenin biçimi için sınıf başvurusu sayfasında tanımlanmıştır <xref:System.Reflection.AssemblyName> .  
  
 `ppIUnk`  
 'ndaki Arabirim işaretçilerine yerleştirilecek [IUnknown](/cpp/atl/iunknown) türünde bir dizi `IMetadataAssemblyImport` .  
  
 `cMax`  
 dışı İçine yerleştirilebilecek en fazla arabirim işaretçisi sayısı `ppIUnk` .  
  
 `pcAssemblies`  
 dışı Döndürülen arabirim işaretçilerinin sayısı. Diğer bir deyişle, gerçekte içine yerleştirilmiş olan arabirim işaretçilerinin sayısı `ppIUnk` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`başarıyla döndürüldü.|  
|`S_FALSE`|Hiçbir derleme yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme adı verildiğinde, yöntem derleme `FindAssembliesByName` başvurularını çözümlemek için standart kuralları izleyerek derlemeyi bulur. (Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`çağıranın, uygulama temeli ve özel arama yolu gibi bütünleştirilmiş kod çözümleyici bağlamının çeşitli yönlerini yapılandırmasına izin verir.  
  
 `FindAssembliesByName`Yöntemi, derleme çözümleme mantığını çağırmak IÇIN clr 'nin işlemde başlatılmasını gerektirir. Bu nedenle, çağrılmadan önce [Coınitialeee](../hosting/coinitializeee-function.md) (geçirme COINITEE_DEFAULT) yöntemini çağırmanız `FindAssembliesByName` ve sonra [Counınitializecor](../hosting/couninitializecor-function.md)çağrısı ile izlemeniz gerekir.  
  
 `FindAssembliesByName`geçirilen derleme adı için derleme bildirimini içeren dosyaya bir [IMetaDataImport](imetadataimport-interface.md) işaretçisi döndürür. Verilen derleme adı tam olarak belirtilmemişse (örneğin, bir sürüm içermiyorsa), birden çok derleme döndürülebilir.  
  
 `FindAssembliesByName`, derleme zamanında başvurulan bir derlemeyi bulmayı deneyen bir derleyici tarafından yaygın olarak kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
