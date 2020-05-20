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
ms.openlocfilehash: acbc37d0f49af21c60ff6989932c5d341673512b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421182"
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
