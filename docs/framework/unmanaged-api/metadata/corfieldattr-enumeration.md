---
title: CorFieldAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 432e202eb8db105e8d56d3d36cdc8001bac5320c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182383"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr Numaralandırması
Bir alan hakkında açıklayan meta verileri değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`fdFieldAccessMask`|Erişilebilirlik bilgileri belirtir.|  
|`fdPrivateScope`|Alan başvurulamaz belirtir.|  
|`fdPrivate`|Alan yalnızca kendi üst türü tarafından erişilebilir olduğunu belirtir.|  
|`fdFamANDAssem`|Alanın kendi derlemedeki türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.|  
|`fdAssembly`|Alanın kendi derlemedeki tüm tür tarafından erişilebilir olduğunu belirtir.|  
|`fdFamily`|Alan yalnızca türü tarafından erişilebilir olduğundan ve türetilmiş sınıfları belirtir.|  
|`fdFamORAssem`|Alanın kendi derlemesi içindeki tüm türleri ve türetilen sınıflar tarafından erişilebilir olduğunu belirtir.|  
|`fdPublic`|Alanın tüm türleri bu kapsamı tarafından görünürlük ile erişilebilir olduğunu belirtir.|  
|`fdStatic`|Alan türünü üyesi yerine bir örnek üyesi olduğunu belirtir.|  
|`fdInitOnly`|Alan başlatıldıktan sonra değiştirilemeyeceğini belirtir.|  
|`fdLiteral`|Alan değeri bir derleme zamanı sabiti olduğunu belirtir.|  
|`fdNotSerialized`|Alan türünü düğümlerde olduğunda serileştirildiği değil belirtir.|  
|`fdSpecialName`|Alan özel olduğundan ve adının açıklayan belirtir nasıl.|  
|`fdPinvokeImpl`|Alan uygulamasında PInvoke aracılığıyla iletilir belirtir.|  
|`fdReservedMask`|İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.|  
|`fdRTSpecialName`|Ortak dil çalışma zamanı meta veri adı kodlama dahili API'lerde denetleyeceğini belirtir.|  
|`fdHasFieldMarshal`|Alan sıralama bilgilerini içerdiğini belirtir.|  
|`fdHasDefault`|Alanın bir varsayılan değer olduğunu belirtir.|  
|`fdHasFieldRVA`|Bir göreli sanal adres alanına sahip olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
