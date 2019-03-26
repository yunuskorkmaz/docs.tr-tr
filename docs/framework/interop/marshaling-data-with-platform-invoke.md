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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cb310dc6d786c3c7711f4c194c6623324c777dd
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412402"
---
# <a name="marshaling-data-with-platform-invoke"></a>Platform Çağırma ile Veri Sıralama

Yönetilmeyen bir kitaplığından dışa aktarılan işlevleri çağırmak için bir .NET Framework uygulaması yönetilmeyen işlev temsil eden yönetilen kodda bir işlev prototipi gerektirir. Platform sağlayan bir prototip oluşturmak için doğru veri sıralamakta çağırmak, aşağıdakileri yapmanız gerekir:

- Uygulama <xref:System.Runtime.InteropServices.DllImportAttribute> statik işlev veya yöntem yönetilen kodda özniteliği.

- Yönetilmeyen veri türleri için yönetilen veri türlerini değiştirin.

Yönetilmeyen bir işlev ile sağlanan belgelere özniteliği, isteğe bağlı alanları ile uygulama ve yönetilmeyen türleri için yönetilen veri türlerini değiştirerek bir eşdeğer yönetilen prototip oluşturmak için kullanabilirsiniz. Uygulama hakkında yönergeler için <xref:System.Runtime.InteropServices.DllImportAttribute>, bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).

Bu bölümde, bağımsız değişkenleri geçirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan İşlevler'den dönüş değerleri almak için Yönetilen işlev prototipleri oluşturma işlemini gösteren örnekleri sağlar. Örnekleri de ne zaman kullanılacağını göstermek <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği ve <xref:System.Runtime.InteropServices.Marshal> veri açıkça sıralamakta sınıfı.

## <a name="platform-invoke-data-types"></a>Platform çağırma veri türleri

Aşağıdaki tabloda, Windows API'ları ve C-stili İşlevler'de kullanılan veri türlerini listeler. Bu veri türlerini parametreler ve dönüş değerleri işlevleri birçok yönetilmeyen kitaplıkları içerir. Üçüncü sütunda, karşılık gelen .NET Framework yerleşik değer türünde veya yönetilen kodda kullanan sınıf listeler. Bazı durumlarda tabloda listelenen tür için aynı boyutta bir tür yerine kullanabilirsiniz.

|Windows API'lerindeki yönetilmeyen tür|Yönetilmeyen C dil türü|Yönetilen tür|Açıklama|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Bir değer döndürmeyen bir işlev uygulandı.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> veya <xref:System.UIntPtr?displayProperty=nameWithType>|32 bit 32-bit Windows işletim sistemlerine, 64 bit Windows işletim sistemlerinde 64 bit.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bit|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bit|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bit|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bit|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bit|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> veya <xref:System.Int32?displayProperty=nameWithType>|32 bit|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|ANSI ile işaretleme.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Unicode süslemek.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile işaretleme.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile işaretleme.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode süslemek.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode süslemek.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bit|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bit|

Visual Basic'de karşılık gelen türler için C#ve C++ bkz [.NET Framework sınıf kitaplığı giriş](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Aşağıdaki kod Pinvoke.dll tarafından sağlanan kitaplık işlevleri tanımlar. Çok sayıda Bu bölümde çağrısında bu kitaplığı açıklanmaktadır.

### <a name="example"></a>Örnek

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
