---
title: CorMethodAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177001"
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
|`mdFamANDAssem`|Üyenin alt yalnızca bu derlemedeki türleri tarafından erişilebilir olduğunu belirtir.|  
|`mdAssem`|Üye accessibly derlemedeki hiç kimse tarafından olduğunu belirtir.|  
|`mdFamily`|Üye yalnızca türü ve alt türleri tarafından erişilebilir olduğunu belirtir.|  
|`mdFamORAssem`|Üye, diğer türleri ve türetilen sınıflar tarafından erişilebilir olduğunu belirtir.|  
|`mdPublic`|Üye kapsamına erişimi olan tüm türleri tarafından erişilebilir olduğunu belirtir.|  
|`mdStatic`|Üye türü bir parçası olarak yerine bir örnek üyesi olarak tanımlandı belirtir.|  
|`mdFinal`|Yöntem kılınamayacağını belirtir.|  
|`mdVirtual`|Yöntem geçersiz kılınabilir belirtir.|  
|`mdHideBySig`|Yöntemi yalnızca ada göre değil, ada ve imzaya göre gizlediğini belirtir.|  
|`mdVtableLayoutMask`|Sanal Tablo düzeni belirtir.|  
|`mdReuseSlot`|Bu yöntem sanal tabloda kullanılan yuva yeniden kullanılabilir belirtir. Bu varsayılandır.|  
|`mdNewSlot`|Yöntem her zaman sanal tablosunda yeni bir yuva alır belirtir.|  
|`mdCheckAccessOnOverride`|Yöntemi aynı türleri için görülebilir tarafından geçersiz kılınabilir belirtir.|  
|`mdAbstract`|Yöntem uygulanmadı belirtir.|  
|`mdSpecialName`|Yöntem özeldir ve adını açıklayan belirtir nasıl.|  
|`mdPinvokeImpl`|Yöntem uygulaması PInvoke kullanarak iletilir belirtir.|  
|`mdUnmanagedExport`|Yöntemi yönetilmeyen koda verilen yönetilen bir yöntem olduğunu belirtir.|  
|`mdReservedMask`|İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.|  
|`mdRTSpecialName`|Ortak dil çalışma zamanı yöntemi adı kodlama denetleyeceğini belirtir.|  
|`mdHasSecurity`|Yöntemi, kendisiyle ilişkilendirilmiş güvenlik sahip olduğunu belirtir.|  
|`mdRequireSecObject`|Yöntemi güvenlik kodu içeren başka bir yöntemi çağıran belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
