---
title: Birlikte çalışabilirlik C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 896f89304289fd90c10da9aaa7ea15ada35ef8f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589085"
---
# <a name="interoperability-c-programming-guide"></a>Birlikte Çalışabilirlik (C# Programlama Kılavuzu)
Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımlardan korunmanızı ve avantajlarını yapmanızı sağlar. Ortak dil çalışma zamanının (CLR) denetimi altında çalışan koda *yönetilen kod*adı verılır ve CLR dışında çalışan koda *yönetilmeyen kod*denir. COM, COM+, C++ bileşenler, ActiveX bileşenleri ve MICROSOFT Windows API, yönetilmeyen kod örnekleridir.  
  
 .NET Framework platform çağırma Hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve com birlikte çalışabilirliği (com birlikte çalışma) aracılığıyla yönetilmeyen kodla birlikte çalışabilirliğe izin verebilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte Çalışabilirliğe Genel Bakış](./interoperability-overview.md)  
 Yönetilen kod ve yönetilmeyen kod C# arasında birlikte çalışma yöntemlerini açıklar.  
  
 [Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişin](./how-to-access-office-onterop-objects.md)  
 Office programlama işlemini kolaylaştırmak için görselde C# tanıtılan özellikleri açıklar.  
  
 [Nasıl yapılır: COM birlikte çalışma programlamada dizinli özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.  
  
 [Nasıl yapılır: Bir Wave dosyasını oynatmak için platform çağırma kullanma](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Windows işletim sisteminde bir. wav ses dosyası oynatmak için platform çağırma Hizmetleri ' nin nasıl kullanılacağını açıklar.  
  
 [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)  
 Çalışma kitabının bir bağlantısını içeren bir Excel çalışma kitabı ve Word belgesi oluşturmayı gösterir.  
  
 [Örnek COM Sınıfı](./example-com-class.md)  
 Bir C# SıNıFıN bir com nesnesi olarak nasıl kullanıma sunuleceğini gösterir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [temel kavramlar](~/_csharplang/spec/unsafe-code.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)
