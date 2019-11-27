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
ms.openlocfilehash: bc30f9fb120db92ccfc1e7dd0560b3fe18c54b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432735"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption Yöntemi
Belirtilen seçeneği geçerli meta veri kapsamı için verilen bir değere ayarlar. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `optionId`  
 'ndaki Ayarlanacak seçeneği belirten bir GUID işaretçisi.  
  
 `pValue`  
 'ndaki Seçeneğini ayarlamak için kullanılacak değer. Bu değerin türü, belirtilen seçeneğin türünün bir değişkeni olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda `optionId` parametresinin işaret edip `pValue` parametresi için karşılık gelen geçerli değerler listelenmektedir.  
  
|GUID|Açıklama|`pValue` parametresi|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Hangi öğelerin yinelenenlere denetleneceğini denetler. Yeni bir öğe oluşturan bir [ımetadatayayma](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yöntemini her çağırdığınızda, yöntemin geçerli kapsamda zaten var olup olmadığını denetlemesini isteyebilirsiniz. Örneğin, `mdMethodDef` öğelerinin varlığını kontrol edebilirsiniz; Bu durumda, [ımetadatayayma::D efineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)' ı çağırdığınızda, yöntemin geçerli kapsamda zaten mevcut olmadığını kontrol eder. Bu denetim, belirli bir yöntemi benzersiz bir şekilde tanımlayan anahtarı kullanır: üst tür, ad ve imza.|UI4 türünde bir değişken olmalıdır ve sabit listesi [Için Corcheckduplicatesvalues](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) değerlerinin bir birleşimini içermelidir.|  
|MetaDataRefToDefCheck|Hangi Başvurulmuş öğelerin tanımlara dönüştürüleceğini denetler. Varsayılan olarak, başvurulan öğe geçerli kapsamda tanımlanmazsa, meta veri altyapısı, başvurulan bir öğeyi tanımına dönüştürerek kodu iyileştirir.|UI4 türünde bir değişken olması gerekir ve [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|Metadadtanocertificate Ationfortokentaşıması|Meta veri birleştirme sırasında oluşan belirteç yeniden eşlemelerinin geri çağırmalar üretmekte olduğunu denetler. [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabiriminizi oluşturmak Için [ımetadatayayma:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metodunu kullanın.|UI4 türünde bir değişken olmalıdır ve [Cornotificationfortokentaşıması](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataSetENC|Düzenle ve devam et (ENC) davranışını denetler. Tek seferde yalnızca bir davranış modu ayarlanabilir.|UI4 türünde bir değişken olmalıdır ve [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) numaralandırması değerini içermelidir. Değer bir bit maskesi değil.|  
|Metadataerrorifemıtoutoforder|Hangi sıralı olmayan hataların geri çağırmaları üretdiğini denetler. Meta verileri sıra dışı yayma önemli değildir; ancak meta verileri meta veri altyapısı tarafından sık sık kırmızı olan bir sırayla yayırsanız meta veriler daha kompakt olur ve bu nedenle daha etkin bir şekilde aranabilir. [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) arabiriminizi oluşturmak için `IMetaDataEmit::SetHandler` yöntemini kullanın.|UI4 türünde bir değişken olması gerekir ve [Corerrorifemıtoutoforder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|Metadataımportoption|Bir ENC sırasında silinen öğe türlerinin bir Numaralandırıcı tarafından alındığını denetler.|UI4 türünde bir değişken olmalıdır ve [CorImportOptions sabit](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) listesi numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataThreadSafetyOptions|Meta veri altyapısının okuyucu/yazıcı kilitlerini alıp almadığını denetler ve bu sayede iş parçacığı güvenliğini sağlar. Varsayılan olarak, altyapı, erişimin arayan tarafından tek iş parçacıklı olduğunu varsayar, dolayısıyla hiçbir kilit alınmaz. İstemciler, meta veri API 'SI kullanılırken uygun iş parçacığı eşitlemesini sürdürmekten sorumludur.|UI4 türünde bir değişken olmalıdır ve [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) sabit listesinin bir değerini içermesi gerekir. Değer bir bit maskesi değil.|  
|Metadatageneratetcebağdaştırıcıları|Tür Kitaplığı İçeri Aktarıcı 'nın COM bağlantı noktası kapsayıcıları için sıkı şekilde bağlanmış olay (TCE) bağdaştırıcılarını oluşturup üretmeyeceğini denetler.|BOOL türünde bir değişken olmalıdır. `pValue`, `true`olarak ayarlanırsa, tür kitaplığı İçeri Aktarıcı TCE bağdaştırıcılarını oluşturur.|  
|Metadatatypelibımportnamespace|İçeri aktarılmakta olan tür kitaplığı için varsayılan olmayan bir ad alanı belirtir.|Null değer ya da BSTR türünde bir değişken olmalıdır. `pValue` null bir değer ise, geçerli ad alanı null olarak ayarlanır; Aksi takdirde, geçerli ad alanı, VARIANT 'ın BSTR türünde tutulan dizeye ayarlanır.|  
|Metaveriveri ınkeroptions|Bağlayıcının bir derleme veya .NET Framework modül dosyası oluşturup üretmeyeceğini denetler.|UI4 türünde bir değişken olması gerekir ve [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataRuntimeVersion|Bu görüntünün oluşturulduğu ortak dil çalışma zamanının sürümünü belirtir. Sürüm, "v 1.0.3705" gibi bir dize olarak depolanır.|Null bir değer, bir VT_EMPTY değeri veya BSTR türünde bir değişken olmalıdır. `pValue` null ise, çalışma zamanı sürümü null olarak ayarlanır. `pValue` VT_EMPTY ise, sürüm, meta veri kodunun çalıştığı mscorwks. dll sürümünden çizilen bir varsayılan değere ayarlanır. Aksi takdirde, çalışma zamanı sürümü, VARIANT 'ın BSTR türünde tutulan dize olarak ayarlanır.|  
|MetaDataMergerOptions|Meta verileri birleştirme seçeneklerini belirtir.|UI4 türünde bir değişken olmalıdır ve CorHdr. h dosyasında açıklanan `MergeFlags` numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataPreserveLocalRefs|Yerel başvuruları tanımlarda iyileştirerek devre dışı bırakır.|[Corlocalrefkoruma](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) numaralandırması değerlerinin birleşimini içermelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
