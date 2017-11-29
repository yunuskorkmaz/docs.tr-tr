---
title: "CorMethodAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodAttr
helpviewer_keywords: CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91afbc9894826b1f44d84f23b550a81d610e3de9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr Numaralandırması
Bir yöntem özelliklerini açıklayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`mdMemberAccessMask`|Üye erişimi belirtir.|  
|`mdPrivateScope`|Üye başvurulamaz belirtir.|  
|`mdPrivate`|Üye yalnızca üst türü tarafından erişilebilir olduğunu belirtir.|  
|`mdFamANDAssem`|Üye bu derlemedeki yalnızca alt türler tarafından erişilebilir olduğunu belirtir.|  
|`mdAssem`|Üye accessibly derlemesindeki herkes tarafından olduğunu belirtir.|  
|`mdFamily`|Üye yalnızca türü ve alt türler tarafından erişilebilir olduğunu belirtir.|  
|`mdFamORAssem`|Üye türetilen sınıflar ve diğer türleri kendi derlemesi tarafından erişilebilir olduğunu belirtir.|  
|`mdPublic`|Üye erişimi olan tüm türleri tarafından kapsama erişilebilir olduğunu belirtir.|  
|`mdStatic`|Üye türü bir parçası olarak yerine bir örneği bir üyesi olarak tanımlandı belirtir.|  
|`mdFinal`|Yöntemi geçersiz kılınamaz belirtir.|  
|`mdVirtual`|Yöntem geçersiz kılınabilir belirtir.|  
|`mdHideBySig`|Yöntem adı ve imza yerine yalnızca ada göre gizler belirtir.|  
|`mdVtableLayoutMask`|Sanal Tablo düzeni belirtir.|  
|`mdReuseSlot`|Bu yöntemde sanal tablo için kullanılan yuvası yeniden kullanılabilir belirtir. Bu varsayılandır.|  
|`mdNewSlot`|Yöntem her zaman sanal tablosunda yeni bir yuva alır belirtir.|  
|`mdCheckAccessOnOverride`|Yöntem için görülebilir aynı türlerine göre geçersiz kılınabilir belirtir.|  
|`mdAbstract`|Yöntem uygulanmadı belirtir.|  
|`mdSpecialName`|Yöntemi özeldir ve adını açıklayan belirtir nasıl.|  
|`mdPinvokeImpl`|Yöntem uygulaması PInvoke kullanarak iletilir belirtir.|  
|`mdUnmanagedExport`|Yöntem yönetilmeyen koda dışarı yönetilen bir yöntem olduğunu belirtir.|  
|`mdReservedMask`|İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.|  
|`mdRTSpecialName`|Ortak dil çalışma zamanı yöntemi adı kodlama denetleyeceğini belirtir.|  
|`mdHasSecurity`|Yöntemi, kendisiyle ilişkilendirilmiş güvenlik olduğunu belirtir.|  
|`mdRequireSecObject`|Yöntemi güvenlik kodunu içeren başka bir yöntem çağırır belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
