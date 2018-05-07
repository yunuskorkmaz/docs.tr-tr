---
title: 'Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: f2234acb9d4eb3b436f3ccdad19525a5ebf26f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)
Aşağıdaki C# kod örneğinde nasıl platform kullanılacağını anlatan Windows işletim sisteminde ses wave dosyasını oynatmak için hizmetlerini çağırma.  
  
## <a name="example"></a>Örnek  
 Bu kod örneği kullanan `DllImport` almak için `winmm.dll`'s `PlaySound` yöntemi giriş noktası olarak `Form1 PlaySound()`. Örnek basit bir Windows formunda bir düğme vardır. Düğmesine tıkladığınızda açılır standart windows <xref:System.Windows.Forms.OpenFileDialog> iletişim kutusunu yürütmek için bir dosyayı açın. Wave dosyasını seçildiğinde kullanarak çalınır `PlaySound()` WINMM yöntemi. DLL derleme yöntemi. Winmm.dll'ın hakkında daha fazla bilgi için `PlaySound` yöntemi, bkz: [dalga biçiminin ses dosyaları ile PlaySound işlevini kullanarak](https://msdn.microsoft.com/library/aa910379.aspx). Gözat ve .wav uzantılı bir dosya seçin ve ardından **açık** oynatmak için platform kullanarak wave dosyasını çağırır. Bir metin kutusu seçili dosyasının tam yolunu gösterir.  
  
 **Açık dosyalar** iletişim kutusu filtre filtre ayarları aracılığıyla .wav uzantısı olan dosyaları göstermek için:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
### <a name="to-compile-the-code"></a>Kodu derlemek için  
  
1.  Visual Studio'da yeni bir C# Windows uygulama projesi oluşturun ve adlandırın **WinSound**.  
  
2.  Yukarıdaki kodu kopyalayabilir ve üzerinde içeriğini yapıştırın `Form1.cs` dosya.  
  
3.  Aşağıdaki kodu kopyalayın ve yapıştırın `Form1.Designer.cs` dosyasında `InitializeComponent()` tüm var olan koddan sonra yöntemi.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Derleme ve kodu çalıştırın.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Daha fazla bilgi için bkz: [.NET Framework Güvenliği](https://technet.microsoft.com/en-us/security/).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Birlikte Çalışabilirliğe Genel Bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Yakından Platform çağırma](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [Platform Çağırma ile Veri Hazırlama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
