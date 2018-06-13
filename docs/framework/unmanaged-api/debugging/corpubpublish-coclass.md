---
title: CorpubPublish Ortak Sınıfı
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9941a9be7d9f68255636b405db29a623be8d37e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406444"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish Coclass’ı
Uygulama etki alanları ve işlemler hakkında bilgi yayımlamak için arabirimi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Arabirimler  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|[ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Bu işlemleri süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemleri sağlar.|  
|[ICorPublishAppDomain Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Temsil eder ve bir işlemde bir uygulama etki alanı hakkında bilgi sağlar.|  
|[ICorPublishAppDomainEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Şu anda bir işlem içinde mevcut uygulama etki alanları koleksiyonu çapraz yöntemleri sağlar.|  
|[ICorPublishProcess Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Bir bilgisayarda çalışan bir işlemi temsil eder.|  
|[ICorPublishProcessEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Bir bilgisayarda çalışan işlemlerin bir koleksiyon geçiş yöntemleri sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tipik bir yayımlama senaryosu uygulama etki alanı içindeki bir bilgisayarda çalışan yönetilen kodda hata ayıklama isteyen bir geliştirici içerir. Barındırma ortamı birden fazla uygulama etki alanı bir işlem içinde çalışmıyor olabilir. Geliştirici, tüm bilgisayar üzerinde çalışan işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir şekilde kullanmak ve belirli bir işlemin çekme ister misiniz? Listenin tüm yönetilen kod çalışan işlemleri içinde uygulama etki alanları içermelidir. Geliştirici belirli uygulama etki alanını tanımlamak ve bir hata ayıklayıcı bu etki alanına bağlayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorPub.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
