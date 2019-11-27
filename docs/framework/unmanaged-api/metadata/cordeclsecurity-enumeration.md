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
ms.openlocfilehash: 98183ed02f8821b7c40852de2d040775d30f2518
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443747"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity Numaralandırması
Bildirime dayalı güvenlik kullanılarak gerçekleştirilebilecek güvenlik eylemlerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`dclActionMask`|Ayrılamadı.|  
|`dclActionNil`|Ayrılamadı.|  
|`dclRequest`|Ayrılamadı.|  
|`dclDemand`|Çağrı yığınında daha yüksek olan tüm arayanlara geçerli izin nesnesi tarafından belirtilen izin verilmesi gerekir.|  
|`dclAssert`|Çağıran kod, yığında daha yüksek arayanlara kaynağa erişim izni verilmese bile, geçerli izin nesnesi tarafından tanımlanan kaynağa erişebilir|  
|`dclDeny`|Geçerli izin nesnesi tarafından belirtilen kaynağa erişme özelliği, bunlara erişim izni verilmiş olsa bile çağıranlara reddedilir.|  
|`dclPermitOnly`|Koda diğer kaynaklara erişim izni verilse bile, yalnızca bu izin nesnesi tarafından belirtilen kaynaklara erişilebilir.|  
|`dclLinktimeCheck`|Hemen çağıranın belirli bir süre için belirtilen izin verilmesi gerekir.|  
|`dclInheritanceCheck`|Başka bir sınıfı devralan veya bir yöntemi geçersiz kılan türetilmiş sınıfın belirtilen izin verilmesi gerekir.|  
|`dclRequestMinimum`|Çağıran, kodun çalışması için gereken en düşük izinleri isteyebilir. Bu eylem yalnızca derlemenin kapsamı içinde kullanılabilir.|  
|`dclRequestOptional`|Çağıran, isteğe bağlı (çalışması için gerekli değildir) ek izinler talep edebilir. Bu istek özellikle istenen tüm diğer izinleri örtülü olarak reddeder. Bu eylem yalnızca derlemenin kapsamı içinde kullanılabilir.|  
|`dclRequestRefuse`|Çağıranın, yanlış bir şekilde kötüye olabilecek izin isteği verilmeyecektir. Bu eylem yalnızca derlemenin kapsamı içinde kullanılabilir.|  
|`dclPrejitGrant`|Ayrılamadı.|  
|`dclPrejitDenied`|Ayrılamadı.|  
|`dclNonCasDemand`|Ayrılamadı.|  
|`dclNonCasLinkDemand`|Hemen çağıranın belirtilen izin verilmesi gerekir.|  
|`dclNonCasInheritance`|Ayrılamadı.|  
|`dclLinkDemandChoice`|Ayrılamadı.|  
|`dclInheritanceDemandChoice`|Ayrılamadı.|  
|`dclDemandChoice`|Ayrılamadı.|  
|`dclMaximumValue`|Ayrılamadı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
