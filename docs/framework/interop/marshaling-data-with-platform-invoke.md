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
ms.openlocfilehash: 396dc1dec60a6a984f9ddd0b8a8753b7293a5ab9
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307869"
---
# <a name="marshaling-data-with-platform-invoke"></a>Platform Çağırma ile Veri Sıralama

Yönetilmeyen bir kitaplığından dışa aktarılan işlevleri çağırmak için bir .NET Framework uygulaması yönetilmeyen işlev temsil eden yönetilen kodda bir işlev prototipi gerektirir. Platform sağlayan bir prototip oluşturmak için doğru veri sıralamakta çağırmak, aşağıdakileri yapmanız gerekir:

- Uygulama <xref:System.Runtime.InteropServices.DllImportAttribute> statik işlev veya yöntem yönetilen kodda özniteliği.

- Yönetilmeyen veri türleri için yönetilen veri türlerini değiştirin.

Yönetilmeyen bir işlev ile sağlanan belgelere özniteliği, isteğe bağlı alanları ile uygulama ve yönetilmeyen türleri için yönetilen veri türlerini değiştirerek bir eşdeğer yönetilen prototip oluşturmak için kullanabilirsiniz. Uygulama hakkında yönergeler için **DllImportAttribute**, bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).

Bu bölümde, bağımsız değişkenleri geçirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan İşlevler'den dönüş değerleri almak için Yönetilen işlev prototipleri oluşturma işlemini gösteren örnekleri sağlar. Örnekleri de ne zaman kullanılacağını göstermek <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği ve <xref:System.Runtime.InteropServices.Marshal> veri açıkça sıralamakta sınıfı.

## <a name="platform-invoke-data-types"></a>Platform çağırma veri türleri

Aşağıdaki tablo, C stili işlevleri ve Win32 API (Wtypes.h içinde listelenmiştir) içinde kullanılan veri türlerini listeler. Bu veri türlerini parametreler ve dönüş değerleri işlevleri birçok yönetilmeyen kitaplıkları içerir. Üçüncü sütunda, karşılık gelen .NET Framework yerleşik değer türünde veya yönetilen kodda kullanan sınıf listeler. Bazı durumlarda tabloda listelenen tür için aynı boyutta bir tür yerine kullanabilirsiniz.

|Yönetilmeyen tür Wtypes.h içinde|Yönetilmeyen C dil türü|Yönetilen tür adı|Açıklama|
|--------------------------------|-------------------------------|------------------------|-----------------|
|**GEÇERSİZ KILMA**|**void**|<xref:System.Void?displayProperty=nameWithType>|Bir değer döndürmeyen bir işlev uygulandı.|
|**TANITICI**|**Geçersiz kılma \***|<xref:System.IntPtr?displayProperty=nameWithType> veya <xref:System.UIntPtr?displayProperty=nameWithType>|32 bit 32-bit Windows işletim sistemlerine, 64 bit Windows işletim sistemlerinde 64 bit.|
|**BAYT**|**İmzasız char**|<xref:System.Byte?displayProperty=nameWithType>|8 bit|
|**KISA**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bit|
|**WORD**|**İmzasız short**|<xref:System.UInt16?displayProperty=nameWithType>|16 bit|
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 bit|
|**UINT**|**işaretsiz int**|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|**UZUN**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32 bit|
|**BOOL**|**long**|<xref:System.Boolean?displayProperty=nameWithType> veya <xref:System.Int32?displayProperty=nameWithType>|32 bit|
|**DWORD**|**İmzasız long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|**ULONG**|**İmzasız long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|ANSI ile işaretleme.|
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Unicode süslemek.|
|**LPSTR**|**Char &ast;**|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile işaretleme.|
|**LPCSTR**|**const char &ast;**|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile işaretleme.|
|**LPWSTR**|**wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode süslemek.|
|**LPCWSTR**|**wchar_t const &ast;**|<xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode süslemek.|
|**KAYAN NOKTA**|**float**|<xref:System.Single?displayProperty=nameWithType>|32 bit|
|**ÇİFT**|**double**|<xref:System.Double?displayProperty=nameWithType>|64 bit|

Karşılık gelen türler için [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# ve C++ için bkz: [.NET Framework sınıf kitaplığı giriş](../../../docs/standard/class-library-overview.md).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Aşağıdaki kod Pinvoke.dll tarafından sağlanan kitaplık işlevleri tanımlar. Çok sayıda Bu bölümde çağrısında bu kitaplığı açıklanmaktadır.

### <a name="example"></a>Örnek

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
