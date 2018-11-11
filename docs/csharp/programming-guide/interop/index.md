---
title: Birlikte Çalışabilirlik (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: dc68a2a9c21f6fdb9b531bd07428325ac22ebfb6
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980654"
---
# <a name="interoperability-c-programming-guide"></a>Birlikte Çalışabilirlik (C# Programlama Kılavuzu)
Birlikte çalışabilirlik, yönetilmeyen kodda mevcut yatırımlarınızdan yararlanın ve korumak sağlar. Ortak dil çalışma zamanı (CLR) denetimi altında çalışan kod çağrılır *yönetilen kod*, ve CLR dışında çalışan kod çağrılır *yönetilmeyen kod*. COM, COM +, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Win32 API yönetilmeyen kod örnekleridir.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Etkinleştirir birlikte çalışabilirlik platformu aracılığıyla yönetilmeyen kod ile çağırma Hizmetleri <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirlik (COM birlikte çalışma).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte Çalışabilirliğe Genel Bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 C# yönetilen kod ve yönetimsiz kod birlikte çalışmak için yöntemler açıklanır.  
  
 [Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Görsel Office programlama kolaylaştırmak için C# içinde sunulan özellikleri açıklar.  
  
 [Nasıl yapılır: COM Birlikte Çalışma Programlamada Dizin Oluşturulmuş Özellikleri Kullanma](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Dizinli Özellikler parametrelere sahip COM özelliklere erişmek için kullanmayı açıklar.  
  
 [Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Platform kullanmayı açıklar Windows işletim sisteminde .wav ses dosyasını oynatmak için hizmetleri.  
  
 [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Bir Excel çalışma kitabının ve çalışma kitabının bağlantısını içeren bir Word belgesi nasıl oluşturulacağını gösterir.  
  
 [Örnek COM Sınıfı](../../../csharp/programming-guide/interop/example-com-class.md)  
 C# sınıfı bir COM nesnesi olarak kullanıma sunmak nasıl gösterir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [temel kavramları](~/_csharplang/spec/unsafe-code.md) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../../docs/framework/interop/index.md)  
- [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
