---
title: 64 bitlik Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
ms.openlocfilehash: 90e022d5643dc49ccc5b78d071b3b473c92f0670
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74429670"
---
# <a name="64-bit-applications"></a>64 bitlik Uygulamalar
Bir uygulamayı derlediğinizde, 64 bitlik bir Windows işletim sisteminde yerel uygulama olarak ya da WOW64 (Windows 64-bit üzerinde Windows-32-bit) altında çalışmasını belirtebilirsiniz. WOW64, 32 bitlik bir uygulamanın 64 bitlik bir sistemde çalışmasını sağlayan bir uyumluluk ortamıdır. WOW64, Windows işletim sisteminin tüm 64 bitlik sürümlerinde bulunur.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Windows'da 32-Bit ve 64-bit Uygulamalar Çalıştırma  
 .NET Framework 1.0 veya 1.1 üzerinde oluşturulan tüm uygulamalar, 64 bitlik bir işletim sisteminde 32 bitlik uygulamalar olarak kabul edilir ve her zaman WOW64 ve 32 bitlik ortak dil çalışma zamanı (CLR) altında yürütülür. .NET Framework 4 veya sonraki sürümler üzerinde oluşturulmuş 32 bit uygulamalar da 64 bit sistemlerde WOW64 altında çalışır.  
  
 Visual Studio, bir x86 bilgisayara CLR'nin 32 bitlik sürümünü, ve 64 bitlik bir Windows bilgisayara hem CLR'nin hem 32 bitlik hem de uygun 64 bitlik sürümünü yükler. (Visual Studio 32 bitlik bir uygulama olduğu için, 64 bitlik bir sisteme yüklendiğinde WOW64 altında çalışır.)  
  
> [!NOTE]
> Itanium işlemci ailesine ait x86 öykünmesinin ve WOW64 alt sisteminin tasarımı nedeniyle uygulamalar tek işlemcide yürütülmeye sınırlıdır. Bu etkenler, Itanium tabanlı sistemlerde çalışan 32 bitlik .NET Framework uygulamalarının performansını ve ölçeklenebilirliğini azaltır. Daha yüksek performans ve ölçeklenebilirlik için Itanium tabanlı sistemler için yerel 64 bit desteği içeren .NET Framework 4'ü kullanmanızı öneririz.  
  
 Varsayılan olarak, 64 bitlik bir Windows işletim sisteminde 64 bitlik yönetilen bir uygulama çalıştırdığınızda, 2 gigabayttan (GB) daha büyük bir nesne oluşturamazsınız. Ancak, .NET Framework 4.5'te bu sınırı artırabilirsiniz.  Daha fazla bilgi için [ \<gcAllowVeryLargeObjects> öğesine](./configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)bakın.  
  
 Çoğu derleme, 32 bitlik CLR ve 64 bitlik CLR'de aynı şekilde çalışır. Ancak bazı programlar, eğer aşağıdakilerden bir veya daha fazlasını içeriyorlarsa CLR'ye bağlı olarak farklı şekilde davranabilir:  
  
- Platforma göre boyutunu değiştiren üyeler içeren yapılar (örneğin, herhangi bir işaretçi türü).  
  
- Sabit boyutlar içeren işaretçi aritmetiği.  
  
- Tanıtıcılar için `Int32` yerine `IntPtr` kullanan yanlış platform çağrıları veya COM bildirimleri.  
  
- `IntPtr` öğesini `Int32`'e yayınlayan kod.  
  
 64 bit CLR'de çalışacak 32 bit lik bir uygulamayı nasıl işaretedin hakkında daha fazla bilgi [için](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10))bkz.  
  
## <a name="general-64-bit-programming-information"></a>Genel 64-Bit Programlama Bilgileri  
 64 bit programlama hakkında genel bilgi için, aşağıdaki belgelere bakın:  
  
- Windows SDK belgelerinde, [64 bit Windows için Programlama Kılavuzu'na](/windows/win32/winprog64/programming-guide-for-64-bit-windows)bakın.  
  
- 64 bit uygulamalar oluşturmak için Visual Studio desteği hakkında daha fazla bilgi için [Visual Studio IDE 64-Bit Desteği'ne](/visualstudio/ide/visual-studio-ide-64-bit-support)bakın.  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>64-Bit Uygulamalar Oluşturmak için Derleme Desteği  
 Varsayılan olarak, 32 bitlik veya 64 bitlik bir bilgisayarda uygulama oluşturmak için .NET Framework'ü kullandığınızda, uygulama 64 bitlik bir bilgisayarda yerel uygulama olarak (yani WOW64 altında olmadan) çalışır. Aşağıdaki tablo, yerel olarak, WOW64 altında veya her iki şekilde de çalışacak olan 64 bitlik uygulamalar oluşturmak için Visual Studio'nun nasıl kullanıldığını açıklayan belgeleri listeler.  
  
|Derleyici|Derleyici seçeneği|  
|--------------|---------------------|  
|Visual Basic|[-platform (Visual Basic)](../visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[-platform (C# Derleyici Seçenekleri)](../csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|**/clr:safe**kullanarak platform-agnostik, Microsoft ara dil (MSIL) uygulamaları oluşturabilirsiniz. Daha fazla bilgi için bkz: [-clr (Ortak Dil Çalışma Zamanı Derlemesi).](/cpp/build/reference/clr-common-language-runtime-compilation)<br /><br /> Visual C++, 64 bitlik her bir işletim sistemi için ayrı bir derleyici içerir. 64 bit Windows işletim sisteminde çalışan yerel uygulamalar oluşturmak için Visual C++'ın nasıl kullanılacağı hakkında daha fazla bilgi için [64 bit Programlama'ya](/cpp/build/configuring-programs-for-64-bit-visual-cpp)bakın.|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Bir .exe Dosyası veya .dll Dosyasının Durumunu Belirleme  
 Bir .exe dosyasının veya .dll dosyasının yalnızca belirli bir platformda mı yoksa WOW64 altında mı çalıştırAcağını belirlemek [için, corflags.exe 'yi (CorFlags Dönüşüm Aracı)](./tools/corflags-exe-corflags-conversion-tool.md) seçeneği olmadan kullanın. Bir .exe dosyasının veya .dll dosyasının platform durumunu değiştirmek için aynı zamanda CorFlags.exe'yi de kullanabilirsiniz. Bir Visual Studio derlemesinin CLR başlığının ana çalışma zamanı sürümü numarası 2 olarak, alt çalışma zamanı sürümü numarası ise 5 olarak ayarlanır. Alt çalışma zamanı sürümü 0 olarak ayarlanan uygulamalar eski uygulamalar olarak işlenir ve her zaman WOW64 altında yürütülür.  
  
 Bir .exe veya .dll dosyasını, belirli bir platformda mı yoksa WOW4 altında mı çalışmak için tasarlandığını görmek üzere program aracılığıyla sorgulamak amacıyla <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> yöntemini kullanın.
