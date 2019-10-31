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
ms.openlocfilehash: 89af99fab1f1265701e0dbfe74a46000cb3bfaa6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132145"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish Ortak Sınıfı
Uygulama etki alanları ve işlemleriyle ilgili bilgileri yayımlamak için arabirimler sağlar.  
  
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
|[ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Bu süreçlerdeki süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.|  
|[ICorPublishAppDomain Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|, Bir işlemdeki uygulama etki alanı ile ilgili bilgi sağlar.|  
|[ICorPublishAppDomainEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Bir işlem içinde mevcut olan bir uygulama etki alanı koleksiyonunu gezme yöntemleri sağlar.|  
|[ICorPublishProcess Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Bir bilgisayarda çalışan bir işlemi temsil eder.|  
|[ICorPublishProcessEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Bir bilgisayarda çalışan işlem koleksiyonunda geçiş yapan yöntemler sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tipik bir yayımlama senaryosu, uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak isteyen bir geliştirici içerir. Barındırma ortamı bir işlem içinde birden fazla uygulama etki alanı çalıştırıyor olabilir. Geliştirici, bilgisayarda çalışan tüm işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yöntem kullanmak ister ve belirli bir işlem seçer. Liste, yönetilen kod çalıştıran işlemlerin içindeki tüm uygulama etki alanlarını içermelidir. Geliştirici daha sonra belirli uygulama etki alanını tanımlayabilir ve bu etki alanına bir hata ayıklayıcı ekleyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
