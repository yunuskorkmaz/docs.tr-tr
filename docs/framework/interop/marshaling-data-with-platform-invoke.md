---
title: Platform Çağırma ile Veri Sıralama
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
ms.openlocfilehash: b8c4e9d835db044912d1cbed92a14dd05e7de658
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399940"
---
# <a name="marshaling-data-with-platform-invoke"></a>Platform Çağırma ile Veri Sıralama

Yönetilmeyen bir kitaplıktan dışa aktarılan işlevleri çağırmak için ,.NET Framework uygulaması, yönetilmeyen işlevi temsil eden yönetilen kodda bir işlev prototipi gerektirir. Platform çağırmayı sağlayan bir prototip oluşturmak için verileri doğru bir şekilde ele kelemesi için aşağıdakileri yapmanız gerekir:

- <xref:System.Runtime.InteropServices.DllImportAttribute> Özniteliği yönetilen koddaki statik işlev veya yönteme uygulayın.

- Yönetilmeyen veri türleri için yönetilen veri türlerini değiştirin.

Özniteliği isteğe bağlı alanlarıyla uygulayarak ve yönetilen veri türlerini yönetilmeyen türler için ikame ederek eşdeğer yönetilen bir prototip oluşturmak için yönetilmeyen bir işlevle birlikte verilen belgeleri kullanabilirsiniz. Nasıl uygulanacağına ilişkin <xref:System.Runtime.InteropServices.DllImportAttribute>talimatlar için [bkz.](consuming-unmanaged-dll-functions.md)

Bu bölümde, bağımsız değişkenleri geçirip yönetilmeyen kitaplıklar tarafından dışa aktarılan işlevlerden iade değerleri almak için yönetilen işlev prototiplerinin nasıl oluşturulacaklarını gösteren örnekler sağlar. Örnekler ayrıca, verileri açıkça <xref:System.Runtime.InteropServices.MarshalAsAttribute> bağlamak için <xref:System.Runtime.InteropServices.Marshal> öznitelik ve sınıfın ne zaman kullanılacağını da gösterir.

## <a name="platform-invoke-data-types"></a>Platform çağrıcı veri türleri

Aşağıdaki tabloda Windows API'lerinde ve C stili işlevlerinde kullanılan veri türleri listelenir. Birçok yönetilmeyen kitaplık, bu veri türlerini parametre ve iade değerleri olarak geçen işlevler içerir. Üçüncü sütun, yönetilen kodda kullandığınız ilgili .NET Framework yerleşik değer türünü veya sınıfını listeler. Bazı durumlarda, tabloda listelenen tür için aynı boyutta bir tür değiştirebilirsiniz.

|Windows API'larında yönetilmeyen tür|Yönetilmeyen C dil türü|Yönetilen tür|Açıklama|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Değer döndürmeyen bir işleve uygulanır.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> veya <xref:System.UIntPtr?displayProperty=nameWithType>|32 bit Windows işletim sistemlerinde 32 bit, 64 bit Windows işletim sistemlerinde 64 bit.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bit|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bit|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bit|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bit|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bit|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> veya <xref:System.Int32?displayProperty=nameWithType>|32 bit|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|ANSI ile süsleyin.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Unicode ile süsleyin.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile süsleyin.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile süsleyin.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode ile süsleyin.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode ile süsleyin.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bit|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bit|

Visual Basic, C#ve C++'daki ilgili türler için [.NET Framework Class Kitaplığına Giriş'e](../../standard/class-library-overview.md#system-namespace)bakın.

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Aşağıdaki kod, Pinvoke.dll tarafından sağlanan kitaplık işlevlerini tanımlar. Bu bölümde açıklanan birçok örnek bu kitaplığı çağırır.

### <a name="example"></a>Örnek

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
