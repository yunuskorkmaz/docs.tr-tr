---
title: Parametre mareşalleme özelleştirme - .NET
description: .NET parametrelerinizi yerel bir gösterime nasıl görebilirsiniz öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400367"
---
# <a name="customizing-parameter-marshaling"></a>Parametre hazırlamayı özelleştirme

.NET çalışma zamanının varsayılan parametre mareşalleme davranışı istediğinizi yapmazsa, <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> parametrelerinizin nasıl marshaled olduğunu özelleştirmek için özniteliği kullanabilirsiniz.

## <a name="customizing-string-parameters"></a>Dize parametrelerini özelleştirme

.NET dizeleri mareşaliçin çeşitli biçimleri vardır. Bu yöntemler, C stili dizeleri ve Windows merkezli dize biçimleri üzerinde farklı bölümlere ayrılır.

### <a name="c-style-strings"></a>C-Style dizeleri

Bu biçimlerin her biri, null-sonlandırılan dizeyi yerel koda geçirir. Bunlar, yerel dizenin kodlanmasına göre farklılık gösterir.

| `System.Runtime.InteropServices.UnmanagedType`Değer | Encoding |
|------------------------------------------------------|----------|
| Lpstr | ANSI |
| LPUTF8Str | UTF-8 |
| Lpwstr | UTF-16 |
| Lptstr | UTF-16 |

Biçimi <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> biraz farklıdır. Gibi, `LPWStr`utf-16 kodlanmış bir yerli C tarzı dize için dize marshals. Ancak, yönetilen imza, dizeyi başvuru yla geçirmenizi ve eşleşen yerel imzanın dizeyi değerine göre alır. Bu ayrım, bir dize değeri alır ve bir `StringBuilder`kullanmak zorunda kalmadan yerinde değiştirir yerel bir API kullanmanıza olanak sağlar . Eşleşmeyen yerel ve yönetilen imzalarla karışıklığa neden olmaya yatkın olduğundan, bu biçimi el ile kullanmanızı öneririz.

### <a name="windows-centric-string-formats"></a>Windows merkezli dize biçimleri

COM veya OLE arabirimleriyle etkileşimde bulunurken, yerel işlevlerin dizeleri bağımsız değişken olarak `BSTR` kabul ettiğini büyük olasılıkla göreceksiniz. Bir dizeyi <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> `BSTR`' olarak mareşallemek için yönetilmeyen türü kullanabilirsiniz.

WinRT API'leri ile etkileşimde yseniz, <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> bir dizeyi `HSTRING`bir dize olarak mareşallemek için biçimi kullanabilirsiniz.

## <a name="customizing-array-parameters"></a>Dizi parametrelerini özelleştirme

.NET ayrıca dizi parametrelerini sıralamak için birden çok yol sağlar. C stili dizi alan bir API'yi arıyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> yönetilmeyen türü kullanın. Dizideki değerlerin özelleştirilmiş bir şekilde marshaling'e <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> ihtiyacı `[MarshalAs]` varsa, bunun için öznitelikteki alanı kullanabilirsiniz.

COM API'leri kullanıyorsanız, büyük olasılıkla dizi parametrelerinizi `SAFEARRAY*`s olarak belirlemeniz gerekir. Bunu yapmak için, <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> yönetilmeyen türü kullanabilirsiniz. Öğelerinin `SAFEARRAY` varsayılan [türü, özelleştirme `object` alanlarında](./customize-struct-marshaling.md#marshaling-systemobjects)tabloda görülebilir. Tam öğe <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> türünü <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> özelleştirmek için alanları ve `SAFEARRAY`alanları kullanabilirsiniz.

## <a name="customizing-boolean-or-decimal-parameters"></a>Boolean veya ondalık parametreleri özelleştirme

Boolean veya ondalık parametreler hakkında bilgi için [bkz.](customize-struct-marshaling.md)

## <a name="customizing-object-parameters-windows-only"></a>Nesne parametrelerini özelleştirme (yalnızca Windows)

Windows'da ,NET çalışma zamanı nesne parametrelerini yerel koda göre mareşallemek için çeşitli yollar sağlar.

### <a name="marshaling-as-specific-com-interfaces"></a>Belirli COM arabirimleri olarak marshaling

API'niz bir COM nesnesine işaretçi götürüyorsa, `UnmanagedType` .NET'i bu özel arabirimler olarak işaretlemeye söylemek için yazılı bir `object`parametrede aşağıdaki biçimlerinden birini kullanabilirsiniz:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ayrıca, türünüz işaretliyse `[ComVisible(true)]` veya `object` türü mareşallik ediyorsanız, türünüzdeki <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> COM görünümü için nesnenizi arama yla işaretlenebilir bir paket olarak biçimlendirmek için kullanabilirsiniz.

### <a name="marshaling-to-a-variant"></a>Bir mareşal`VARIANT`

Yerel API'niz `VARIANT`bir Win32 alıyorsa, nesnelerinizi s olarak <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> `object` `VARIANT`sıralamak için parametrenizdeki biçimi kullanabilirsiniz. .NET türleri ve `VARIANT` türleri arasında eşleme için [ `object` alanları özelleştirmeyle](customize-struct-marshaling.md#marshaling-systemobjects) ilgili belgelere bakın.

### <a name="custom-marshalers"></a>Özel mareşaller

Yerel bir COM arabirimini farklı bir yönetilen türe `UnmanagedType.CustomMarshaler` yansıtmak istiyorsanız, <xref:System.Runtime.InteropServices.ICustomMarshaler> kendi özel mareşalkodunuzu sağlamak için biçimini ve uygulamasını kullanabilirsiniz.
