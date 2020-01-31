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
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789212"
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
|[ICorPublish Arabirimi](icorpublish-interface.md)|Bu süreçlerdeki süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.|  
|[ICorPublishAppDomain Arabirimi](icorpublishappdomain-interface.md)|, Bir işlemdeki uygulama etki alanı ile ilgili bilgi sağlar.|  
|[ICorPublishAppDomainEnum Arabirimi](icorpublishappdomainenum-interface.md)|Bir işlem içinde mevcut olan bir uygulama etki alanı koleksiyonunu gezme yöntemleri sağlar.|  
|[ICorPublishProcess Arabirimi](icorpublishprocess-interface.md)|Bir bilgisayarda çalışan bir işlemi temsil eder.|  
|[ICorPublishProcessEnum Arabirimi](icorpublishprocessenum-interface.md)|Bir bilgisayarda çalışan işlem koleksiyonunda geçiş yapan yöntemler sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tipik bir yayımlama senaryosu, uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak isteyen bir geliştirici içerir. Barındırma ortamı bir işlem içinde birden fazla uygulama etki alanı çalıştırıyor olabilir. Geliştirici, bilgisayarda çalışan tüm işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yöntem kullanmak ister ve belirli bir işlem seçer. Liste, yönetilen kod çalıştıran işlemlerin içindeki tüm uygulama etki alanlarını içermelidir. Geliştirici daha sonra belirli uygulama etki alanını tanımlayabilir ve bu etki alanına bir hata ayıklayıcı ekleyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
