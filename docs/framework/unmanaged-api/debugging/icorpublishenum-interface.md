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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993544"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum Arabirimi
Yayımlama işlemleri ve uygulama etki alanları hakkında bilgilerin kullanılan numaralandırıcılar için soyut temel arayüz görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|Bu bir kopyasını oluşturur `ICorPublishEnum` nesne.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|Sabit listede öğe sayısını alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|İmleç numaralandırma başlangıcına taşır.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki numaralandırıcılar türetilmesi `ICorPublishEnum`:  
  
- [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
