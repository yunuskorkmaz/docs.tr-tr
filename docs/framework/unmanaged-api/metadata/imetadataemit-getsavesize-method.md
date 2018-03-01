---
title: IMetaDataEmit::GetSaveSize Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7585f6adbca97b252fdad90276b0cd422d32c04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize Metodu
Derleme ve meta verilerini tahmini ikili boyutunu geçerli kapsamda alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fSave`  
 [in] Değerini [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) doğru veya yaklaşık boyutu almak belirtir numaralandırması. Yalnızca üç değerler geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:  
  
-   cssAccurate tam boyutu kaydetme verir ancak hesaplamak için daha uzun sürer.  
  
-   cssQuick güvenliğiniz için doldurulan bir boyutu döndüren ancak hesaplamak için daha az zaman alır.  
  
-   cssDiscardTransientCAs söyler `GetSaveSize` discardable özel öznitelikler hemen atabilirsiniz.  
  
 `pdwSaveSize`  
 [out] Dosyayı kaydetmek için gereken boyutu için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetSaveSize`, derleme ve tüm meta veriler geçerli kapsamda kaydetmek için bayt cinsinden gerekli alanı hesaplar. (Çağrı [Imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) yöntemi bu bayt sayısını yayması.)  
  
 Arayan uyguluyorsa [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimi (aracılığıyla [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) veya [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` iki geçişleri gerçekleştirecek en iyi duruma getirme ve onu sıkıştırmak için meta veriler üzerinde. Aksi takdirde, herhangi bir iyileştirme gerçekleştirilir.  
  
 En iyi duruma getirme gerçekleştirilirse, ilk geçişi yalnızca alma zamanı aramaları performansı ayarlamak için meta veri yapılarını sıralar. Bu adım genellikle ileride kullanılmak üzere aracı tarafından korunduğunu belirteçleri geçersiz kılınır yan etkisi, geçici kayıtlarıyla taşıma sonuçlanır. Meta veriler bu belirteci değişinceye kadar arayan ikinci geçişinden sonra ancak bildirin değil. İkinci geçişinde koyma (erken bağlama) en iyi duruma getirme gibi meta veriler, toplam boyutunu azaltmak için yönelik çeşitli iyileştirmeler gerçekleştirilen `mdTypeRef` ve `mdMemberRef` belirteçler: başvuru türü veya içinde bildirilen üyesi olduğunda geçerli meta veri kapsamı. Bu geçişte belirteci eşleme başka bir gidiş oluşur. Bu aşamadan sonra meta veri altyapısı aracılığıyla arayan bildirir, `IMapToken` herhangi arabirimi simge değerlerini değiştirildi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
