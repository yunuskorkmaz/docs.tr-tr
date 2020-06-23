---
title: Platform Çağırma ile Veri Sıralama
description: .NET ' te platform çağırma ile verileri sıralama. Windows API 'Leri ve C stili işlevlerde kullanılan veri türlerinin bir listesini görün ve .NET yönetilen tür eşdeğerlerini bulun.
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
ms.openlocfilehash: 27045790780c1eef9537bdf7e52deb579e2b467c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904110"
---
# <a name="marshaling-data-with-platform-invoke"></a>Platform Çağırma ile Veri Sıralama

Yönetilmeyen bir kitaplıktan aktarılmış işlevleri çağırmak için, bir .NET Framework uygulaması yönetilmeyen işlevi temsil eden yönetilen kodda bir işlev prototipi gerektirir. Platform Invoke 'ın verileri doğru bir şekilde sıralaması için bir prototip oluşturmak üzere şunları yapmanız gerekir:

- Özniteliği, <xref:System.Runtime.InteropServices.DllImportAttribute> Yönetilen koddaki statik işleve veya yöntemine uygulayın.

- Yönetilmeyen veri türleri için yönetilen veri türlerini değiştirin.

Özniteliği isteğe bağlı alanlarıyla uygulayıp yönetilmeyen türler için yönetilen veri türlerini değiştirerek eşdeğer bir yönetilen prototip oluşturmak için, yönetilmeyen bir işlevle sağlanan belgeleri kullanabilirsiniz. Uygulamasına nasıl uygulandığına ilişkin yönergeler için <xref:System.Runtime.InteropServices.DllImportAttribute> bkz. [yönetilmeyen DLL işlevlerini](consuming-unmanaged-dll-functions.md)kullanma.

Bu bölümde, yönetilmeyen kitaplıklar tarafından dışarıya aktarılmış işlevlerden gelen bağımsız değişkenleri iletmek ve dönüş değerlerini almak için yönetilen işlev prototürlerinin nasıl oluşturulacağı gösterilmektedir. Örnekler Ayrıca, <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Runtime.InteropServices.Marshal> verileri açıkça sıralamak için özniteliği ve sınıfını ne zaman kullanacağınızı gösterir.

## <a name="platform-invoke-data-types"></a>Platform çağırma veri türleri

Aşağıdaki tabloda, Windows API 'Leri ve C stili işlevlerinde kullanılan veri türleri listelenmektedir. Birçok yönetilmeyen kitaplık, bu veri türlerini parametre olarak geçen ve değer döndüren işlevleri içerir. Üçüncü sütunda karşılık gelen .NET Framework yerleşik değer türü veya yönetilen kodda kullandığınız sınıf listelenir. Bazı durumlarda, tabloda listelenen tür için aynı boyuttaki bir türü değiştirebilirsiniz.

|Windows API 'Lerinde yönetilmeyen tür|Yönetilmeyen C dil türü|Yönetilen tür|Description|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Değer döndürmeyen bir işleve uygulandı.|
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
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|ANSI ile süslemek.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Unicode ile süsle.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile süslemek.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile süslemek.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode ile süsle.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode ile süsle.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bit|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bit|

Visual Basic, C# ve C++ ' daki ilgili türler için [.NET Framework sınıfı kitaplığına giriş](../../standard/class-library-overview.md#system-namespace)bölümüne bakın.

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Aşağıdaki kod, Pinvoke.dll tarafından sunulan kitaplık işlevlerini tanımlar. Bu bölümde açıklanan birçok örnek, bu kitaplığı çağırır.

### <a name="example"></a>Örnek

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
