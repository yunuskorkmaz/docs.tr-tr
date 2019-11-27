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
ms.openlocfilehash: b1586184c91619994ba0dfc9d5dcc277c10f99cf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436450"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr Numaralandırması
Tür meta verilerini gösteren değerleri içerir.  
  
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`tdVisibilityMask`|Tür görünürlük bilgileri için kullanılır.|  
|`tdNotPublic`|Türün ortak kapsamda değil olduğunu belirtir.|  
|`tdPublic`|Türün ortak kapsamda olduğunu belirtir.|  
|`tdNestedPublic`|Türün genel görünürlük ile iç içe olduğunu belirtir.|  
|`tdNestedPrivate`|Türün özel görünürlük ile iç içe olduğunu belirtir.|  
|`tdNestedFamily`|Türün aile görünürlüğü ile iç içe olduğunu belirtir.|  
|`tdNestedAssembly`|Türün derleme görünürlüğünde iç içe olduğunu belirtir.|  
|`tdNestedFamANDAssem`|Türün aile ve derleme görünürlüğünde iç içe olduğunu belirtir.|  
|`tdNestedFamORAssem`|Türün aile veya derleme görünürlüğünde iç içe olduğunu belirtir.|  
|`tdLayoutMask`|Türün düzen bilgisini alır.|  
|`tdAutoLayout`|Bu tür alanların otomatik olarak düzenlendiğini belirtir.|  
|`tdSequentialLayout`|Bu türdeki alanların sırayla düzenlendiğini belirtir.|  
|`tdExplicitLayout`|Alan düzeninin açık olarak sağlanmış olduğunu belirtir.|  
|`tdClassSemanticsMask`|Tür hakkında anlam bilgileri alır.|  
|`tdClass`|Türün bir sınıf olduğunu belirtir.|  
|`tdInterface`|Türün bir arabirim olduğunu belirtir.|  
|`tdAbstract`|Türün soyut olduğunu belirtir.|  
|`tdSealed`|Türün uzatılamaz olduğunu belirtir.|  
|`tdSpecialName`|Sınıf adının özel olduğunu belirtir. Adının nasıl yapılacağı açıklanmaktadır.|  
|`tdImport`|Türün içeri aktarılacağını belirtir.|  
|`tdSerializable`|Türün seri hale getirilebilir olduğunu belirtir.|  
|`tdWindowsRuntime`|Bu türün bir Windows Çalışma Zamanı türü olduğunu belirtir.|  
|`tdStringFormatMask`|Dizelerin nasıl kodlandığını ve biçimlendirildiğini hakkında bilgi alır.|  
|`tdAnsiClass`|Bu türün bir LPTSTR öğesini ANSI olarak yorumlaması gerektiğini belirtir.|  
|`tdUnicodeClass`|Bu türün bir LPTSTR öğesini Unicode olarak yorumlayacağını belirtir.|  
|`tdAutoClass`|Bu türün bir LPTSTR öğesini otomatik olarak yorumlayacağını belirtir.|  
|`tdCustomFormatClass`|Türün, `CustomFormatMask`tarafından belirtilen standart olmayan bir kodlamaya sahip olduğunu belirtir.|  
|`tdCustomFormatMask`|Yerel birlikte çalışma için standart olmayan kodlama bilgilerini almak için bu maskeyi kullanın. Bu iki bitin değerlerinin anlamı belirtilmemiş.|  
|`tdBeforeFieldInit`|Statik alana ilk erişim denemesinden önce türün başlatılması gerektiğini belirtir.|  
|`tdForwarder`|Türün verildiğini ve bir tür ileticisi olduğunu belirtir.|  
|`tdReservedMask`|Bu bayrak ve aşağıdaki bayraklar ortak dil çalışma zamanı tarafından dahili olarak kullanılır.|  
|`tdRTSpecialName`|Ortak dil çalışma zamanının ad kodlamasını denetlemesi gerektiğini belirtir.|  
|`tdHasSecurity`|Türün onunla ilişkili güvenlik olduğunu belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
