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
ms.openlocfilehash: 09a351db65c7ed310d3eb68c71a5207ed6040dd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177963"
---
# <a name="cornativetype-enumeration"></a>CorNativeType Numaralandırması
Yerel yönetilmeyen türleri açıklayan değerler içerir.  
  
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
|`NATIVE_TYPE_BOOLEAN`|TRUE'nun sıfır olmadığı ve FALSE'un sıfır olduğu 4 baytBoolean değeri.|  
|`NATIVE_TYPE_I1`|İmzalı 8 bit tamsayı değeri.|  
|`NATIVE_TYPE_U1`|İmzasız 8 bit'lik bir sayı değeri.|  
|`NATIVE_TYPE_I2`|İmzalı 16 bit tamsayı değeri.|  
|`NATIVE_TYPE_U2`|İmzasız 16 bit'lik bir sayı değeri.|  
|`NATIVE_TYPE_I4`|İmzalı 32 bit tamsayı değeri.|  
|`NATIVE_TYPE_U4`|İmzasız 32 bit'lik bir sayı değeri.|  
|`NATIVE_TYPE_I8`|İmzalı 64 bit tamsayı değeri.|  
|`NATIVE_TYPE_U8`|İmzasız 64 bit'lik bir sayı değeri.|  
|`NATIVE_TYPE_R4`|4 bayt kayan nokta sayısal değeri.|  
|`NATIVE_TYPE_R8`|8 bayt kayan nokta sayısal değeri.|  
|`NATIVE_TYPE_SYSCHAR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_VARIANT`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_CURRENCY`|Yönetilen <xref:System.Decimal> türe karşılık gelen sayısal bir COM türü.|  
|`NATIVE_TYPE_PTR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_DECIMAL`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_DATE`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|LPSTR dize değeri.|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR dize değeri.|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR dize değeri.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Sabit, sistem tanımlı dize değeri.|  
|`NATIVE_TYPE_OBJECTREF`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Yerel yapı değeri.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Sabit uzunlukta bir dizi değeri.|  
|`NATIVE_TYPE_INT`|Yerel 16 bit imzalı tamsayı değeri.|  
|`NATIVE_TYPE_UINT`|Yerel 16 bit imzasız tamsayı değeri.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Kullanımdan kalktı.<br /><br /> NATIVE_TYPE_STRUCT kullan.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Platforma bağlı olarak BSTR veya ANSIBSTR'yi seçin.|  
|`NATIVE_TYPE_VARIANTBOOL`|TRUE -1 ve FALSE sıfır olduğu 2 bayt Boolean değeri.|  
|`NATIVE_TYPE_FUNC`|Bir işlev işaretçisi.|  
|`NATIVE_TYPE_ASANY`|Herhangi bir yerli türe bir başvuru.|  
|`NATIVE_TYPE_ARRAY`|Belirtilmemiş bir türün üyeleri olan bir diziye başvuru.|  
|`NATIVE_TYPE_LPSTRUCT`|Bir yapıya 32 bit tamsayı işaretçisi.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Özel bir mareşal yerli tipi.<br /><br /> Bunu aşağıdaki biçimde bir dize izlenmelidir: "Yerel yazı adı/0Özel mareşal türü adı/0İsteğe bağlı çerez/0" veya "{Yerel tür GUID}/0Custom mareşal türü adı/0İsteğe bağlı çerez/0"|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> ELEMENT_TYPE_I4 ile bu tür haritalar VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Yerli `IInspectable` bir tip.|  
|`NATIVE_TYPE_HSTRING`|Bir `HString`yerli.|  
|`NATIVE_TYPE_MAX`|Geçersiz bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorHdr.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
