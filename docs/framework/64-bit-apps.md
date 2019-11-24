---
title: 64 bitlik Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
ms.openlocfilehash: 90e022d5643dc49ccc5b78d071b3b473c92f0670
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429670"
---
# <a name="64-bit-applications"></a>64 bitlik Uygulamalar
Bir uygulamayı derlediğinizde, 64 bitlik bir Windows işletim sisteminde yerel uygulama olarak ya da WOW64 (Windows 64-bit üzerinde Windows-32-bit) altında çalışmasını belirtebilirsiniz. WOW64, 32 bitlik bir uygulamanın 64 bitlik bir sistemde çalışmasını sağlayan bir uyumluluk ortamıdır. WOW64, Windows işletim sisteminin tüm 64 bitlik sürümlerinde bulunur.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Windows'da 32-Bit ve 64-bit Uygulamalar Çalıştırma  
 .NET Framework 1.0 veya 1.1 üzerinde oluşturulan tüm uygulamalar, 64 bitlik bir işletim sisteminde 32 bitlik uygulamalar olarak kabul edilir ve her zaman WOW64 ve 32 bitlik ortak dil çalışma zamanı (CLR) altında yürütülür. 32-bit applications that are built on the .NET Framework 4 or later versions also run under WOW64 on 64-bit systems.  
  
 Visual Studio, bir x86 bilgisayara CLR'nin 32 bitlik sürümünü, ve 64 bitlik bir Windows bilgisayara hem CLR'nin hem 32 bitlik hem de uygun 64 bitlik sürümünü yükler. (Visual Studio 32 bitlik bir uygulama olduğu için, 64 bitlik bir sisteme yüklendiğinde WOW64 altında çalışır.)  
  
> [!NOTE]
> Itanium işlemci ailesine ait x86 öykünmesinin ve WOW64 alt sisteminin tasarımı nedeniyle uygulamalar tek işlemcide yürütülmeye sınırlıdır. Bu etkenler, Itanium tabanlı sistemlerde çalışan 32 bitlik .NET Framework uygulamalarının performansını ve ölçeklenebilirliğini azaltır. We recommend that you use the .NET Framework 4, which includes native 64-bit support for Itanium-based systems, for increased performance and scalability.  
  
 Varsayılan olarak, 64 bitlik bir Windows işletim sisteminde 64 bitlik yönetilen bir uygulama çalıştırdığınızda, 2 gigabayttan (GB) daha büyük bir nesne oluşturamazsınız. However, in the .NET Framework 4.5, you can increase this limit.  For more information, see the [\<gcAllowVeryLargeObjects> element](./configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Çoğu derleme, 32 bitlik CLR ve 64 bitlik CLR'de aynı şekilde çalışır. Ancak bazı programlar, eğer aşağıdakilerden bir veya daha fazlasını içeriyorlarsa CLR'ye bağlı olarak farklı şekilde davranabilir:  
  
- Platforma göre boyutunu değiştiren üyeler içeren yapılar (örneğin, herhangi bir işaretçi türü).  
  
- Sabit boyutlar içeren işaretçi aritmetiği.  
  
- Tanıtıcılar için `Int32` yerine `IntPtr` kullanan yanlış platform çağrıları veya COM bildirimleri.  
  
- `IntPtr` öğesini `Int32`'e yayınlayan kod.  
  
 For more information about how to port a 32-bit application to run on the 64-bit CLR, see [Migrating 32-bit Managed Code to 64-bit](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10)).  
  
## <a name="general-64-bit-programming-information"></a>Genel 64-Bit Programlama Bilgileri  
 64 bit programlama hakkında genel bilgi için, aşağıdaki belgelere bakın:  
  
- In the Windows SDK documentation, see [Programming Guide for 64-bit Windows](/windows/win32/winprog64/programming-guide-for-64-bit-windows).  
  
- For information about Visual Studio support for creating 64-bit applications, see [Visual Studio IDE 64-Bit Support](/visualstudio/ide/visual-studio-ide-64-bit-support).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>64-Bit Uygulamalar Oluşturmak için Derleme Desteği  
 Varsayılan olarak, 32 bitlik veya 64 bitlik bir bilgisayarda uygulama oluşturmak için .NET Framework'ü kullandığınızda, uygulama 64 bitlik bir bilgisayarda yerel uygulama olarak (yani WOW64 altında olmadan) çalışır. Aşağıdaki tablo, yerel olarak, WOW64 altında veya her iki şekilde de çalışacak olan 64 bitlik uygulamalar oluşturmak için Visual Studio'nun nasıl kullanıldığını açıklayan belgeleri listeler.  
  
|Compiler|Derleyici seçeneği|  
|--------------|---------------------|  
|Visual Basic|[-platform (Visual Basic)](../visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[-platform (C# Compiler Options)](../csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|You can create platform-agnostic, Microsoft intermediate language (MSIL) applications by using **/clr:safe**. For more information, see [-clr (Common Language Runtime Compilation)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++, 64 bitlik her bir işletim sistemi için ayrı bir derleyici içerir. For more information about how to use Visual C++ to create native applications that run on a 64-bit Windows operating system, see [64-bit Programming](/cpp/build/configuring-programs-for-64-bit-visual-cpp).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Bir .exe Dosyası veya .dll Dosyasının Durumunu Belirleme  
 To determine whether an .exe file or .dll file is meant to run only on a specific platform or under WOW64, use [CorFlags.exe (CorFlags Conversion Tool)](./tools/corflags-exe-corflags-conversion-tool.md) with no options. Bir .exe dosyasının veya .dll dosyasının platform durumunu değiştirmek için aynı zamanda CorFlags.exe'yi de kullanabilirsiniz. Bir Visual Studio derlemesinin CLR başlığının ana çalışma zamanı sürümü numarası 2 olarak, alt çalışma zamanı sürümü numarası ise 5 olarak ayarlanır. Alt çalışma zamanı sürümü 0 olarak ayarlanan uygulamalar eski uygulamalar olarak işlenir ve her zaman WOW64 altında yürütülür.  
  
 Bir .exe veya .dll dosyasını, belirli bir platformda mı yoksa WOW4 altında mı çalışmak için tasarlandığını görmek üzere program aracılığıyla sorgulamak amacıyla <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> yöntemini kullanın.
