---
title: CorTypeAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f71e59eb13321517de61315d3ba06b96c5458f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449279"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr Numaralandırması
Tür meta veri gösteren değerler içeriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`tdVisibilityMask`|Tür görünürlüğü bilgileri kullanılır.|  
|`tdNotPublic`|Tür genel kapsamda değil belirtir.|  
|`tdPublic`|Türünün ortak kapsamında olduğunu belirtir.|  
|`tdNestedPublic`|Ortak bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedPrivate`|Özel bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedFamily`|Türü ile ailesi görünürlük iç içe yerleştirilmiş belirtir.|  
|`tdNestedAssembly`|Derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedFamANDAssem`|Aile ve derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedFamORAssem`|Aile veya derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdLayoutMask`|Türü için Düzen bilgileri alır.|  
|`tdAutoLayout`|Bu tür alanları otomatik olarak düzenlenmiştir belirtir.|  
|`tdSequentialLayout`|Bu tür alanları sırayla düzenlenmiştir belirtir.|  
|`tdExplicitLayout`|Bu alan düzeni açıkça sağlanan belirtir.|  
|`tdClassSemanticsMask`|Türü anlamsal bilgilerini alır.|  
|`tdClass`|Türün bir sınıf olduğunu belirtir.|  
|`tdInterface`|Türün bir arabirim olduğunu belirtir.|  
|`tdAbstract`|Türün Özet olup olmadığını belirtir.|  
|`tdSealed`|Türü genişletilemez belirtir.|  
|`tdSpecialName`|Sınıf adı özel olduğunu belirtir. Adını açıklar nasıl.|  
|`tdImport`|Türü alınır belirtir.|  
|`tdSerializable`|Türü seri hale getirilebilir olduğunu belirtir.|  
|`tdWindowsRuntime`|Bu tür gerektiğini belirten bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türü.|  
|`tdStringFormatMask`|Dizeleri nasıl kodlanmış ve biçimlendirilmiş hakkında bilgi alır.|  
|`tdAnsiClass`|Bu tür bir LPTSTR ANSI olarak yorumlar belirtir.|  
|`tdUnicodeClass`|Bu tür bir LPTSTR Unicode olarak yorumlar belirtir.|  
|`tdAutoClass`|Bu tür bir LPTSTR otomatik olarak yorumlar belirtir.|  
|`tdCustomFormatClass`|Türü bir standart kodlama, olduğunu belirtir belirtildiği gibi `CustomFormatMask`.|  
|`tdCustomFormatMask`|Yerel birlikte çalışabilirliği için standart olmayan kodlama bilgilerini almak için bu maskesi kullanın. Bu iki BITS değerlerin anlamı, belirtilmedi.|  
|`tdBeforeFieldInit`|Türü statik bir alana erişmek için ilk deneme önce başlatılmalıdır belirtir.|  
|`tdForwarder`|Türü dışarı belirtir ve bir tür iletici.|  
|`tdReservedMask`|Bu bayrak ve bayrakları ortak dil çalışma zamanı tarafından dahili olarak kullanılır.|  
|`tdRTSpecialName`|Ortak dil çalışma zamanı adı kodlama denetleyeceğini belirtir.|  
|`tdHasSecurity`|Türü, kendisiyle ilişkilendirilmiş güvenlik olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
