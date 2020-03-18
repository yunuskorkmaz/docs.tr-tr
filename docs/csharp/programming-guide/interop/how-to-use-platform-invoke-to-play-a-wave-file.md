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
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="fa976-102">WAV dosyasını oynatmak için platform çağırma nasıl kullanılır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fa976-102">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="fa976-103">Aşağıdaki C# kodu örneği, Windows işletim sisteminde bir WAV ses dosyası çalmak için platform çağırma hizmetlerinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fa976-103">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="fa976-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa976-104">Example</span></span>

<span data-ttu-id="fa976-105">Bu örnek <xref:System.Runtime.InteropServices.DllImportAttribute> kod `winmm.dll`'ın `PlaySound` yöntem giriş `Form1 PlaySound()`noktasını ' olarak almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa976-105">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="fa976-106">Örnekte düğmeli basit bir Windows Formu vardır.</span><span class="sxs-lookup"><span data-stu-id="fa976-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="fa976-107">Düğmeyi tıklattığınızda, <xref:System.Windows.Forms.OpenFileDialog> oynatılacağı bir dosyayı açabilmeniz için standart bir windows iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="fa976-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="fa976-108">Bir dalga dosyası seçildiğinde, `PlaySound()` *winmm.dll* kitaplığı yöntemi kullanılarak oynanır.</span><span class="sxs-lookup"><span data-stu-id="fa976-108">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="fa976-109">Bu yöntem hakkında daha fazla bilgi için [Waveform-Audio Files ile PlaySound işlevini kullanma](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="fa976-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="fa976-110">.wav uzantılı bir dosyaya göz atın ve seçin ve platform çağırmayı kullanarak dalga dosyasını oynatmak için **Aç'ı** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fa976-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="fa976-111">Metin kutusu seçilen dosyanın tam yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa976-111">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="fa976-112">**Dosyaları Aç** iletişim kutusu, yalnızca .wav uzantısı olan dosyaları filtre ayarları üzerinden göstermek için filtrelenir:</span><span class="sxs-lookup"><span data-stu-id="fa976-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="fa976-113">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="fa976-113">Compiling the code</span></span>

1. <span data-ttu-id="fa976-114">Visual Studio'da yeni bir C# Windows Forms Uygulama projesi oluşturun ve **adını WinSound**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="fa976-114">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="fa976-115">Yukarıdaki kodu kopyalayın ve *Form1.cs* dosyanın içeriğine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa976-115">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="fa976-116">Aşağıdaki kodu kopyalayın ve varolan *Form1.Designer.cs* herhangi bir `InitializeComponent()` koddan sonra yöntemde Form1.Designer.cs dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa976-116">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="fa976-117">Kodu derle ve çalıştır.</span><span class="sxs-lookup"><span data-stu-id="fa976-117">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa976-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa976-118">See also</span></span>

- [<span data-ttu-id="fa976-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fa976-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fa976-120">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa976-120">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="fa976-121">Platform Invoke'a Daha Yakından Bakış</span><span class="sxs-lookup"><span data-stu-id="fa976-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="fa976-122">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="fa976-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
