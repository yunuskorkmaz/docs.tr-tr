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
ms.openlocfilehash: a6c7bf332d829a440fe216756f7a23ec1277e6c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449292"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
Belirtilen derleme dizisi alır `szAssemblyName` başvurularını çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kurallar kullanarak parametresi.  
  
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
 [in] Verilen derleme için aranacak kök dizininde. Bu değer ayarlanırsa `null`, `FindAssembliesByName` yalnızca genel derleme önbelleğinde derleme için arar.  
  
 `szPrivateBin`  
 [in] Noktalı virgülle ayrılmış alt dizinleri (örneğin, "depo; Kutu2"), derleme için aranacağı kök dizininin altında bir listesi. Algılama kuralları varsayılan olarak belirtilen yanı sıra bu dizinleri sıklığının.  
  
 `szAssemblyName`  
 [in] Bulunacak derleme adı. Bu dize biçimi sınıfı başvuru sayfası için tanımlanan <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Türünde bir dizi <<!--zzxref:IUnknown --> `IUnknown`> yerleştirileceği `IMetadataAssemblyImport` arabirim işaretçileri.  
  
 `cMax`  
 [out] Yerleştirilebilir arabirim işaretçileri en fazla `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Döndürülen arabirim işaretçileri sayısı. Diğer bir deyişle, arabirim işaretçileri sayısı gerçekte yerleştirilen `ppIUnk`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` başarıyla döndürüldü.|  
|`S_FALSE`|Hiçbir derlemeleri vardır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derleme adı verilen `FindAssembliesByName` yöntemi derleme başvurularını çözmek için standart kurallar izleyerek derlemeyi bulur. (Daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` arayanın derleme Çözümleyicisi bağlamı uygulama temel ve özel arama yolu gibi çeşitli yönlerini yapılandırmalarını izin verir.  
  
 `FindAssembliesByName` Yöntemi derleme çözümleme mantığı çağırmak için işlemin başlatılması CLR gerektirir. Bu nedenle, çağırmalısınız [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT geçirme) çağırmadan önce `FindAssembliesByName`ve ardından bir çağrı izleyin [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` döndüren bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) geçirilen derleme adı derleme bildirimi içeren dosyanın işaretçi. Verilen derleme adı (örneğin bir sürüm içermiyorsa) tam olarak belirtilmezse, birden çok derleme döndürülen.  
  
 `FindAssembliesByName` derleme zamanında başvurulan bir derleme bulmaya çalışır bir derleyici tarafından yaygın olarak kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
