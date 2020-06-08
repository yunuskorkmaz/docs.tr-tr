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
ms.openlocfilehash: 28aea8534eed3bcd1f645844e28849be89e130d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501332"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption Yöntemi
Belirtilen seçeneği geçerli meta veri kapsamı için verilen bir değere ayarlar. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Aşağıdaki tabloda, parametrenin işaret edip kullanabileceği kullanılabilir GUID 'Ler `optionId` ve parametresi için karşılık gelen geçerli değerler listelenmiştir `pValue` .  
  
|GUID|Description|`pValue`Parametresinin|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Hangi öğelerin yinelenenlere denetleneceğini denetler. Yeni bir öğe oluşturan bir [ımetadatayayma](imetadataemit-interface.md) yöntemini her çağırdığınızda, yöntemin geçerli kapsamda zaten var olup olmadığını denetlemesini isteyebilirsiniz. Örneğin, öğelerin varlığını kontrol edebilirsiniz `mdMethodDef` ; Bu durumda, [ımetadatayayma::D efineMethod](imetadataemit-definemethod-method.md)' ı çağırdığınızda, yöntemin geçerli kapsamda zaten mevcut olmadığını kontrol eder. Bu denetim, belirli bir yöntemi benzersiz bir şekilde tanımlayan anahtarı kullanır: üst tür, ad ve imza.|UI4 türünde bir değişken olmalıdır ve sabit listesi [Için Corcheckduplicatesvalues](corcheckduplicatesfor-enumeration.md) değerlerinin bir birleşimini içermelidir.|  
|MetaDataRefToDefCheck|Hangi Başvurulmuş öğelerin tanımlara dönüştürüleceğini denetler. Varsayılan olarak, başvurulan öğe geçerli kapsamda tanımlanmazsa, meta veri altyapısı, başvurulan bir öğeyi tanımına dönüştürerek kodu iyileştirir.|UI4 türünde bir değişken olması gerekir ve [CorRefToDefCheck](correftodefcheck-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|Metadadtanocertificate Ationfortokentaşıması|Meta veri birleştirme sırasında oluşan belirteç yeniden eşlemelerinin geri çağırmalar üretmekte olduğunu denetler. [IMapToken](imaptoken-interface.md) arabiriminizi oluşturmak Için [ımetadatayayma:: SetHandler](imetadataemit-sethandler-method.md) metodunu kullanın.|UI4 türünde bir değişken olmalıdır ve [Cornotificationfortokentaşıması](cornotificationfortokenmovement-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataSetENC|Düzenle ve devam et (ENC) davranışını denetler. Tek seferde yalnızca bir davranış modu ayarlanabilir.|UI4 türünde bir değişken olmalıdır ve [CorSetENC](corsetenc-enumeration.md) numaralandırması değerini içermelidir. Değer bir bit maskesi değil.|  
|Metadataerrorifemıtoutoforder|Hangi sıralı olmayan hataların geri çağırmaları üretdiğini denetler. Meta verileri sıra dışı yayma önemli değildir; ancak meta verileri meta veri altyapısı tarafından sık sık kırmızı olan bir sırayla yayırsanız meta veriler daha kompakt olur ve bu nedenle daha etkin bir şekilde aranabilir. `IMetaDataEmit::SetHandler` [IMetaDataError](imetadataerror-interface.md) arabiriminizi oluşturmak için yöntemini kullanın.|UI4 türünde bir değişken olması gerekir ve [Corerrorifemıtoutoforder](corerrorifemitoutoforder-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|Metadataımportoption|Bir ENC sırasında silinen öğe türlerinin bir Numaralandırıcı tarafından alındığını denetler.|UI4 türünde bir değişken olmalıdır ve [CorImportOptions sabit](corimportoptions-enumeration.md) listesi numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataThreadSafetyOptions|Meta veri altyapısının okuyucu/yazıcı kilitlerini alıp almadığını denetler ve bu sayede iş parçacığı güvenliğini sağlar. Varsayılan olarak, altyapı, erişimin arayan tarafından tek iş parçacıklı olduğunu varsayar, dolayısıyla hiçbir kilit alınmaz. İstemciler, meta veri API 'SI kullanılırken uygun iş parçacığı eşitlemesini sürdürmekten sorumludur.|UI4 türünde bir değişken olmalıdır ve [CorThreadSafetyOptions](corthreadsafetyoptions-enumeration.md) sabit listesinin bir değerini içermesi gerekir. Değer bir bit maskesi değil.|  
|Metadatageneratetcebağdaştırıcıları|Tür Kitaplığı İçeri Aktarıcı 'nın COM bağlantı noktası kapsayıcıları için sıkı şekilde bağlanmış olay (TCE) bağdaştırıcılarını oluşturup üretmeyeceğini denetler.|BOOL türünde bir değişken olmalıdır. , `pValue` Olarak ayarlanırsa `true` , tür kitaplığı İçeri Aktarıcı TCe bağdaştırıcılarını üretir.|  
|Metadatatypelibımportnamespace|İçeri aktarılmakta olan tür kitaplığı için varsayılan olmayan bir ad alanı belirtir.|Null değer ya da BSTR türünde bir değişken olmalıdır. `pValue`Null bir değer ise, geçerli ad alanı null olarak ayarlanır; Aksi takdirde, geçerli ad alanı, VARIANT 'ıN BSTR türünde tutulan dizeye ayarlanır.|  
|Metaveriveri ınkeroptions|Bağlayıcının bir derleme veya .NET Framework modül dosyası oluşturup üretmeyeceğini denetler.|UI4 türünde bir değişken olması gerekir ve [CorLinkerOptions](corlinkeroptions-enumeration.md) numaralandırması değerlerinin bir birleşimini içermelidir.|  
|MetaDataRuntimeVersion|Bu görüntünün oluşturulduğu ortak dil çalışma zamanının sürümünü belirtir. Sürüm, "v 1.0.3705" gibi bir dize olarak depolanır.|Null bir değer, bir VT_EMPTY değeri veya BSTR türünde bir değişken olmalıdır. `pValue`Null ise, çalışma zamanı sürümü null olarak ayarlanır. `pValue`VT_EMPTY ise, sürüm, meta veri kodunun çalıştığı mscorwks. dll sürümünden çizilen bir varsayılan değere ayarlanır. Aksi takdirde, çalışma zamanı sürümü, VARIANT 'ın BSTR türünde tutulan dize olarak ayarlanır.|  
|MetaDataMergerOptions|Meta verileri birleştirme seçeneklerini belirtir.|UI4 türünde bir değişken olmalıdır ve, `MergeFlags` CorHdr. h dosyasında açıklanan numaralandırmanın değerlerinin bir birleşimini içermelidir.|  
|MetaDataPreserveLocalRefs|Yerel başvuruları tanımlarda iyileştirerek devre dışı bırakır.|[Corlocalrefkoruma](corlocalrefpreservation-enumeration.md) numaralandırması değerlerinin birleşimini içermelidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenserEx Arabirimi](imetadatadispenserex-interface.md)
- [IMetaDataDispenser Yöntemi](imetadatadispenser-interface.md)
