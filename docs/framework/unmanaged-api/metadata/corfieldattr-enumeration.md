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
ms.openlocfilehash: dea69e18fc517eddddc5b99950a6f3b16ee3e426
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007409"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr Numaralandırması
Bir alanla ilgili meta verileri tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`fdPrivateScope`|Alana başvurulmadığını belirtir.|  
|`fdPrivate`|Alana yalnızca üst öğe türüyle erişilebilir olduğunu belirtir.|  
|`fdFamANDAssem`|Alanı, derlemesinde türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.|  
|`fdAssembly`|Alanı, derlemesindeki tüm türler tarafından erişilebilir olduğunu belirtir.|  
|`fdFamily`|Alanına yalnızca türü ve türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.|  
|`fdFamORAssem`|Alan türetilmiş sınıflar ve kendi derlemesindeki tüm türler tarafından erişilebilir olduğunu belirtir.|  
|`fdPublic`|Alana, bu kapsamın görünürlüğünü içeren tüm türler tarafından erişilebilir olduğunu belirtir.|  
|`fdStatic`|Alanın bir örnek üyesi yerine türünün bir üyesi olduğunu belirtir.|  
|`fdInitOnly`|Alanın başlatıldıktan sonra değiştirilemeyeceğini belirtir.|  
|`fdLiteral`|Alan değerinin bir derleme zamanı sabiti olduğunu belirtir.|  
|`fdNotSerialized`|Türü uzaktan olduğunda alanın serileştirilmemiş olduğunu belirtir.|  
|`fdSpecialName`|Alanın özel olduğunu ve adının nasıl kullanıldığını belirtir.|  
|`fdPinvokeImpl`|Alan uygulamasının PInvoke aracılığıyla iletildiğini belirtir.|  
|`fdReservedMask`|Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.|  
|`fdRTSpecialName`|Ortak dil çalışma zamanı meta veri iç API 'Lerinin ad kodlamasını denetlemesi gerektiğini belirtir.|  
|`fdHasFieldMarshal`|Alanın sıralama bilgilerini içerdiğini belirtir.|  
|`fdHasDefault`|Alanın varsayılan bir değere sahip olduğunu belirtir.|  
|`fdHasFieldRVA`|Alanın göreli bir sanal adresi olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
