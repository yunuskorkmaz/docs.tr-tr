---
title: Bir WAV dosyası oynatmak için platform çağırma kullanma-C# Programlama Kılavuzu
description: Bu C# kod örneği, Windows işletim sisteminde bir WAV ses dosyası oynatmak için platform çağırma hizmetleri 'ni nasıl kullanacağınızı göstermektedir.
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6f507fa348bf1ea1b3fc5c3a868a6fbab7f8ec56
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558361"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>Bir WAV dosyası oynatmak için platform çağırma kullanma (C# Programlama Kılavuzu)

Aşağıdaki C# kod örneği, Windows işletim sisteminde bir WAV ses dosyası oynatmak için platform çağırma hizmetleri 'ni nasıl kullanacağınızı göstermektedir.

## <a name="example"></a>Örnek

Bu örnek kod, <xref:System.Runtime.InteropServices.DllImportAttribute> `winmm.dll` `PlaySound` yöntemi giriş noktasını olarak içeri aktarmak için kullanır `Form1 PlaySound()` . Örnekte, bir düğme içeren basit bir Windows formu vardır. Düğmeye tıkladığınızda, <xref:System.Windows.Forms.OpenFileDialog> oynatmak üzere bir dosya açabilmek için standart bir Windows iletişim kutusu açılır. Bir dalga dosyası seçildiğinde, `PlaySound()` *winmm.dll* kitaplığının yöntemi kullanılarak yürütülür. Bu yöntem hakkında daha fazla bilgi için bkz. [PlaySound Işlevini Waveform ses dosyalarıyla kullanma](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). . Wav uzantılı bir dosyaya gözatıp seçin ve ardından **Aç** ' a tıklayarak Wave dosyasını platform Invoke kullanarak yürütün. Bir metin kutusu seçili dosyanın tam yolunu gösterir.

**Dosyaları Aç** iletişim kutusu, filtre ayarları aracılığıyla yalnızca. wav uzantılı dosyaları gösterecek şekilde filtrelenmiştir:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Kod derleme

1. Visual Studio 'da yeni bir C# Windows Forms uygulama projesi oluşturun ve **WinSound**olarak adlandırın.

2. Yukarıdaki kodu kopyalayın ve *Form1.cs* dosyasının içeriğinin üzerine yapıştırın.

3. Aşağıdaki kodu kopyalayın ve *Form1.Designer.cs* dosyasına, `InitializeComponent()` varsa, varolan herhangi bir koddan sonra yapıştırın.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Kodu derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte Çalışabilirliğe Genel Bakış](interoperability-overview.md)
- [Platform çağırma ' ye daha yakından bakış](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma ile Veri Sıralama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
