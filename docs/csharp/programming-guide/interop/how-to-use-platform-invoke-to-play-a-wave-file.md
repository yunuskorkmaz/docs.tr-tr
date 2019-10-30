---
title: 'Nasıl yapılır: bir Wave dosyasını oynatmak için platform çağırma kullanma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6c2313f7b600bc1670c944f6a93868c1bc4c7c16
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039321"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)

Aşağıdaki C# kod örneği, Windows işletim sisteminde bir Wave ses dosyası oynatmak için platform çağırma hizmetleri 'ni nasıl kullanacağınızı göstermektedir.

## <a name="example"></a>Örnek

Bu örnek kod, `winmm.dll``PlaySound` yöntem giriş noktasını `Form1 PlaySound()`olarak içeri aktarmak için <xref:System.Runtime.InteropServices.DllImportAttribute> kullanır. Örnekte, bir düğme içeren basit bir Windows formu vardır. Düğmeye tıkladığınızda yürütmek üzere bir dosyayı açabilmek için standart bir Windows <xref:System.Windows.Forms.OpenFileDialog> iletişim kutusu açılır. Bir dalga dosyası seçildiğinde, *winmm. dll* kitaplığının `PlaySound()` yöntemi kullanılarak oynatılır. Bu yöntem hakkında daha fazla bilgi için bkz. [PlaySound Işlevini Waveform ses dosyalarıyla kullanma](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). . Wav uzantılı bir dosyaya gözatıp seçin ve ardından **Aç** ' a tıklayarak Wave dosyasını platform Invoke kullanarak yürütün. Bir metin kutusu seçili dosyanın tam yolunu gösterir.

**Dosyaları Aç** iletişim kutusu, filtre ayarları aracılığıyla yalnızca. wav uzantılı dosyaları gösterecek şekilde filtrelenmiştir:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Kodu derleme

1. Visual Studio 'da C# yeni bir Windows Forms uygulama projesi oluşturun ve **WinSound**olarak adlandırın.

2. Yukarıdaki kodu kopyalayın ve *Form1.cs* dosyasının içeriğinin üzerine yapıştırın.

3. Aşağıdaki kodu kopyalayın ve mevcut koddan sonra `InitializeComponent()` yönteminde *Form1.Designer.cs* dosyasına yapıştırın.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Kodu derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte Çalışabilirliğe Genel Bakış](interoperability-overview.md)
- [Platform çağırma ' ye daha yakından bakış](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma ile Veri Hazırlama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
