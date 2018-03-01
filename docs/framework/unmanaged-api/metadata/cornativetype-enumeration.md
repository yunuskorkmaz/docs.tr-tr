---
title: "CorNativeType Numaralandırması"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6be442dd74f6a71494e140b76357be1bc9e1b747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativetype-enumeration"></a>CorNativeType Numaralandırması
Yerel yönetilmeyen türlerini tanımlamak değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`NATIVE_TYPE_BOOLEAN`|TRUE sıfır olmayan ve yanlış olduğu bir 4-bayt Boole değeri sıfırdır.|  
|`NATIVE_TYPE_I1`|İşaretli 8 bit tam sayı değeri.|  
|`NATIVE_TYPE_U1`|Bir imzasız 8 bit tamsayı değeri.|  
|`NATIVE_TYPE_I2`|İşaretli 16 bit tamsayı değeri.|  
|`NATIVE_TYPE_U2`|Bir imzasız 16 bit tamsayı değeri.|  
|`NATIVE_TYPE_I4`|İşaretli 32 bit tamsayı değeri.|  
|`NATIVE_TYPE_U4`|Bir imzasız 32 bit tamsayı değeri.|  
|`NATIVE_TYPE_I8`|İşaretli 64-bit tamsayı değeri.|  
|`NATIVE_TYPE_U8`|Bir İmzasız 64-bit tamsayı değeri.|  
|`NATIVE_TYPE_R4`|4-bayt kayan nokta sayısal bir değer.|  
|`NATIVE_TYPE_R8`|Bir 8-bayt kayan nokta sayısal değer.|  
|`NATIVE_TYPE_SYSCHAR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_VARIANT`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_CURRENCY`|Yönetilen karşılık gelen sayısal bir COM türü <xref:System.Decimal> türü.|  
|`NATIVE_TYPE_PTR`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_DECIMAL`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_DATE`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_BSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_LPSTR`|LPSTR dize değeri.|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR dize değeri.|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR dize değeri.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Bir sabit, sistem tarafından tanımlanan dize değeri.|  
|`NATIVE_TYPE_OBJECTREF`|Kullanımdan kalktı.|  
|`NATIVE_TYPE_IUNKNOWN`|COM birlikte çalışma.|  
|`NATIVE_TYPE_IDISPATCH`|COM birlikte çalışma.|  
|`NATIVE_TYPE_STRUCT`|Bir yerel yapısı değer.|  
|`NATIVE_TYPE_INTF`|COM birlikte çalışma.|  
|`NATIVE_TYPE_SAFEARRAY`|COM birlikte çalışma.|  
|`NATIVE_TYPE_FIXEDARRAY`|Bir sabit uzunluk dizisi değer.|  
|`NATIVE_TYPE_INT`|Bir yerel 16 bit işaretli tamsayıyı değer.|  
|`NATIVE_TYPE_UINT`|Bir yerel 16 bit işaretsiz tamsayı değeri.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Kullanımdan kalktı.<br /><br /> NATIVE_TYPE_STRUCT kullanın.|  
|`NATIVE_TYPE_BYVALSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_ANSIBSTR`|COM birlikte çalışma.|  
|`NATIVE_TYPE_TBSTR`|COM birlikte çalışma.<br /><br /> BSTR veya ANSIBSTR platformuna bağlı olarak seçin.|  
|`NATIVE_TYPE_VARIANTBOOL`|Burada TRUE -1 ve sıfırsa yanlış bir 2-bayt Boole değeri.|  
|`NATIVE_TYPE_FUNC`|Bir işlev işaretçisi.|  
|`NATIVE_TYPE_ASANY`|Tüm yerel tür referansı.|  
|`NATIVE_TYPE_ARRAY`|Belirtilmeyen bir türün üyeleri olan bir dizi referansı.|  
|`NATIVE_TYPE_LPSTRUCT`|Bir yapı için bir 32 bit tamsayı işaretçi.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Özel sıralayıcı yerel tür.<br /><br /> Bu şekilde, aşağıdaki biçimde bir dizeyle izlemelidir: "yerel tür adı/0Custom sıralayıcı türü adı/0Optional tanımlama bilgisi/0" veya "{yerel türü GUID'i} / 0Custom sıralayıcı türü adı/0Optional tanımlama bilgisi/0"|  
|`NATIVE_TYPE_ERROR`|COM birlikte çalışma.<br /><br /> ELEMENT_TYPE_I4 ile bu tür için VT_HRESULT eşler.|  
|`NATIVE_TYPE_IINSPECTABLE`|Yerel `IInspectable` türü.|  
|`NATIVE_TYPE_HSTRING`|Yerel `HString`.|  
|`NATIVE_TYPE_MAX`|Geçersiz bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
