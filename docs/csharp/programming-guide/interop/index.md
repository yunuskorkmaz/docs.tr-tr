---
title: Birlikte çalışabilirlik-C# Programlama Kılavuzu
description: Birlikte çalışabilirlik, ortak dil çalışma zamanı altında çalışan kodun yanına yönetilmeyen kodu destekler. Birlikte çalışabilirlik seçeneklerini anlamak için bu kaynakları kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 84cdc16ccda7a5c629a90b0752071a98de81a9b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178482"
---
# <a name="interoperability-c-programming-guide"></a>Birlikte Çalışabilirlik (C# Programlama Kılavuzu)

Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımlardan korunmanızı ve avantajlarını yapmanızı sağlar. Ortak dil çalışma zamanının (CLR) denetimi altında çalışan koda *yönetilen kod*adı verılır ve CLR dışında çalışan koda *yönetilmeyen kod*denir. COM, COM+, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API, yönetilmeyen kod örnekleridir.  
  
.NET, platform çağırma Hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirliği ve com birlikte çalışabilirliği (com birlikte çalışma) aracılığıyla yönetilmeyen kod ile birlikte çalışabilirliği etkinleştirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Birlikte Çalışabilirliğe Genel Bakış](./interoperability-overview.md)  
 C# yönetilen kodu ve yönetilmeyen kod arasında birlikte çalışma yöntemlerini açıklar.  
  
 [Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](./how-to-access-office-onterop-objects.md)  
 Visual C# ' de Office programlamayı kolaylaştırmak Için sunulan özellikleri açıklar.  
  
 [COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.  
  
 [WAV dosyasını oynatmak için platform çağırma kullanma](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Windows işletim sisteminde bir. wav ses dosyası oynatmak için platform çağırma Hizmetleri ' nin nasıl kullanılacağını açıklar.  
  
 [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)  
 Çalışma kitabının bir bağlantısını içeren bir Excel çalışma kitabı ve Word belgesi oluşturmayı gösterir.  
  
 [Örnek COM Sınıfı](./example-com-class.md)  
 C# sınıfının bir COM nesnesi olarak nasıl kullanıma sunuleceğini gösterir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [temel kavramlar](~/_csharplang/spec/unsafe-code.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)
