---
title: Parametre hazırlamayı özelleştirme-.NET
description: .NET 'in parametrelerinizi yerel bir gösterimde nasıl sıraladığında nasıl özelleştireceğinizi öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159617"
---
# <a name="customizing-parameter-marshaling"></a>Parametre hazırlamayı özelleştirme

.NET çalışma zamanının varsayılan parametre sıralama davranışı istediğiniz şeyi gerçekleştirmezse, kullanım parametrelerinden nasıl sıralandıklarınızı özelleştirmek için <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> özniteliğini kullanabilir.

## <a name="customizing-string-parameters"></a>Dize parametrelerini özelleştirme

.NET, dizeleri sıralama için çeşitli biçimlere sahiptir. Bu yöntemler, C stili dizeler ve Windows merkezli dize biçimleri üzerinde ayrı bölümlere ayrılır.

### <a name="c-style-strings"></a>C stili dizeler

Bu biçimlerin her biri, yerel koda null ile sonlandırılmış bir dize geçirir. Bunlar yerel dizenin kodlamasına göre farklılık gösterir.

| `System.Runtime.InteropServices.UnmanagedType` değeri | Encoding |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> biçimi biraz farklıdır. `LPWStr`gibi, dize, UTF-16 ' d e kodlanmış yerel bir C stili dizeye göre sıraar. Ancak, yönetilen imza dizeyi başvuruya göre geçirirseniz ve eşleşen yerel imza, dizeyi değere göre alır. Bu ayrım, değere göre bir dize alan ve bir `StringBuilder`kullanmak zorunda kalmadan yerinde değişiklik yapan yerel bir API kullanmanıza olanak sağlar. Eşleşmeyen yerel ve yönetilen imzalarla karışıklık oluşmasına yol açacağımız için bu biçimi kullanarak el ile karşı öneriyoruz.

### <a name="windows-centric-string-formats"></a>Windows merkezli dize biçimleri

COM veya OLE arabirimleriyle etkileşim kurarken, yerel işlevlerin dizeleri `BSTR` bağımsız değişken olarak ele geçirmesine benzer. Bir dizeyi `BSTR`olarak sıralamak için <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> yönetilmeyen türünü kullanabilirsiniz.

WinRT API 'Leri ile etkileşim ediyorsanız, bir dizeyi `HSTRING`olarak sıralamak için <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> biçimini kullanabilirsiniz.

## <a name="customizing-array-parameters"></a>Dizi parametrelerini özelleştirme

.NET ayrıca dizi parametrelerini sıralamak için birçok yol sağlar. C stili dizi alan bir API arıyorsanız <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> yönetilmeyen türünü kullanın. Dizideki değerlerin özelleştirilmiş sıralama ihtiyacı varsa, bunun için `[MarshalAs]` özniteliğinde <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> alanını kullanabilirsiniz.

COM API 'Leri kullanıyorsanız, muhtemelen dizi parametrelerinizi `SAFEARRAY*`s olarak sıralıyoruz. Bunu yapmak için <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> yönetilmeyen türünü kullanabilirsiniz. `SAFEARRAY` öğelerinin varsayılan türü, [`object` alanları özelleştirilirken](./customize-struct-marshaling.md#marshaling-systemobjects)tabloda görülebilir. `SAFEARRAY`öğesinin tam öğe türünü özelleştirmek için <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> alanlarını kullanabilirsiniz.

## <a name="customizing-boolean-or-decimal-parameters"></a>Boole veya ondalık parametrelerini özelleştirme

Boolean veya Decimal parametrelerini hazırlama hakkında bilgi için bkz. [Yapı hazırlamayı özelleştirme](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Nesne parametrelerini özelleştirme (yalnızca Windows)

Windows 'da, .NET çalışma zamanı, yerel koda nesne parametrelerini sıralamak için çeşitli yollar sağlar.

### <a name="marshaling-as-specific-com-interfaces"></a>Belirli COM arabirimleri olarak hazırlama

API 'niz bir COM nesnesine bir işaretçi alırsa, .NET 'in bu belirli arabirimler olarak Marshal konusunda bilgi almak için, `object`türü belirlenmiş bir parametre üzerinde aşağıdaki `UnmanagedType` biçimlerinden herhangi birini kullanabilirsiniz:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ayrıca, türü `[ComVisible(true)]` işaretlenmişse veya `object` türünü sıraaktarıyorsanız, nesnenizin COM görünümü için bir COM çağrılabilir sarmalayıcı olarak nesneyi sıralamak üzere <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> biçimini kullanabilirsiniz.

### <a name="marshaling-to-a-variant"></a>`VARIANT` sıralama

Yerel API 'niz bir Win32 `VARIANT`alırsa, nesnelerinizi `VARIANT`s olarak sıralamak için `object` parametresindeki <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> biçimini kullanabilirsiniz. .NET türleri ve `VARIANT` türleri arasındaki bir eşlemenin [`object` alanlarını özelleştirme](customize-struct-marshaling.md#marshaling-systemobjects) hakkındaki belgelere bakın.

### <a name="custom-marshalers"></a>Özel sıralayıcılar

Yerel bir COM arabirimini farklı bir yönetilen türe eklemek istiyorsanız, kendi özel sıralama kodunuzu sağlamak için `UnmanagedType.CustomMarshaler` biçimini ve <xref:System.Runtime.InteropServices.ICustomMarshaler> uygulamasını kullanabilirsiniz.
