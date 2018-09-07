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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9babd5e50166be2c2d1b7bc32a5fc11d1ad8ba9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086416"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
Derlemeler belirli bir dizisini alır `szAssemblyName` başvurularını çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kurallar kullanılarak parametre.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szAppBase`  
 [in] Belirtilen derleme için aranacak kök dizini. Bu değer ayarlanırsa `null`, `FindAssembliesByName` yalnızca genel derleme önbelleğinde derleme için görünür.  
  
 `szPrivateBin`  
 [in] Noktalı virgül ile ayrılmış alt dizinleri (örneğin, "depo; bin2"), derleme için aranacak kök dizininin altındaki bir listesi. Bu dizinler, varsayılan algılama kurallarını belirtilenlerin yanı sıra araştırıldığı.  
  
 `szAssemblyName`  
 [in] Bulunacak derlemenin adı. Bu dizenin biçimi sınıf başvurusu sayfasında tanımlanan <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Türünde bir dizi [IUnknown](/cpp/atl/iunknown) yerleştirileceği `IMetadataAssemblyImport` arabirim işaretçisi.  
  
 `cMax`  
 [out] Yerleştirilebilir arabirim işaretçilerini sayısı `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Döndürülen arabirim işaretçilerini sayısı. Diğer bir deyişle, arabirim işaretçilerini sayısı gerçekte yerleştirilen `ppIUnk`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` başarıyla döndürüldü.|  
|`S_FALSE`|Bütünleştirilmiş kod yok vardır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bütünleştirilmiş kod adı verilir `FindAssembliesByName` yöntemi derleme başvurularını çözümlemek için standart kuralları izleyerek derlemeyi bulur. (Daha fazla bilgi için [çalışma zamanı derlemeleri nasıl konumlandırır](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` derleme Çözümleyicisi bağlamı, uygulama temel ve özel arama yolu gibi çeşitli yönlerini yapılandırmak çağıranın izin verir.  
  
 `FindAssembliesByName` Yöntem CLR'nin işlemdeki bütünleştirilmiş kod çözümleme mantıksal çağırmak için başlatılması gerektirir. Bu nedenle, çağırmalıdır [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT geçirme) çağırmadan önce `FindAssembliesByName`ve ardından bir çağrı ile izleyin [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` döndürür bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) geçirilen derleme adı için derleme bildirimini içeren dosyayı işaretçisi. Belirtilen derleme adı tam olarak (örneğin bir sürüm içermiyorsa) belirtilmezse, birden çok derleme döndürülen.  
  
 `FindAssembliesByName` başvurulan derlemenin derleme zamanında bulmaya çalışır bir derleyici tarafından yaygın olarak kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
