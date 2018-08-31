---
title: 'Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6b20877e54722b338c9905445a39c42350c7f7d7
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253144"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)
Aşağıdaki C# kod örneği platform kullanılması gösterilmektedir Windows işletim sisteminde ses wave dosyasını oynatmak için hizmetlerini çağırma.  
  
## <a name="example"></a>Örnek  
 Bu kod örneği kullanan `DllImport` içeri aktarmak için `winmm.dll`'s `PlaySound` yöntemi giriş noktası olarak `Form1 PlaySound()`. Örneğin, bir düğme içeren basit bir Windows Form vardır. Düğmeye tıklandığında, standart windows açılır <xref:System.Windows.Forms.OpenFileDialog> iletişim kutusunu yürütmek için bir dosyayı açabilirsiniz. Wave dosyasını seçildiğinde kullanarak çalınır `PlaySound()` yöntemi `winmm.dll` kitaplığı. Bu yöntem hakkında daha fazla bilgi için bkz: [PlaySound işlevi kullanılarak oluşturulan dalga biçiminin ses dosyaları ile](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Gözat ve .wav uzantılı bir dosya seçin ve ardından **açık** platformu kullanarak wave dosyasını oynatmak için çağırır. Bir metin kutusu seçili dosyanın tam yolunu gösterir.  
  
 **Açık dosyalar** iletişim kutusu filtre ayarları aracılığıyla .wav uzantısına sahip dosyaları gösterecek şekilde filtrelenmiştir:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
### <a name="to-compile-the-code"></a>Kodu derlemek için  
  
1.  Visual Studio'da yeni bir C# Windows uygulaması projesi oluşturun ve adlandırın **WinSound**.  
  
2.  Yukarıdaki kodu kopyalayabilir ve üzerinde içeriğini yapıştırın `Form1.cs` dosya.  
  
3.  Aşağıdaki kodu kopyalayın ve yapıştırın `Form1.Designer.cs` dosyasındaki `InitializeComponent()` yöntemi, mevcut kodlar sonra.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Derleyin ve kod çalıştırın.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Daha fazla bilgi için [.NET içinde güvenlik](../../../standard/security/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Birlikte Çalışabilirliğe Genel Bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Yakından Platform çağırma](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [Platform Çağırma ile Veri Hazırlama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
