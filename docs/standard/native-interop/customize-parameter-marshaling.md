---
title: Parametre hazırlamayı özelleştirme-.NET
description: .NET 'in parametrelerinizi yerel bir gösterimde nasıl sıraladığında nasıl özelleştireceğinizi öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 1999cad057875f15b283421f87f485c2e5ca2306
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374318"
---
# <a name="customizing-parameter-marshaling"></a>Parametre hazırlamayı özelleştirme

.NET çalışma zamanının varsayılan parametre sıralama davranışı istediğiniz şeyi gerçekleştirmezse, kullanım <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> parametrelerinizin nasıl sıralanmasını özelleştirmek için özniteliğini kullanabilir.

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

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType>Biçim biraz farklıdır. Benzer şekilde `LPWStr` , dizeyi, UTF-16 ' d e kodlanmış yerel bir C stili dizeye göre sıralamalıdır. Ancak, yönetilen imza dizeyi başvuruya göre geçirirseniz ve eşleşen yerel imza, dizeyi değere göre alır. Bu ayrım, bir dizeyi değere göre alan ve bir kullanarak yerinde değiştiren yerel bir API kullanmanıza olanak sağlar `StringBuilder` . Eşleşmeyen yerel ve yönetilen imzalarla karışıklık oluşmasına yol açacağımız için bu biçimi kullanarak el ile karşı öneriyoruz.

### <a name="windows-centric-string-formats"></a>Windows merkezli dize biçimleri

COM veya OLE arabirimleriyle etkileşim kurarken, yerel işlevlerin dizeleri bağımsız değişken olarak ele geçirmesine da fark edeceksiniz `BSTR` . <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>Yönetilmeyen türü bir dizeyi bir olarak sıralamak için kullanabilirsiniz `BSTR` .

WinRT API 'Leri ile etkileşim ediyorsanız, bir <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> dizeyi bir olarak sıralamak için biçimini kullanabilirsiniz `HSTRING` .

## <a name="customizing-array-parameters"></a>Dizi parametrelerini özelleştirme

.NET ayrıca dizi parametrelerini sıralamak için birçok yol sağlar. C stili dizi alan bir API arıyorsanız, <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> yönetilmeyen türü kullanın. Dizideki değerlerin özelleştirilmiş sıralama ihtiyacı varsa, <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> Bu alanı özniteliği üzerinde kullanabilirsiniz `[MarshalAs]` .

COM API 'Leri kullanıyorsanız, muhtemelen dizi parametrelerinizi s olarak sıralıyoruz `SAFEARRAY*` . Bunu yapmak için <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> yönetilmeyen türü kullanabilirsiniz. Öğelerinin varsayılan türü, `SAFEARRAY` [ `object` alanları özelleştirmek](./customize-struct-marshaling.md#marshal-systemobject)için tablosunda görülebilir. <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> Öğesinin tam öğe türünü özelleştirmek için ve alanlarını kullanabilirsiniz `SAFEARRAY` .

## <a name="customizing-boolean-or-decimal-parameters"></a>Boole veya ondalık parametrelerini özelleştirme

Boolean veya Decimal parametrelerini hazırlama hakkında bilgi için bkz. [Yapı hazırlamayı özelleştirme](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Nesne parametrelerini özelleştirme (yalnızca Windows)

Windows 'da, .NET çalışma zamanı, yerel koda nesne parametrelerini sıralamak için çeşitli yollar sağlar.

### <a name="marshaling-as-specific-com-interfaces"></a>Belirli COM arabirimleri olarak hazırlama

API 'niz bir COM nesnesine bir işaretçi alırsa, `UnmanagedType` `object` .net 'e bu özel arabirimler olarak sıralama yapmak için aşağıdaki biçimlerden herhangi birini yazılı bir parametre üzerinde kullanabilirsiniz:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ayrıca, tür işaretlenmişse `[ComVisible(true)]` veya `object` türü <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> sıraaktarıyorsanız, nesnenizin com görünümü IÇIN, nesneyi com çağrılabilir bir sarmalayıcı olarak sıralamak üzere biçimini kullanabilirsiniz.

### <a name="marshaling-to-a-variant"></a>Bir`VARIANT`

Yerel API 'niz bir Win32 alırsa `VARIANT` , <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> `object` nesnelerinizi s olarak sıralamak için parametresindeki biçimi kullanabilirsiniz `VARIANT` . .NET türleri ve türleri arasındaki eşleme için [ `object` alanları özelleştirmeye](customize-struct-marshaling.md#marshal-systemobject) yönelik belgelere bakın `VARIANT` .

### <a name="custom-marshalers"></a>Özel sıralayıcılar

Yerel bir COM arabirimini farklı bir yönetilen türe proje yapmak istiyorsanız, `UnmanagedType.CustomMarshaler` <xref:System.Runtime.InteropServices.ICustomMarshaler> kendi özel sıralama kodunuzu sağlamak için biçimini ve uygulamasını kullanabilirsiniz.
