---
title: "Platform Çağırma ile Veri Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71a4962029c0056287e97ea56dc02ae6cef8b603
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-platform-invoke"></a>Platform Çağırma ile Veri Hazırlama
Yönetilmeyen Kitaplığı'ndan dışarı aktarılan işlevleri çağırmak için bir işlev prototipi yönetilmeyen işlevi temsil eden yönetilen kodda .NET Framework uygulamasını gerektirir. Platform sağlayan prototip oluşturmak için veri doğru sıralamakta çağırma, aşağıdakileri yapmanız gerekir:  
  
-   Uygulama <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği statik işlev veya yöntem yönetilen kod için.  
  
-   Yönetilmeyen veri türleri için yönetilen veri türleri yerine koyun.  
  
 Yönetilmeyen işlev ile sağlanan belgelere özniteliği isteğe bağlı alanları ile uygulama ve yönetilmeyen türleri için yönetilen veri türleri değiştirerek bir eşdeğer yönetilen prototip oluşturmak için kullanabilirsiniz. Uygulama hakkında yönergeler için **DllImportAttribute**, bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Bu bölüm için bağımsız değişkenleri geçirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevlerden dönüş değerleri alma Yönetilen işlev prototipleri oluşturma gösteren örnekler sağlar. Örnekler de ne zaman kullanılacağını göstermek <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği ve <xref:System.Runtime.InteropServices.Marshal> veri açıkça sıralamakta sınıfı.  
  
## <a name="platform-invoke-data-types"></a>Platform çağırma veri türleri  
 Aşağıdaki tabloda, Win32 API (Wtypes.h içinde listelenen) ve C stili işlevlerde kullanılan veri türlerini listeler. Birçok yönetilmeyen kitaplıkları bu veri türleri parametreler ve dönüş değerleri işlevler içerir. Üçüncü sütun karşılık gelen .NET Framework yerleşik değer türü veya yönetilen kodda kullanma sınıfı listeler. Bazı durumlarda tabloda listelenen türü için aynı boyutta türünü değiştirebilirsiniz.  
  
|Wtypes.h yönetilmeyen türü|Yönetilmeyen C dil türü|Yönetilen sınıf adı|Açıklama|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**İŞLEME**|**void\***|<xref:System.IntPtr?displayProperty=nameWithType>|32 bit 32-bit Windows işletim sistemlerinde, 64-bit Windows işletim sistemlerinde 64 bit.|  
|**BAYT**|**İmzasız char**|<xref:System.Byte?displayProperty=nameWithType>|8 bit|  
|**KISA**|**kısa**|<xref:System.Int16?displayProperty=nameWithType>|16 bit|  
|**WORD**|**İmzasız short**|<xref:System.UInt16?displayProperty=nameWithType>|16 bit|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 bit|  
|**UINT**|**İmzasız int**|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|  
|**UZUN**|**uzun**|<xref:System.Int32?displayProperty=nameWithType>|32 bit|  
|**BOOL**|**uzun**|<xref:System.Byte>|32 bit|  
|**DWORD**|**İmzasız long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|  
|**ULONG**|**İmzasız long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bit|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|ANSI ile işaretleme.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Unicode ile işaretleme.|  
|**LPSTR**|**char\***|<xref:System.String?displayProperty=nameWithType>veya<xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile işaretleme.|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=nameWithType>veya<xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI ile işaretleme.|  
|**LPWSTR**|**wchar_t\***|<xref:System.String?displayProperty=nameWithType>veya<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode ile işaretleme.|  
|**LPCWSTR**|**Const wchar_t\***|<xref:System.String?displayProperty=nameWithType>veya<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode ile işaretleme.|  
|**KAYAN NOKTA**|**Kayan nokta**|<xref:System.Single?displayProperty=nameWithType>|32 bit|  
|**ÇİFT**|**Çift**|<xref:System.Double?displayProperty=nameWithType>|64 bit|  
  
 Karşılık gelen türlerin [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# ve C++, bkz: [.NET Framework sınıf kitaplığı giriş](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 Aşağıdaki kod Pinvoke.dll tarafından sağlanan kitaplık işlevleri tanımlar. Çok sayıda Bu bölümde çağrısında bu kitaplığı açıklanmaktadır.  
  
### <a name="example"></a>Örnek  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
