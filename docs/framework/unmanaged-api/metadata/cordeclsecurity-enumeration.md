---
title: "CorDeclSecurity Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30fd7ca2cf7962c6cadb43d4d8e3031b59292463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity Numaralandırması
Bildirim temelli güvenlik kullanılarak gerçekleştirilebilir güvenlik eylemleri belirtir.  
  
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
|`dclDemand`|Geçerli izin nesnesi tarafından belirtilen izni verilmiş tüm arayanlar çağrı yığınında yüksek gereklidir.|  
|`dclAssert`|Arayanlar yığında yüksek kaynağa erişim izni verilmemiş bile çağıran kodu geçerli izin nesnesi tarafından tanımlanan kaynağa erişebilir|  
|`dclDeny`|Erişim izni verilmiş olsa bile geçerli izni nesnesi tarafından belirlenen kaynak erişim olanağı çağıranlar için reddedildi.|  
|`dclPermitOnly`|Kod diğer kaynaklara erişim izni verilmiş olsa bile, yalnızca bu izni nesnesi tarafından belirlenen kaynakları erişilebilir.|  
|`dclLinktimeCheck`|Anında arayanlar belirli bir süre için belirtilmiş izni verilmiş olması gereklidir.|  
|`dclInheritanceCheck`|Başka bir sınıf ya da bir yöntemini geçersiz kılma türetilmiş sınıf belirtilen izin verilmiş olması gereklidir.|  
|`dclRequestMinimum`|Çağıran, kodun çalışması için gerekli minimum izinleri isteyebilir. Bu eylem yalnızca derleme kapsamında kullanılabilir.|  
|`dclRequestOptional`|Çağıran, isteğe bağlı (çalıştırmak için gerekli değildir) için ek izinler isteyebilir. Bu istek, özellikle istenen tüm izinleri örtük olarak reddediyor. Bu eylem yalnızca derleme kapsamında kullanılabilir.|  
|`dclRequestRefuse`|Arayanın istek kötüye kullanımını izinler için izni yok. Bu eylem yalnızca derleme kapsamında kullanılabilir.|  
|`dclPrejitGrant`|Ayrılmış.|  
|`dclPrejitDenied`|Ayrılmış.|  
|`dclNonCasDemand`|Ayrılmış.|  
|`dclNonCasLinkDemand`|Anında arayanlar belirtilmiş izni verilmiş olması gereklidir.|  
|`dclNonCasInheritance`|Ayrılmış.|  
|`dclLinkDemandChoice`|Ayrılmış.|  
|`dclInheritanceDemandChoice`|Ayrılmış.|  
|`dclDemandChoice`|Ayrılmış.|  
|`dclMaximumValue`|Ayrılmış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
