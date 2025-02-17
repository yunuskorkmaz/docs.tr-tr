---
description: 'Daha fazla bilgi edinin: Cormethodadttr numaralandırması'
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
ms.openlocfilehash: 4050235675f4b237b184d31378a614a0613ab3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784385"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr Numaralandırması

Bir yöntemin özelliklerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
|Üye|Description|  
|------------|-----------------|  
|`mdMemberAccessMask`|Üye erişimini belirtir.|  
|`mdPrivateScope`|Üyenin başvurumadığını belirtir.|  
|`mdPrivate`|Üyenin yalnızca üst tür tarafından erişilebilir olduğunu belirtir.|  
|`mdFamANDAssem`|Üyenin yalnızca bu derlemede alt türler tarafından erişilebilir olduğunu belirtir.|  
|`mdAssem`|Üyenin derlemedeki herkes tarafından erişilebilir olduğunu belirtir.|  
|`mdFamily`|Üyenin yalnızca Type ve alt türleri tarafından erişilebilir olduğunu belirtir.|  
|`mdFamORAssem`|Üyenin türetilmiş sınıflar ve kendi derlemesindeki diğer türler tarafından erişilebilir olduğunu belirtir.|  
|`mdPublic`|Üyenin kapsama erişimi olan tüm türler tarafından erişilebilir olduğunu belirtir.|  
|`mdStatic`|Üyenin, bir örneğin üyesi olarak değil türün bir parçası olarak tanımlandığını belirtir.|  
|`mdFinal`|Yöntemin geçersiz kılınamayacağını belirtir.|  
|`mdVirtual`|Yöntemin geçersiz kılınabileceğini belirtir.|  
|`mdHideBySig`|Yöntemin yalnızca ada göre değil, ad ve imzaya göre gizlediğini belirtir.|  
|`mdVtableLayoutMask`|Sanal tablo yerleşimini belirtir.|  
|`mdReuseSlot`|Sanal tabloda bu yöntem için kullanılan yuvanın yeniden kullanıldığını belirtir. Bu varsayılan seçenektir.|  
|`mdNewSlot`|Yöntemin sanal tabloda her zaman yeni bir yuva aldığından emin olur.|  
|`mdCheckAccessOnOverride`|Yöntemin görünür olduğu aynı türler tarafından geçersiz kılınabileceğini belirtir.|  
|`mdAbstract`|Yöntemin uygulandığını belirtir.|  
|`mdSpecialName`|Yöntemin özel olduğunu ve adının nasıl kullanıldığını belirtir.|  
|`mdPinvokeImpl`|Yöntem uygulamasının PInvoke kullanılarak iletildiğini belirtir.|  
|`mdUnmanagedExport`|Yöntemin yönetilmeyen koda aktarılmış yönetilen bir yöntem olduğunu belirtir.|  
|`mdReservedMask`|Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.|  
|`mdRTSpecialName`|Ortak dil çalışma zamanının Yöntem adının kodlamasını denetlemesi gerektiğini belirtir.|  
|`mdHasSecurity`|Metodun onunla ilişkili güvenlik olduğunu belirtir.|  
|`mdRequireSecObject`|Metodun güvenlik kodu içeren başka bir yöntemi çağırıyorsa belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
