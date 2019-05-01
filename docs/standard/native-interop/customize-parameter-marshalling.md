---
title: Özelleştirme parametre taşıma - .NET
description: .NET yerel gösterimine parametrelerinizi nasıl sürekliliğe devreder özelleştirmeyi öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 7821da546e0ed0ab5fa97d00a638aa5cc1a3089c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973595"
---
# <a name="customizing-parameter-marshalling"></a>Parametre taşıma özelleştirme

.NET çalışma zamanının varsayılan parametre sıralama davranışını istediklerinizi yapmaz, kullanım kullanabilirsiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> parametrelerinizi nasıl sıralanmış özelleştirmek için özniteliği.

## <a name="customizing-string-parameters"></a>Dize parametreleri özelleştirme

.NET, çeşitli biçimlerde düzenleme dizeler için vardır. Bu yöntemler, C stili dizeler ve dize biçimleri Windows merkezli ayrı bölümlere ayrılır.

### <a name="c-style-strings"></a>C stili dizeler

Her biri Bu biçimler yerel kod için null ile sonlandırılmış bir dize geçirir. Bunlar, yerel dizesi kodlayarak farklılık gösterir.

| `System.Runtime.InteropServices.UnmanagedType` Değer | Encoding |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 | 
| LPWStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> Biçimi biraz farklıdır. Gibi `LPWStr`, yerel C stili dizeyi UTF-16 kodlamalı dize sıralar. Ancak, başvuruya göre dizesine geçmenizi yönetilen imzaya sahip ve eşleşen yerel imza dize değerine göre alır. Bu ayrım değere göre bir dize alır ve değiştirdiği bir yerel API kullanmak üzere yerinde kullanmak zorunda kalmadan sağlar bir `StringBuilder`. Eşleşmeyen yerel ve yönetilen imzalarla karışıklığa neden eğilimlidir olduğundan el ile şu biçimi kullanarak karşı öneririz.

### <a name="windows-centric-string-formats"></a>Windows merkezli dize biçimleri

COM veya OLE arabirimleri ile etkileşim kurulurken, büyük olasılıkla yerel işlevleri dize olarak alın bulabilirsiniz `BSTR` bağımsız değişkenler. Kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> türü bir dize olarak hazırlamak için yönetilmeyen bir `BSTR`.

WinRT API'lar ile etkileşim kurma, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> biçiminde bir dize olarak hazırlamak için bir `HSTRING`.

## <a name="customizing-array-parameters"></a>Dizi parametreleri özelleştirme

.NET de sıralama dizi parametreleri için birden çok yol sağlar. Bir C tarzı dizi alan bir API arıyoruz kullanırsanız <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> yönetilmeyen türü. Dizideki değerleri, özelleştirilmiş taşıma gerekiyorsa, kullanabileceğiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> alanını `[MarshalAs]` söz konusu öznitelik.

COM API kullanıyorsanız, büyük olasılıkla, dizi parametreleri olarak sıralamanız gerekir `SAFEARRAY*`s. Bunu yapmak için kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> yönetilmeyen türü. Varsayılan tür öğelerinin `SAFEARRAY` tablodaki görülebilir [özelleştirme `object` alanları](./customize-struct-marshalling.md#marshalling-systemobjects). Kullanabileceğiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> tam öğe özelleştirmek için alanları türü `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Ondalık ya da Boole parametreleri özelleştirme

Ondalık ya da Boole parametreleri taşıma hakkında daha fazla bilgi için bkz: [yapısı taşıma özelleştirme](customize-struct-marshalling.md).

## <a name="customizing-object-parameters-windows-only"></a>Nesnesi parametrelerini özelleştirme (yalnızca Windows)

Windows üzerinde .NET çalışma zamanı bir nesne parametreleri yerel kod için hazırlamak için farklı yollar sağlar.

### <a name="marshalling-as-specific-com-interfaces"></a>Belirli bir COM arabirimleri olarak taşıma

API'nizi bir COM nesnesi için bir işaretçi alır, aşağıdakilerden herhangi birini kullanabilirsiniz `UnmanagedType` biçimleri üzerinde bir `object`-yazılan bu belirli arabirimleri hazırlamak için .NET bildirmek için parametre:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ayrıca, türünüz işaretlenmişse `[ComVisible(true)]` veya taşıma `object` kullanabileceğiniz türü <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> COM çağrılabilir sarmalayıcı COM görünümün türünüz olarak nesnenizin sıralamakta biçimi.

### <a name="marshalling-to-a-variant"></a>Taşıma için bir `VARIANT`

API'nizi yerel bir Win32 sürerse `VARIANT`, kullanabileceğiniz <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> Biçimlendir, `object` nesnelerinizi olarak hazırlamak için parametre `VARIANT`s. İlgili belgelere bakın [özelleştirme `object` alanları](customize-struct-marshalling.md#marshalling-systemobjects) .NET türleri arasında bir eşleme için ve `VARIANT` türleri.

### <a name="custom-marshalers"></a>Özel sıralayıcılara

Yerel bir COM arabirimi farklı bir yönetilen türü proje istiyorsanız kullanabileceğiniz `UnmanagedType.CustomMarshaler` biçimi ve uygulaması <xref:System.Runtime.InteropServices.ICustomMarshaler> kendi özel sıralama kodu sağlayabilir.
