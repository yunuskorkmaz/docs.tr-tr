---
title: "IMetaDataDispenserEx::SetOption Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 96810ba0eab99d1df58f0b68b85ef4da8ce7084e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption Yöntemi
Belirtilen seçenek geçerli meta veri kapsam için belirli bir değeri ayarlar. Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `optionId`  
 [in] Bir işaretçi olarak ayarlanması için seçeneği belirten bir GUID.  
  
 `pValue`  
 [in] Seçeneği belirlemek için kullanılacak bir değer. Bu değer türü belirtilen seçeneğin türünde bir değişken olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda kullanılabilir GUID'ler listeler, `optionId` parametresi ' in üzerine gelin ve karşılık gelen geçerli değerler `pValue` parametresi.  
  
|GUID|Açıklama|`pValue`Parametre|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Hangi öğelerin çoğaltmaları denetlenir denetler. Her çağırdığında bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yeni bir öğe oluşturan yöntemi, öğesi geçerli kapsamda zaten var olup olmadığını denetlemek için yöntemin sorun. Örneğin, varlığını kontrol edebilirsiniz `mdMethodDef` öğelerini; çağırdığınızda, bu durumda [Imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), yöntemi geçerli kapsamda zaten yok kontrol eder. Bu onay belirli bir yöntemin benzersiz olarak tanımlayan anahtar kullanır: üst türü, ad ve imza.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) numaralandırması.|  
|MetaDataRefToDefCheck|Öğeleri başvuran denetimleri tanımlarını dönüştürülür. Varsayılan olarak, meta veri altyapısı, kod başvuru yapılan öğe geçerli kapsamda tanımlanırsa öğenin tanımına başvuruda bulunulan öğe dönüştürerek iyileştirin.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) numaralandırması.|  
|MetaDataNotificationForTokenMovement|Hangi belirteci meta veri birleştirme sırasında gerçekleşen Eşitle denetimleri geri aramalar oluşturun. Kullanım [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) kurmaya yöntemi, [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimi.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) numaralandırması.|  
|MetaDataSetENC|Düzenle ve devam et (ÇÖZÜCÜ) davranışını denetler. Aynı anda yalnızca bir modu davranış ayarlanabilir.|UI4 türünde bir değişken olmalıdır ve bir değeri içermelidir [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) numaralandırması. Değer bir bit maskesi değil.|  
|MetaDataErrorIfEmitOutOfOrder|Geri aramalar hangi yayılan-genişletme-sıra hatalara neden denetler. Meta verileri bozuk yayma önemli değildir; Ancak, meta verileri meta veri altyapısı tarafından avantajlı bir sırada yayma, meta veriler daha kısadır ve daha verimli bir şekilde aranabilir. Kullanım `IMetaDataEmit::SetHandler` kurmaya yöntemi, [Imetadataerror](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) arabirimi.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir [Corerrorıfemitoutoforder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) numaralandırması.|  
|MetaDataImportOption|Hangi türde bir ÇÖZÜCÜ sırasında silinen öğeler bir numaralandırıcı tarafından alınır denetler.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir [Corımportoptions numaralandırması](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) numaralandırması.|  
|MetaDataThreadSafetyOptions|Meta veri altyapısı Okuyucu/Yazıcı kilitleri, böylece iş parçacığı güvenliği sağlama alacağını denetler. Varsayılan olarak, altyapı hiçbir kilit alınması için erişim tek çağıran tarafından iş parçacıklı olduğunu varsayar. İstemciler, uygun iş parçacığı eşitleme API meta verileri kullanarak koruma için sorumludur.|UI4 türünde bir değişken olmalıdır ve bir değeri içermelidir [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) numaralandırması. Değer bir bit maskesi değil.|  
|MetaDataGenerateTCEAdapters|Tür kitaplığı içeri Aktarıcı COM bağlantı noktası kapsayıcıları için sıkı şekilde bağlı olayı (TCE) bağdaştırıcıları oluşturup oluşturmayacağını denetler.|BOOL türünde bir değişken olmalıdır. Varsa `pValue` ayarlanır `true`, tür kitaplığı içeri Aktarıcı TCE bağdaştırıcıları oluşturur.|  
|MetaDataTypeLibImportNamespace|İçeri aktarılan tür kitaplığı için varsayılan olmayan ad alanını belirtir.|Bir null değer veya BSTR türünde bir değişken olmalıdır. Varsa `pValue` null değeri, geçerli ad ayarlanır; tersi, geçerli ad değişken 's BSTR türünde tutulan dizeye ayarlayın.|  
|MetaDataLinkerOptions|Bağlayıcı bir derlemeyi ya da .NET Framework modül dosyası oluşturup oluşturmayacağını denetler.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) numaralandırması.|  
|MetaDataRuntimeVersion|Ortak dil çalışma zamanı göre bu görüntüyü oluşturulmuş sürümünü belirtir. Sürüm "v1.0.3705" gibi bir dize olarak depolanır.|Bir null değer, bir VT_EMPTY değer veya BSTR türünde bir değişken olmalıdır. Varsa `pValue` olduğu çalışma zamanı sürümü null ayarlanır null. Varsa `pValue` VT_EMPTY, olan sürümü meta veri kod içinde çalıştığı Mscorwks.dll sürümünden çizilmiş bir varsayılan değere ayarlanır. Aksi halde, çalışma zamanı sürümü değişken 's BSTR türünde tutulan dizeye ayarlanır.|  
|MetaDataMergerOptions|Meta veri birleştirme seçeneklerini belirtir.|UI4 türünde bir değişken olmalıdır ve değerlerini bileşimini içermelidir `MergeFlags` CorHdr.h dosyasında tanımlanan numaralandırması.|  
|MetaDataPreserveLocalRefs|Yerel başvuruları tanımları içine en iyi duruma getirme devre dışı bırakır.|Değerleri bir birleşimini içermelidir [corlocalrefpreservation sabit](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) numaralandırması.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
