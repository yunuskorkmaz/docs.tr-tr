---
title: Birlikte çalışabilirlik - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 50f2a72bf4981a49d5597a9bc8922db81197d810
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710231"
---
# <a name="interoperability-c-programming-guide"></a>Birlikte Çalışabilirlik (C# Programlama Kılavuzu)
Birlikte çalışabilirlik, yönetilmeyen kodda mevcut yatırımlarınızdan yararlanın ve korumak sağlar. Ortak dil çalışma zamanı (CLR) denetimi altında çalışan kod çağrılır *yönetilen kod*, ve CLR dışında çalışan kod çağrılır *yönetilmeyen kod*. COM, COM +, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API yönetilmeyen kod örnekleridir.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Etkinleştirir birlikte çalışabilirlik platformu aracılığıyla yönetilmeyen kod ile çağırma Hizmetleri <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirlik (COM birlikte çalışma).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte Çalışabilirliğe Genel Bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 C# yönetilen kod ve yönetimsiz kod birlikte çalışmak için yöntemler açıklanır.  
  
 [Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Görsel Office programlama kolaylaştırmak için C# içinde sunulan özellikleri açıklar.  
  
 [Nasıl yapılır: COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Dizinli Özellikler parametrelere sahip COM özelliklere erişmek için kullanmayı açıklar.  
  
 [Nasıl yapılır: Wave dosyasını oynatmak için Platform çağırma kullanma](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Platform kullanmayı açıklar Windows işletim sisteminde .wav ses dosyasını oynatmak için hizmetleri.  
  
 [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Bir Excel çalışma kitabının ve çalışma kitabının bağlantısını içeren bir Word belgesi nasıl oluşturulacağını gösterir.  
  
 [Örnek COM Sınıfı](../../../csharp/programming-guide/interop/example-com-class.md)  
 C# sınıfı bir COM nesnesi olarak kullanıma sunmak nasıl gösterir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [temel kavramları](~/_csharplang/spec/unsafe-code.md) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../../docs/framework/interop/index.md)
- [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
