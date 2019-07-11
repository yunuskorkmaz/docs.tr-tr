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
ms.openlocfilehash: 7d1ca8ea9d00de8a07c67977cf108c50268802e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739359"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish Ortak Sınıfı
Uygulama etki alanları ve işlemler hakkında bilgi yayımlamak için arabirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|[ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Bu işlemde süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.|  
|[ICorPublishAppDomain Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Temsil eder ve bir uygulama etki alanında bir işlem hakkında bilgi sağlar.|  
|[ICorPublishAppDomainEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Şu anda bir işlem içinde varolan bir uygulama etki alanlarının bir koleksiyonu geçirmek için yöntemler sağlar.|  
|[ICorPublishProcess Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Bir bilgisayar üzerinde çalışan bir işlemi temsil eder.|  
|[ICorPublishProcessEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Bir bilgisayarda çalışan işlemler koleksiyonunu geçirmek için yöntemler sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yayımlama için tipik senaryo, bir uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak için isteyen bir geliştirici içerir. Bir işlem içinde birden fazla uygulama etki alanı barındırma ortamı çalışıyor olabilir. Geliştirici, tüm bilgisayarda çalışan işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yolla kullanın ve belirli bir işlem seçin ister misiniz? Listenin tüm yönetilen kod çalışan işlemleri içinde uygulama etki alanları içermelidir. Geliştirici belirli bir uygulama etki alanını tanımlamak ve bir hata ayıklayıcı bu etki alanına ekleyin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
