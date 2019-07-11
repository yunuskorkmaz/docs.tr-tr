---
title: CorNativeType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846c754aeb0a710fa70e906e666f694eaa77c576
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781705"
---
# <a name="cornativetype-enumeration"></a>CorNativeType Numaralandırması
Yönetilmeyen yerel türleri açıklayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_VOID`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_BOOLEAN`|TRUE sıfır olmayan ve FALSE olduğu bir 4 baytlık Boole değeri sıfırdır.|  
|`NATIVE_TYPE_I1`|Bir işaretli 8 bit tam sayı değeri.|  
|`NATIVE_TYPE_U1`|İmzalanmamış 8 bit tamsayı değeri.|  
|`NATIVE_TYPE_I2`|Bir 16 bitlik işaretli tamsayı değeri.|  
|`NATIVE_TYPE_U2`|Bir 16 bitlik işaretsiz tamsayı değeri.|  
|`NATIVE_TYPE_I4`|Bir işaretli 32-bit tamsayı değeri.|  
|`NATIVE_TYPE_U4`|Bir işaretsiz 32-bit tamsayı değeri.|  
|`NATIVE_TYPE_I8`|Bir 64-bit işaretli tamsayı değeri.|  
|`NATIVE_TYPE_U8`|İşaretsiz 64-bit tamsayı değeri.|  
|`NATIVE_TYPE_R4`|4-bayt kayan nokta sayısal bir değer.|  
|`NATIVE_TYPE_R8`|Bir 8-bayt kayan nokta sayısal değer.|  
|`NATIVE_TYPE_SYSCHAR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_VARIANT`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_CURRENCY`|Yönetilen karşılık gelen sayısal bir COM tür <xref:System.Decimal> türü.|  
|`NATIVE_TYPE_PTR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_DECIMAL`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_DATE`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_BSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_LPSTR`|LPSTR dize değeri.|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR dize değeri.|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR dize değeri.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Sabit, sistem tarafından tanımlanan bir dize değeri.|  
|`NATIVE_TYPE_OBJECTREF`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_IUNKNOWN`|COM birlikte çalışma.|  
|`NATIVE_TYPE_IDISPATCH`|COM birlikte çalışma.|  
|`NATIVE_TYPE_STRUCT`|Bir yerel yapısı değeri.|  
|`NATIVE_TYPE_INTF`|COM birlikte çalışma.|  
|`NATIVE_TYPE_SAFEARRAY`|COM birlikte çalışma.|  
|`NATIVE_TYPE_FIXEDARRAY`|Bir sabit uzunluklu dizi değeri.|  
|`NATIVE_TYPE_INT`|Bir yerel 16 bitlik işaretli tamsayı değeri.|  
|`NATIVE_TYPE_UINT`|Bir yerel 16 bitlik işaretsiz tamsayı değeri.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Kullanımdan kalktı.<br /><br /> NATIVE_TYPE_STRUCT kullanın.|  
|`NATIVE_TYPE_BYVALSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_ANSIBSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_TBSTR`|COM birlikte çalışma.<br /><br /> BSTR veya ANSIBSTR platforma bağlı olarak seçin.|  
|`NATIVE_TYPE_VARIANTBOOL`|Burada doğru -1 ve sıfırsa yanlış bir 2 baytlık Boole değeri.|  
|`NATIVE_TYPE_FUNC`|Bir işlev işaretçisi.|  
|`NATIVE_TYPE_ASANY`|Herhangi bir yerel tür referansı.|  
|`NATIVE_TYPE_ARRAY`|Belirtilmeyen bir türün üyeleri olan bir dizi bir başvuru.|  
|`NATIVE_TYPE_LPSTRUCT`|Yapı bir 32-bit tamsayı işaretçisi.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Özel bir Sıralayıcı yerel bir tür.<br /><br /> Bu, aşağıdaki biçimde bir dize tarafından izlenen gerekir: "Yerel tür adı/0Custom Sıralayıcı tür adı/0Optional tanımlama bilgisi/0" veya "{yerel türü GUID'i} / 0Custom sıralayıcı türü adı/0Optional tanımlama bilgisi/0"|  
|`NATIVE_TYPE_ERROR`|COM birlikte çalışma.<br /><br /> ELEMENT_TYPE_I4 ile bu tür için VT_HRESULT eşler.|  
|`NATIVE_TYPE_IINSPECTABLE`|Yerel `IInspectable` türü.|  
|`NATIVE_TYPE_HSTRING`|Yerel `HString`.|  
|`NATIVE_TYPE_MAX`|Geçersiz bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
