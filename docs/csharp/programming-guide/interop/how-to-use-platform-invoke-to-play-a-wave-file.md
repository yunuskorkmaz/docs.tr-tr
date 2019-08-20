---
title: 'Nasıl yapılır: Bir Wave dosyası C# programlama kılavuzunu oynatmak Için platform çağırma kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: cf8415b2d501ae2394fa76170eb232da33c3e308
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589104"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Nasıl yapılır: Bir Wave dosyasını oynatmak için platform çağırma kullanma (C# Programlama Kılavuzu)
Aşağıdaki C# kod örneği, Windows işletim sisteminde bir Wave ses dosyası oynatmak için platform çağırma hizmetleri 'ni nasıl kullanacağınızı göstermektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnek kod, `DllImport` `PlaySound` yöntemi giriş `winmm.dll`noktasını olarak `Form1 PlaySound()`içeri aktarmak için kullanır. Örnekte, bir düğme içeren basit bir Windows formu vardır. Düğmeye tıkladığınızda, oynatmak üzere bir dosya <xref:System.Windows.Forms.OpenFileDialog> açabilmek için standart bir Windows iletişim kutusu açılır. Bir dalga dosyası seçildiğinde, `PlaySound()` `winmm.dll` kitaplığın yöntemi kullanılarak oynatılır. Bu yöntem hakkında daha fazla bilgi için bkz. [PlaySound Işlevini Waveform ses dosyalarıyla kullanma](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). . Wav uzantılı bir dosyaya gözatıp seçin ve ardından **Aç** ' a tıklayarak Wave dosyasını platform Invoke kullanarak yürütün. Bir metin kutusu seçili dosyanın tam yolunu gösterir.  
  
 **Dosyaları Aç** iletişim kutusu, filtre ayarları aracılığıyla yalnızca. wav uzantılı dosyaları gösterecek şekilde filtrelenmiştir:  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
1. Visual Studio 'da C# yeni bir Windows uygulaması projesi oluşturun ve bunu **WinSound**olarak adlandırın.  
  
2. Yukarıdaki kodu kopyalayın ve `Form1.cs` dosyanın içeriğini yapıştırın.  
  
3. Aşağıdaki kodu kopyalayın ve `Form1.Designer.cs` dosyasına `InitializeComponent()` , varsa, varolan herhangi bir koddan sonra yapıştırın.  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. Kodu derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte Çalışabilirliğe Genel Bakış](./interoperability-overview.md)
- [Platform çağırma ' ye daha yakından bakış](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma ile Veri Hazırlama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
