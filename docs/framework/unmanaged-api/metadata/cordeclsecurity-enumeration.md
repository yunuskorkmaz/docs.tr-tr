---
title: CorDeclSecurity Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046039"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity Numaralandırması
Bildirime dayalı güvenlik kullanarak gerçekleştirilebilir güvenlik eylemleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dclActionMask`|Ayrılmış.|  
|`dclActionNil`|Ayrılmış.|  
|`dclRequest`|Ayrılmış.|  
|`dclDemand`|Çağrı yığınında daha yüksek tüm çağıranlar geçerli bir izin nesnesi tarafından belirtilen izin verilen gereklidir.|  
|`dclAssert`|Çağıranlar yığınında daha yüksek bir kaynağa erişim izni verilmemiş bile, çağırma kodunun geçerli izin nesnesi tarafından tanımlanan kaynağa erişebilir|  
|`dclDeny`|Erişim izni verilmiş olsa bile geçerli bir izin nesnesi tarafından belirtilen kaynak erişim olanağı arayanlar için reddedildi.|  
|`dclPermitOnly`|Yalnızca bu izin nesnesi tarafından belirtilen kaynak kodu diğer kaynaklara erişim izni verilmiş olsa bile erişilebilir.|  
|`dclLinktimeCheck`|Şu anki çağırıcı, belirli bir süre için belirtilen izin verilen gereklidir.|  
|`dclInheritanceCheck`|Başka bir sınıf ya da bir yöntemini geçersiz kılma türetilen sınıfın belirtilen izin verilen gereklidir.|  
|`dclRequestMinimum`|Çağıran kodun çalışması için gereken en düşük izinleri isteyebilir. Bu eylem, yalnızca derlemenin kapsamında kullanılabilir.|  
|`dclRequestOptional`|Çağıran, isteğe bağlı (çalıştırmak için gerekli değildir) için ek izinler isteyebilir. Bu istek özel olarak istenen tüm izinlerin dolaylı olarak reddeder. Bu eylem, yalnızca derlemenin kapsamında kullanılabilir.|  
|`dclRequestRefuse`|Çağıranın isteği yanlış izinleri verilmez. Bu eylem, yalnızca derlemenin kapsamında kullanılabilir.|  
|`dclPrejitGrant`|Ayrılmış.|  
|`dclPrejitDenied`|Ayrılmış.|  
|`dclNonCasDemand`|Ayrılmış.|  
|`dclNonCasLinkDemand`|Şu anki çağırıcı belirtilen izin verilen gereklidir.|  
|`dclNonCasInheritance`|Ayrılmış.|  
|`dclLinkDemandChoice`|Ayrılmış.|  
|`dclInheritanceDemandChoice`|Ayrılmış.|  
|`dclDemandChoice`|Ayrılmış.|  
|`dclMaximumValue`|Ayrılmış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
