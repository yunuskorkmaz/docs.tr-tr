---
title: Birlikte çalışabilirlik - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712058"
---
# <a name="interoperability-c-programming-guide"></a>Birlikte Çalışabilirlik (C# Programlama Kılavuzu)
Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımları korumanızı ve bunlardan yararlanmanızı sağlar. Ortak dil çalışma zamanı (CLR) denetimi altında çalışan kod *yönetilen kod*olarak adlandırılır ve CLR dışında çalışan kod *yönetilmeyen kod*olarak adlandırılır. COM, COM+, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API'sı yönetilmeyen kod örnekleridir.  
  
 .NET Framework, platform çağırma hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirlik (COM interop) aracılığıyla yönetilmeyen kodla birlikte çalışabilirlik sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte Çalışabilirliğe Genel Bakış](./interoperability-overview.md)  
 C# yönetilen kod ve yönetilmeyen kod arasında etkileşim yöntemlerini açıklar.  
  
 [Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](./how-to-access-office-onterop-objects.md)  
 Office programlamayı kolaylaştırmak için Visual C# 'da tanıtılan özellikleri açıklar.  
  
 [COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.  
  
 [WAV dosyasını oynatmak için platform çağırma kullanma](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Windows işletim sisteminde bir .wav ses dosyası çalmak için platform çağırma hizmetlerinin nasıl kullanılacağını açıklar.  
  
 [Walkthrough: Office Programlama](./walkthrough-office-programming.md)  
 Excel çalışma kitabı nın ve çalışma kitabına bağlantı içeren bir Word belgesinin nasıl oluşturulup oluşturulabildiğini gösterir.  
  
 [Örnek COM Sınıfı](./example-com-class.md)  
 Bir C# sınıfının COM nesnesi olarak nasıl ortaya çıkarılabildiğini gösterir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [Temel kavramlara](~/_csharplang/spec/unsafe-code.md) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
- [Walkthrough: Office Programlama](./walkthrough-office-programming.md)
