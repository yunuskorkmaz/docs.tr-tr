---
title: IMetaDataDispenserEx::SetOption Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175908"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption Yöntemi
Geçerli meta veri kapsamı için belirtilen seçeneği belirli bir değere ayarlar. Seçenek, geçerli meta veri kapsamına yapılan çağrıların nasıl işleneceğini denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `optionId`  
 [içinde] Ayarlanacak seçeneği belirten bir GUID işaretçisi.  
  
 `pValue`  
 [içinde] Seçeneği ayarlamak için kullanılacak değer. Bu değerin türü, belirtilen seçeneğin türünün bir varyantı olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda, parametrenin `optionId` işaret edebileceği kullanılabilir GUID'ler ve `pValue` parametre için karşılık gelen geçerli değerler listelenmektedir.  
  
|GUID|Açıklama|`pValue`Parametre|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Yinelenenler için hangi öğelerin denetlenir denetimleri. Yeni bir öğe oluşturan bir [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yöntemini her çağırdığınızda, öğenin geçerli kapsamda zaten var olup olmadığını denetlemek için yöntem isteyebilirsiniz. Örneğin, öğelerin `mdMethodDef` varlığını denetleyebilirsiniz; Bu durumda, [IMetaDataEmit::DefineMethod'u](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)aradiğinizde, yöntemin geçerli kapsamda zaten var olup olmadığını denetler. Bu denetim, belirli bir yöntemi benzersiz olarak tanımlayan anahtarı kullanır: üst yazı, ad ve imza.|Tip UI4'ün bir varyantı olmalı ve [numaralandırma için CorCheckDuplicates](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) değerlerinin bir birleşimini içermelidir.|  
|MetaDataReftodefcheck|Başvurulan öğelerin tanımlarına dönüştürüldüğü denetimler. Varsayılan olarak, başvurulan öğe geçerli kapsamda gerçekten tanımlanmışsa, başvurulan bir öğeyi tanımına dönüştürerek kodu en iyi duruma getirecektir.|Tip UI4'ün bir varyantı olmalı ve [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) numaralandırma değerlerinin bir birleşimini içermelidir.|  
|MetaDataNotificationForTokenMovement|Meta veri birleştirme sırasında oluşan yeniden eşlemleri gösteren denetimler geri arama oluşturur. [IMapEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemini kullanarak [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabiriminizi belirleyin.|Tip UI4'ün bir varyantı olmalı ve [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) numaralandırma değerlerinin bir birleşimini içermelidir.|  
|MetaDataSetENC|Edit-and-continue (ENC) davranışını denetler. Aynı anda yalnızca bir davranış biçimi ayarlanabilir.|Tip UI4'ün bir varyantı olmalı ve [KorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) numaralandırmasının bir değerini içermelidir. Değer bir bitmask değildir.|  
|MetaDataErrorIfEmitOutOfOrder|Yayılan-out-of-order hataları geri aramaları oluşturmak denetimleri. Meta verileri sıra dışı yayan ölümcül değildir; ancak, meta veri altyapısı tarafından tercih edilen bir sırada meta veri yontuyorsanız, meta veriler daha kompakttır ve bu nedenle daha verimli bir şekilde aranabilir. `IMetaDataEmit::SetHandler` [iMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) arabiriminizi oluşturmak için yöntemi kullanın.|Tür UI4'ün bir varyantı olmalı ve [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) numaralandırma değerlerinin bir birleşimini içermelidir.|  
|MetaDataImportOption|ENC sırasında silinen öğelerin hangi türlerinin bir sayısallaştırıcı tarafından alındığını denetler.|Tip UI4'ün bir varyantı olmalı ve [CorImportOptions Numaralandırma](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) numaralandırma değerlerinin bir birleşimini içermelidir.|  
|MetaDataThreadSafetyOptions|Meta veri altyapısının okuyucu/yazar kilitleri alıp almadığını kontrol eder ve böylece iş parçacığı güvenliğini sağlar. Varsayılan olarak, motor erişimin arayan tarafından tek iş parçacığı olduğunu varsayar, bu nedenle kilit alınamaz. İstemciler, meta veri API'sını kullanırken uygun iş parçacığı eşitlemeyisağlamaktan sorumludur.|Tip UI4'ün bir varyantı olmalı ve [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) numaralandırmasının bir değerini içermelidir. Değer bir bitmask değildir.|  
|MetaDataGenerateTCEAdapters|Tür kitaplığı aktarıcısının COM bağlantı noktası kapsayıcıları için sıkıca birleştirilmiş olay (TCE) bağdaştırıcılarını oluşturup oluşturmayacağını denetler.|BOOL tipinin bir çeşidi olmalıdır. Olarak `pValue` `true`ayarlanırsa, tür kitaplığı içe aktarıcı TCE bağdaştırıcıları oluşturur.|  
|MetaDataTypeLibImportNamespace|İçe aktarılan tür kitaplığı için varsayılan olmayan bir ad alanı belirtir.|Null değeri veya BSTR tipinin bir varyantı olmalıdır. Null `pValue` değeri ise, geçerli ad alanı null olarak ayarlanır; aksi takdirde, geçerli ad alanı varyantın BSTR türünde tutulan dize ayarlanır.|  
|MetaDataLinkerSeçenekleri|Bağlayıcının bir derleme mi yoksa .NET Framework modülü dosyası mı oluşturması gerektiğini denetler.|Tür UI4'ün bir varyantı olmalı ve [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) numaralandırma değerlerinin bir birleşimini içermelidir.|  
|MetaDataRuntimeVersion|Bu görüntünün oluşturulabildiği ortak dil çalışma zamanının sürümünü belirtir. Sürüm , "v1.0.3705" gibi bir dize olarak depolanır.|Null değeri, VT_EMPTY değeri veya BSTR tipi bir tür olmalıdır. Null `pValue` ise, çalışma zamanı sürümü null olarak ayarlanır. VT_EMPTY `pValue` ise, sürüm, meta veri kodunun çalıştırıldığı Mscorwks.dll sürümünden çekilen varsayılan değere ayarlanır. Aksi takdirde, çalışma zamanı sürümü varyantın BSTR türünde tutulan dize ayarlanır.|  
|MetaDataMergerOptions|Meta verileri birleştirmek için seçenekleri belirtir.|Tür UI4'ün bir varyantı olmalı ve CorHdr.h dosyasında açıklanan numaralandırma değerlerinin `MergeFlags` bir birleşimini içermelidir.|  
|MetaDataPreserveLocalRefs|Yerel başvuruları tanımlara en iyi duruma getirerek devre dışı bırakma.|[CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) numaralandırma değerlerinin bir birleşimini içermelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
