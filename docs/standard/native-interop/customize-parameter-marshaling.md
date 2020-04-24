---
title: Parametre hazırlamayı özelleştirme-.NET
description: .NET 'in parametrelerinizi yerel bir gösterimde nasıl sıraladığında nasıl özelleştireceğinizi öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400367"
---
# <a name="customizing-parameter-marshaling"></a>Parametre hazırlamayı özelleştirme

.NET çalışma zamanının varsayılan parametre sıralama davranışı istediğiniz şeyi gerçekleştirmezse, kullanım parametrelerinizin nasıl sıralanmasını özelleştirmek <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> için özniteliğini kullanabilir.

## <a name="customizing-string-parameters"></a>Dize parametrelerini özelleştirme

.NET, dizeleri sıralama için çeşitli biçimlere sahiptir. Bu yöntemler, C stili dizeler ve Windows merkezli dize biçimleri üzerinde ayrı bölümlere ayrılır.

### <a name="c-style-strings"></a>C stili dizeler

Bu biçimlerin her biri, yerel koda null ile sonlandırılmış bir dize geçirir. Bunlar yerel dizenin kodlamasına göre farklılık gösterir.

| `System.Runtime.InteropServices.UnmanagedType`deeri | Encoding |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> Biçim biraz farklıdır. Benzer `LPWStr`şekilde, DIZEYI, UTF-16 ' d e kodlanmış yerel bir C stili dizeye göre sıralamalıdır. Ancak, yönetilen imza dizeyi başvuruya göre geçirirseniz ve eşleşen yerel imza, dizeyi değere göre alır. Bu ayrım, bir dizeyi değere göre alan ve bir `StringBuilder`kullanarak yerinde değiştiren yerel bir API kullanmanıza olanak sağlar. Eşleşmeyen yerel ve yönetilen imzalarla karışıklık oluşmasına yol açacağımız için bu biçimi kullanarak el ile karşı öneriyoruz.

### <a name="windows-centric-string-formats"></a>Windows merkezli dize biçimleri

COM veya OLE arabirimleriyle etkileşim kurarken, yerel işlevlerin dizeleri bağımsız değişken olarak `BSTR` ele geçirmesine da fark edeceksiniz. <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> Yönetilmeyen türü bir dizeyi bir `BSTR`olarak sıralamak için kullanabilirsiniz.

WinRT API 'Leri ile etkileşim ediyorsanız, bir dizeyi bir <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> `HSTRING`olarak sıralamak için biçimini kullanabilirsiniz.

## <a name="customizing-array-parameters"></a>Dizi parametrelerini özelleştirme

.NET ayrıca dizi parametrelerini sıralamak için birçok yol sağlar. C stili dizi alan bir API arıyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> yönetilmeyen türü kullanın. Dizideki değerlerin özelleştirilmiş sıralama ihtiyacı varsa, bu <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> alanı `[MarshalAs]` özniteliği üzerinde kullanabilirsiniz.

COM API 'Leri kullanıyorsanız, muhtemelen dizi parametrelerinizi s olarak `SAFEARRAY*`sıralıyoruz. Bunu yapmak için <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> yönetilmeyen türü kullanabilirsiniz. Öğelerinin varsayılan türü, `SAFEARRAY` [alanları özelleştirmek `object` ](./customize-struct-marshaling.md#marshaling-systemobjects)için tablosunda görülebilir. Öğesinin tam öğe türünü <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> özelleştirmek <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> için ve alanlarını kullanabilirsiniz `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Boole veya ondalık parametrelerini özelleştirme

Boolean veya Decimal parametrelerini hazırlama hakkında bilgi için bkz. [Yapı hazırlamayı özelleştirme](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Nesne parametrelerini özelleştirme (yalnızca Windows)

Windows 'da, .NET çalışma zamanı, yerel koda nesne parametrelerini sıralamak için çeşitli yollar sağlar.

### <a name="marshaling-as-specific-com-interfaces"></a>Belirli COM arabirimleri olarak hazırlama

API 'niz bir COM nesnesine bir işaretçi alırsa, .NET 'e bu özel arabirimler olarak sıralama yapmak için `UnmanagedType` aşağıdaki biçimlerden herhangi `object`birini yazılı bir parametre üzerinde kullanabilirsiniz:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ayrıca, tür işaretlenmişse `[ComVisible(true)]` veya `object` türü sıraaktarıyorsanız, nesnenizin com görünümü için, nesneyi com çağrılabilir bir <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> sarmalayıcı olarak sıralamak üzere biçimini kullanabilirsiniz.

### <a name="marshaling-to-a-variant"></a>Bir`VARIANT`

Yerel API `VARIANT`'Niz bir Win32 alırsa, nesnelerinizi s olarak <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> `object` `VARIANT`sıralamak için parametresindeki biçimi kullanabilirsiniz. .NET türleri ve `VARIANT` türleri arasındaki eşleme için [alanları özelleştirmeye `object` ](customize-struct-marshaling.md#marshaling-systemobjects) yönelik belgelere bakın.

### <a name="custom-marshalers"></a>Özel sıralayıcılar

Yerel bir COM arabirimini farklı bir yönetilen türe proje yapmak istiyorsanız, kendi özel sıralama kodunuzu sağlamak `UnmanagedType.CustomMarshaler` <xref:System.Runtime.InteropServices.ICustomMarshaler> için biçimini ve uygulamasını kullanabilirsiniz.
