---
title: ICorPublishEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: f54bb99df60d7b3fb7bb98de75fbae210597e45c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790621"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum Arabirimi
, Süreçler ve uygulama etki alanları hakkında bilgi yayımlarken kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorpublishenum-clone-method.md)|Bu `ICorPublishEnum` nesnesinin bir kopyasını oluşturur.|  
|[GetCount Yöntemi](icorpublishenum-getcount-method.md)|Numaralandırmadaki öğelerin sayısını alır.|  
|[Reset Yöntemi](icorpublishenum-reset-method.md)|İmlecini numaralandırmanın başlangıcına taşımalıdır.|  
|[Skip Yöntemi](icorpublishenum-skip-method.md)|İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki Numaralandırıcılar `ICorPublishEnum`türetilir:  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorpubPublish Coclass](corpubpublish-coclass.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
