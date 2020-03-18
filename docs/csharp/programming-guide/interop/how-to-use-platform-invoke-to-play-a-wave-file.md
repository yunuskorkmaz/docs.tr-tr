---
title: WAV dosyasını oynatmak için platform çağırma nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 3ea90f0739ad45c31e4f25836c9de8e708dff2cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700828"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>WAV dosyasını oynatmak için platform çağırma nasıl kullanılır (C# Programlama Kılavuzu)

Aşağıdaki C# kodu örneği, Windows işletim sisteminde bir WAV ses dosyası çalmak için platform çağırma hizmetlerinin nasıl kullanılacağını göstermektedir.

## <a name="example"></a>Örnek

Bu örnek <xref:System.Runtime.InteropServices.DllImportAttribute> kod `winmm.dll`'ın `PlaySound` yöntem giriş `Form1 PlaySound()`noktasını ' olarak almak için kullanır. Örnekte düğmeli basit bir Windows Formu vardır. Düğmeyi tıklattığınızda, <xref:System.Windows.Forms.OpenFileDialog> oynatılacağı bir dosyayı açabilmeniz için standart bir windows iletişim kutusu açılır. Bir dalga dosyası seçildiğinde, `PlaySound()` *winmm.dll* kitaplığı yöntemi kullanılarak oynanır. Bu yöntem hakkında daha fazla bilgi için [Waveform-Audio Files ile PlaySound işlevini kullanma](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files)konusuna bakın. .wav uzantılı bir dosyaya göz atın ve seçin ve platform çağırmayı kullanarak dalga dosyasını oynatmak için **Aç'ı** tıklatın. Metin kutusu seçilen dosyanın tam yolunu gösterir.

**Dosyaları Aç** iletişim kutusu, yalnızca .wav uzantısı olan dosyaları filtre ayarları üzerinden göstermek için filtrelenir:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Kod derleme

1. Visual Studio'da yeni bir C# Windows Forms Uygulama projesi oluşturun ve **adını WinSound**olarak adlandırın.

2. Yukarıdaki kodu kopyalayın ve *Form1.cs* dosyanın içeriğine yapıştırın.

3. Aşağıdaki kodu kopyalayın ve varolan *Form1.Designer.cs* herhangi bir `InitializeComponent()` koddan sonra yöntemde Form1.Designer.cs dosyasına yapıştırın.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Kodu derle ve çalıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte Çalışabilirliğe Genel Bakış](interoperability-overview.md)
- [Platform Invoke'a Daha Yakından Bakış](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Platform Çağırma ile Veri Sıralama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
