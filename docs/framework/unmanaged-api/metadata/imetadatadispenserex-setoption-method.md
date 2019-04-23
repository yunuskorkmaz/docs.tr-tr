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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9869efee18549c3d0c8b9ee9ca27cf31c1ccf452
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197119"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption Yöntemi
Belirtilen seçeneği geçerli meta veri kapsam için belirli bir değere ayarlar. Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `optionId`  
 [in] Ayarlanacak seçenek belirten bir GUID için bir işaretçi.  
  
 `pValue`  
 [in] Seçeneğini ayarlamak için kullanılacak değer. Bu değerin türü, belirtilen seçeneğin türünde bir değişken olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda kullanılabilir GUID'leri listelenmektedir, `optionId` parametresi işaret edebilir ve karşılık gelen geçerli değerleri `pValue` parametresi.  
  
|GUID|Açıklama|`pValue` Parametre|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Çoğaltmaları alınan hangi öğeleri denetler. Her çağırdığında bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yeni bir öğe oluşturan yöntemi öğesi geçerli kapsamda zaten mevcut olup olmadığını denetlemek için yöntemin sorabileceğiniz. Örneğin, varlığını kontrol edebilirsiniz `mdMethodDef` öğeleri; çağırdığınızda bu durumda, [Imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), yöntem geçerli kapsamda zaten yok kontrol eder. Bu denetimi, belirli bir yöntem benzersiz olarak tanımlayan anahtar kullanır: üst türü, adı ve imzası.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) sabit listesi.|  
|MetaDataRefToDefCheck|Başvurulan öğeleri denetimleri tanımları dönüştürülür. Varsayılan olarak, meta veri altyapısı, kod başvurulan öğenin geçerli kapsamda tanımlanmışsa başvuru yapılan öğe tanımına dönüştürerek iyileştirin.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) sabit listesi.|  
|MetaDataNotificationForTokenMovement|Geri çağırmaları hangi belirteci yeniden eşleyen bir meta veri birleştirme sırasında gerçekleşen denetimleri oluşturur. Kullanım [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemi oluşturmak için [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimi.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) sabit listesi.|  
|MetaDataSetENC|Düzenle ve devam et (ENC) davranışını denetler. Aynı anda yalnızca bir modu davranışı ayarlayabilirsiniz.|UI4 türünde bir değişken olmalıdır ve değerini içermelidir [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) sabit listesi. Değeri bir bit maskesi değil.|  
|MetaDataErrorIfEmitOutOfOrder|Denetimleri geri çağırmaları hangi yayılan out-Düzen hatalar oluşturur. Sıralama dışına çıkan meta veriyi yaymak önemli değildir; Ancak, meta verileri meta veri altyapısı tarafından stadyumlarda bir sırada yayma, meta veriler daha kısadır ve daha verimli bir şekilde aranabilir. Kullanım `IMetaDataEmit::SetHandler` yöntemi oluşturmak için [Imetadataerror](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) arabirimi.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir [Corerrorıfemitoutoforder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) sabit listesi.|  
|MetaDataImportOption|Hangi türde bir ENC sırasında silinen öğeler tarafından bir numaralandırıcı alınır denetler.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir [Corımportoptions numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) sabit listesi.|  
|MetaDataThreadSafetyOptions|Meta veri altyapısı Okuyucu/Yazıcı kilitleri, böylece iş parçacığı güvenliği sağlama alacağını denetler. Varsayılan olarak, altyapı, kilit alınması için erişim arayan tarafından tek hiper iş parçacıklı olduğu varsayılır. İstemciler, uygun iş parçacığı eşitleme meta veri API'si kullanılırken sürdürmekten sorumludur.|UI4 türünde bir değişken olmalıdır ve değerini içermelidir [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) sabit listesi. Değeri bir bit maskesi değil.|  
|MetaDataGenerateTCEAdapters|Tür kitaplığı içeri Aktarıcı COM bağlantı noktası kapsayıcılar için sıkı şekilde bağlı olay (TCE) bağdaştırıcıları oluşturması gerekip gerekmediğini denetler.|BOOL türünde bir değişken olmalıdır. Varsa `pValue` ayarlanır `true`, tür kitaplığı içeri Aktarıcı TCE bağdaştırıcıları oluşturur.|  
|MetaDataTypeLibImportNamespace|İçeri aktarılan tür kitaplığı için bir varsayılan olmayan ad alanını belirtir.|Null değer veya BSTR türünde bir değişken olmalıdır. Varsa `pValue` bir null değer, geçerli ad alanı ayarlama için null; Aksi takdirde, geçerli ad değişken 's BSTR türünde tutulan dizeye ayarlayın.|  
|MetaDataLinkerOptions|Bir derlemeyi veya .NET Framework modül dosyası bağlayıcı oluşturması gerekip gerekmediğini denetler.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) sabit listesi.|  
|MetaDataRuntimeVersion|Bu görüntü karşı oluşturulmuş ortak dil çalışma zamanı sürümünü belirtir. Sürümü "v1.0.3705" gibi bir dize olarak depolanır.|Null değeri, VT_EMPTY değeri veya BSTR türünde bir değişken olmalıdır. Varsa `pValue` olan çalışma zamanı sürümü null ayarlanır null. Varsa `pValue` VT_EMPTY, olan sürüm meta verileri kod içinde çalıştığı Mscorwks.dll sürümünden çizilmiş bir varsayılan değere ayarlanır. Aksi takdirde, çalışma zamanı sürümü değişken 's BSTR türünde tutulan dizeyi ayarlanır.|  
|MetaDataMergerOptions|Meta veri birleştirme seçeneklerini belirtir.|UI4 türünde bir değişken olmalıdır ve değerlerinin bir birleşimini içermelidir `MergeFlags` CorHdr.h dosyasında tanımlanan sabit listesi.|  
|MetaDataPreserveLocalRefs|Yerel başvuruyu tanımları en iyi duruma getirme devre dışı bırakır.|Değerlerinin bir birleşimini içermelidir [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) sabit listesi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
