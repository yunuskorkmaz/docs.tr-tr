---
title: "CorFieldAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b199764ea0fb2d02b01d7cf04d1fa8fad743109f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr Numaralandırması
Meta veriler hakkında bir alan açıklamak değerlerini içerir.  
  
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
|`fdFieldAccessMask`|Erişilebilirlik bilgilerini belirtir.|  
|`fdPrivateScope`|Alan başvurulamaz belirtir.|  
|`fdPrivate`|Alan yalnızca kendi üst türü tarafından erişilebilir olduğunu belirtir.|  
|`fdFamANDAssem`|Alan, derleme türetilmiş sınıflarda tarafından erişilebilir olduğunu belirtir.|  
|`fdAssembly`|Alan, derleme içindeki tüm türler tarafından erişilebilir olduğunu belirtir.|  
|`fdFamily`|Alan yalnızca kendi türü tarafından erişilebilir olduğunu ve türetilmiş sınıfları belirtir.|  
|`fdFamORAssem`|Alan, derleme içindeki tüm türler ve türetilen sınıflar tarafından erişilebilir olduğunu belirtir.|  
|`fdPublic`|Alan tüm türleri bu kapsamı tarafından görünürlük ile erişilebilir olduğunu belirtir.|  
|`fdStatic`|Alanın türü üyesi yerine örnek üyesine olduğunu belirtir.|  
|`fdInitOnly`|Alan başlatıldıktan sonra değiştirilemez belirtir.|  
|`fdLiteral`|Alan değeri bir derleme zamanı sabiti olduğunu belirtir.|  
|`fdNotSerialized`|Türünü uzakta olduğunda alan seri değil belirtir.|  
|`fdSpecialName`|Alan özel ve adını açıklayan belirtir nasıl.|  
|`fdPinvokeImpl`|Alan uygulama PInvoke aracılığıyla iletilir belirtir.|  
|`fdReservedMask`|İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.|  
|`fdRTSpecialName`|Ortak dil çalışma zamanı meta verileri iç API adı kodlama denetleyeceğini belirtir.|  
|`fdHasFieldMarshal`|Alan sıralama bilgilerini içerdiğini belirtir.|  
|`fdHasDefault`|Alan varsayılan bir değer olduğunu belirtir.|  
|`fdHasFieldRVA`|Göreli sanal adres alanı olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
