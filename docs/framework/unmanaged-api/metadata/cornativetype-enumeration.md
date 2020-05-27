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
ms.openlocfilehash: dd97c479f12e7bdb015b39a802b398ca2b0bcd3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007643"
---
# <a name="cornativetype-enumeration"></a>CorNativeType Numaralandırması
Yerel yönetilmeyen türleri tanımlayan değerleri içerir.  
  
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
|`NATIVE_TYPE_BOOLEAN`|Bir 4 baytlık Boole değeri, TRUE sıfır değil ve FALSE sıfırdır.|  
|`NATIVE_TYPE_I1`|İşaretli 8 bit tam sayı değeri.|  
|`NATIVE_TYPE_U1`|İşaretsiz 8 bit tamsayı değeri.|  
|`NATIVE_TYPE_I2`|İşaretli 16 bit tamsayı değeri.|  
|`NATIVE_TYPE_U2`|İşaretsiz 16 bit tamsayı değeri.|  
|`NATIVE_TYPE_I4`|İmzalı 32 bitlik bir tamsayı değeri.|  
|`NATIVE_TYPE_U4`|İşaretsiz 32 bitlik bir tamsayı değeri.|  
|`NATIVE_TYPE_I8`|İmzalı 64 bitlik bir tamsayı değeri.|  
|`NATIVE_TYPE_U8`|İşaretsiz 64 bitlik bir tamsayı değeri.|  
|`NATIVE_TYPE_R4`|4 baytlık kayan nokta sayısal değeri.|  
|`NATIVE_TYPE_R8`|8 baytlık kayan nokta sayısal değeri.|  
|`NATIVE_TYPE_SYSCHAR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_VARIANT`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_CURRENCY`|Yönetilen türe karşılık gelen sayısal COM türü <xref:System.Decimal> .|  
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
|`NATIVE_TYPE_STRUCT`|Yerel bir yapı değeri.|  
|`NATIVE_TYPE_INTF`|COM birlikte çalışma.|  
|`NATIVE_TYPE_SAFEARRAY`|COM birlikte çalışma.|  
|`NATIVE_TYPE_FIXEDARRAY`|Sabit uzunluklu bir dizi değeri.|  
|`NATIVE_TYPE_INT`|Yerel bir 16 bit işaretli tamsayı değeri.|  
|`NATIVE_TYPE_UINT`|Yerel bir 16 bit işaretsiz tamsayı değeri.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Kullanımdan kalktı.<br /><br /> NATIVE_TYPE_STRUCT kullanın.|  
|`NATIVE_TYPE_BYVALSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_ANSIBSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_TBSTR`|COM birlikte çalışma.<br /><br /> Platforma bağlı olarak BSTR veya ANSIBSTR seçin.|  
|`NATIVE_TYPE_VARIANTBOOL`|2 baytlık bir Boole değeri; burada TRUE-1 ve FALSE sıfırdır.|  
|`NATIVE_TYPE_FUNC`|Bir işlev işaretçisi.|  
|`NATIVE_TYPE_ASANY`|Herhangi bir yerel türe başvuru.|  
|`NATIVE_TYPE_ARRAY`|Belirtilmemiş bir türün üyeleri olan bir diziye başvuru.|  
|`NATIVE_TYPE_LPSTRUCT`|Bir yapıya 32 bitlik bir tamsayı işaretçisi.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Özel sıralayıcı yerel türü.<br /><br /> Bu, arkasından aşağıdaki biçimdeki bir dize gelmelidir: "Yerel tür adı/0Özel Sıralayıcı türü name/0Optional Cookie/0" veya "{Native Type GUID}/0Özel Sıralayıcı türü ad/0Isteğe bağlı tanımlama bilgisi/0"|  
|`NATIVE_TYPE_ERROR`|COM birlikte çalışma.<br /><br /> ELEMENT_TYPE_I4 bu tür VT_HRESULT eşlenir.|  
|`NATIVE_TYPE_IINSPECTABLE`|Yerel bir `IInspectable` tür.|  
|`NATIVE_TYPE_HSTRING`|Yerel bir `HString` .|  
|`NATIVE_TYPE_MAX`|Geçersiz bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
