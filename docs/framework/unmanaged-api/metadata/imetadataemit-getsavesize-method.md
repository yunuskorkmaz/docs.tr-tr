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
ms.openlocfilehash: 0a283c837e23ab1aafd3545df1dfe8a267de0557
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501293"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize Metodu
Derlemenin tahmini ikili boyutunu ve geçerli kapsamdaki meta verilerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fSave`  
 'ndaki Doğru veya yaklaşık bir boyut almak isteyip istemediğinizi belirten [CorSaveSize](corsavesize-enumeration.md) numaralandırması değeri. Yalnızca üç değer geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:  
  
- cssAccurate, tam kaydetme boyutunu döndürür ancak daha uzun süre içinde hesaplama gerçekleştirir.  
  
- cssQuick, güvenlik için doldurulmuş bir boyut döndürür, ancak hesaplanması daha az zaman alır.  
  
- cssDiscardTransientCAs `GetSaveSize` , discardable özel öznitelikleri oluşturabildiğini söyler.  
  
 `pdwSaveSize`  
 dışı Dosyanın kaydedilmesi için gereken boyuta yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSaveSize`derlemeyi ve geçerli kapsamdaki tüm meta verilerini kaydetmek için gereken alanı bayt cinsinden hesaplar. ( [Imetadatayayma:: SaveToStream](imetadataemit-savetostream-method.md) metoduna yapılan bir çağrı, bu sayıda bayt yaymalıdır.)  
  
 Arayan, [IMapToken](imaptoken-interface.md) arabirimini ( [ımetadatayayma:: SetHandler](imetadataemit-sethandler-method.md) veya [ımetadatayayma:: Merge](imetadataemit-merge-method.md)) uygularsa, `GetSaveSize` en uygun hale getirmek ve sıkıştırmak için meta veriler üzerinde iki geçiş gerçekleştirir. Aksi takdirde, iyileştirmeler yapılmaz.  
  
 İyileştirme gerçekleştirilirse, ilk geçiş yalnızca meta veri yapılarını sıralar ve içeri aktarma zamanı aramalarının performansını ayarlar. Bu adım genellikle, sonraki başvuru için araç tarafından tutulan belirteçlerin geçersiz kılınmasıyla birlikte kayıtları taşımaya neden olur. Ancak meta veriler, ikinci pass öğesine kadar bu belirteç değişikliklerini çağırana bildirir. İkinci geçişte, başvurunun en iyi duruma getirilmesi (erken bağlama) `mdTypeRef` ve `mdMemberRef` belirteçlerin geçerli meta veri kapsamında bildirildiği bir türe veya üyeye olması gibi, meta verilerin genel boyutunu azaltmaya yönelik çeşitli iyileştirmeler yapılır. Bu geçişte, belirteç eşlemesinin başka bir turu oluşur. Bu geçiş işleminden sonra, meta veri altyapısı, `IMapToken` değiştirilen herhangi bir belirteç değerinin arabiriminden, bu çağrıyı yapana bildirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
