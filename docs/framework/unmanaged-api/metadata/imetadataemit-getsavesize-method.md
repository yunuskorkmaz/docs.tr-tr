---
title: IMetaDataEmit::GetSaveSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434326"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize Metodu
Derlemenin tahmini ikili boyutunu ve geçerli kapsamdaki meta verilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fSave`  
 'ndaki Doğru veya yaklaşık bir boyut almak isteyip istemediğinizi belirten [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) numaralandırması değeri. Yalnızca üç değer geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:  
  
- cssAccurate, tam kaydetme boyutunu döndürür ancak daha uzun süre içinde hesaplama gerçekleştirir.  
  
- cssQuick, güvenlik için doldurulmuş bir boyut döndürür, ancak hesaplanması daha az zaman alır.  
  
- cssDiscardTransientCAs, discardable özel öznitelikleri `GetSaveSize` olduğunu söyler.  
  
 `pdwSaveSize`  
 dışı Dosyanın kaydedilmesi için gereken boyuta yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSaveSize`, geçerli kapsamdaki derlemeyi ve tüm meta verilerini kaydetmek için gereken alanı bayt cinsinden hesaplar. ( [Imetadatayayma:: SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metoduna yapılan bir çağrı, bu sayıda bayt yaymalıdır.)  
  
 Arayan, [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimini ( [ımetadatayayma:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) veya [ımetadatayayma:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)) uygularsa, `GetSaveSize` iyileştirmek ve sıkıştırmak için meta veriler üzerinde iki geçiş gerçekleştirilir. Aksi takdirde, iyileştirmeler yapılmaz.  
  
 İyileştirme gerçekleştirilirse, ilk geçiş yalnızca meta veri yapılarını sıralar ve içeri aktarma zamanı aramalarının performansını ayarlar. Bu adım genellikle, sonraki başvuru için araç tarafından tutulan belirteçlerin geçersiz kılınmasıyla birlikte kayıtları taşımaya neden olur. Ancak meta veriler, ikinci pass öğesine kadar bu belirteç değişikliklerini çağırana bildirir. İkinci geçişte, en iyi duruma getirme (erken bağlama) `mdTypeRef` ve `mdMemberRef` belirteçleri geçerli meta veri kapsamında bildirilmeyen bir türe veya üyeye olduğunda, verilerin genel boyutunu azaltmaya yönelik çeşitli iyileştirmeler gerçekleştirilir. Bu geçişte, belirteç eşlemesinin başka bir turu oluşur. Bu geçiş sonrasında, meta veri altyapısı, değişen belirteç değerlerinin `IMapToken` arabirimi aracılığıyla çağrıyı yapana bildirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
