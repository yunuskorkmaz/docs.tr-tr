---
description: ': ICorPublishEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c0d50f67bd61eecbade0b226f2f569ac26712faf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721612"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum Arabirimi

, Süreçler ve uygulama etki alanları hakkında bilgi yayımlarken kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorpublishenum-clone-method.md)|Bu nesnenin bir kopyasını oluşturur `ICorPublishEnum` .|  
|[GetCount Yöntemi](icorpublishenum-getcount-method.md)|Numaralandırmadaki öğelerin sayısını alır.|  
|[Reset Yöntemi](icorpublishenum-reset-method.md)|İmlecini numaralandırmanın başlangıcına taşımalıdır.|  
|[Skip Yöntemi](icorpublishenum-skip-method.md)|İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki Numaralandırıcılar öğesinden türetilir `ICorPublishEnum` :  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorpubPublish Ortak Sınıfı](corpubpublish-coclass.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
