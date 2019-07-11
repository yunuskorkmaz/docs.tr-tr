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
ms.openlocfilehash: 5786f24f6543d4d262dd8a6389132aba02f9aacc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779204"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr Numaralandırması
Türü meta verileri gösteren değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`tdVisibilityMask`|Tür görünürlük bilgileri kullanılır.|  
|`tdNotPublic`|Türün genel kapsam içinde değil belirtir.|  
|`tdPublic`|Tür genel kapsamda olduğunu belirtir.|  
|`tdNestedPublic`|Türü genel görünürlük ile iç içe belirtir.|  
|`tdNestedPrivate`|Özel bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedFamily`|Tür ailesi görünürlük ile iç içe belirtir.|  
|`tdNestedAssembly`|Derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedFamANDAssem`|Aile ve derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdNestedFamORAssem`|Aile veya derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.|  
|`tdLayoutMask`|Düzen türü bilgilerini alır.|  
|`tdAutoLayout`|Bu tür alanlar otomatik olarak düzenlenmiştir belirtir.|  
|`tdSequentialLayout`|Bu tür alanlar sıralı olarak düzenlenmiştir belirtir.|  
|`tdExplicitLayout`|Bu alanı düzeni açıkça sağlanan belirtir.|  
|`tdClassSemanticsMask`|Anlam türü bilgilerini alır.|  
|`tdClass`|Türün bir sınıf olduğunu belirtir.|  
|`tdInterface`|Türün bir arabirim olup olmadığını belirtir.|  
|`tdAbstract`|Türün Özet olup olmadığını belirtir.|  
|`tdSealed`|Tür genişletilemez belirtir.|  
|`tdSpecialName`|Sınıf adı özel olduğunu belirtir. Adını açıklar nasıl.|  
|`tdImport`|Tür içe aktarılan belirtir.|  
|`tdSerializable`|Türü seri hale getirilebilir olduğunu belirtir.|  
|`tdWindowsRuntime`|Bu tür bir Windows çalışma zamanı türü olduğunu belirtir.|  
|`tdStringFormatMask`|Dizeleri nasıl kodlanmış ve biçimlendirilmiş hakkında bilgi alır.|  
|`tdAnsiClass`|Bu tür bir LPTSTR ANSI olarak yorumlar belirtir.|  
|`tdUnicodeClass`|Bu tür bir LPTSTR Unicode olarak yorumlar belirtir.|  
|`tdAutoClass`|Bu tür bir LPTSTR otomatik olarak yorumlar belirtir.|  
|`tdCustomFormatClass`|Türü bir standart kodlama, sahip olduğunu belirtir belirtildiği gibi `CustomFormatMask`.|  
|`tdCustomFormatMask`|Yerel birlikte çalışabilirliği için standart kodlama bilgi almak için bu maskesi kullanın. Bu iki bit değerlerin anlamı, belirtilmemiş.|  
|`tdBeforeFieldInit`|Türü statik bir alana erişmek için yapılan ilk girişim önce başlatılmalıdır belirtir.|  
|`tdForwarder`|Türü dışarı belirtir ve bir tür ileticisi.|  
|`tdReservedMask`|Bu bayrak ve aşağıdaki bayrakları, ortak dil çalışma zamanı tarafından dahili olarak kullanılır.|  
|`tdRTSpecialName`|Ortak dil çalışma zamanı adı kodlama denetleyeceğini belirtir.|  
|`tdHasSecurity`|Türü güvenlik ilişkili olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
