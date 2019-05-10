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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21f6c07976198416bff6e8e2a1789e4ccbf5ca55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665005"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize Metodu
Derleme meta verilerini ve ikili tahmini boyutu geçerli kapsamda alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fSave`  
 [in] Değerini [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) bir doğru ya da yaklaşık boyutunu almak belirten sabit listesi. Yalnızca üç değerler geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:  
  
- cssAccurate tam boyutu kaydetme döndürür ancak hesaplamak için uzun sürer.  
  
- cssQuick güvenliği için doldurulan bir boyutunu döndürür ancak hesaplamak için daha kısa sürer.  
  
- cssDiscardTransientCAs söyler `GetSaveSize` discardable özel öznitelikler yerine atabilirsiniz.  
  
 `pdwSaveSize`  
 [out] Dosyayı kaydetmek için gereken boyut için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSaveSize` , derleme ve tüm meta veriler geçerli kapsamda kaydetmek için bayt cinsinden gereken alanı hesaplar. (Bir çağrı [Imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) yöntemi bu bayt sayısını yayması.)  
  
 Çağıranın uyguluyorsa [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimi (aracılığıyla [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) veya [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` iki geçiş yapar en iyi duruma getirmek ve bunu sıkıştırmak için meta verileri. Aksi takdirde, hiçbir iyileştirmeleri gerçekleştirilir.  
  
 İlk geçişinde, yalnızca en iyi duruma getirme gerçekleştirilirse, alma zamanı Arama performansını ayarlamak için meta veri yapıları sıralar. Bu adım, genellikle etrafında, kayıtları ileride kullanılmak üzere aracı tarafından korunan belirteçleri geçersiz kılınır yan etkisi olan taşıma sonuçlanır. Meta veri belirteci değişikliklerin kadar çağıran ikinci aşamadan sonra ancak bildirin değil. İkinci geçişinde çeşitli en iyi duruma getirme koyma (erken bağlama) en iyi duruma getirme gibi meta veriler, toplam boyutunu azaltmak için hedeflenen gerçekleştirilir `mdTypeRef` ve `mdMemberRef` belirteçler başvuru sağlayan bir tür veya içinde bildirilen üye olduğunda geçerli meta veri kapsamı. Bu geçişte belirteci eşleme başka bir gidiş gerçekleşir. Bu aşamadan sonra meta veri altyapısı aracılığıyla arayan bildirir, `IMapToken` belirteci değerleri herhangi bir arabirim değişti.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
