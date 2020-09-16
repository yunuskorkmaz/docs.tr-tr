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
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="398fc-103">Bir WAV dosyası oynatmak için platform çağırma kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="398fc-103">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="398fc-104">Aşağıdaki C# kod örneği, Windows işletim sisteminde bir WAV ses dosyası oynatmak için platform çağırma hizmetleri 'ni nasıl kullanacağınızı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="398fc-104">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="398fc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="398fc-105">Example</span></span>

<span data-ttu-id="398fc-106">Bu örnek kod, <xref:System.Runtime.InteropServices.DllImportAttribute> `winmm.dll` `PlaySound` yöntemi giriş noktasını olarak içeri aktarmak için kullanır `Form1 PlaySound()` .</span><span class="sxs-lookup"><span data-stu-id="398fc-106">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="398fc-107">Örnekte, bir düğme içeren basit bir Windows formu vardır.</span><span class="sxs-lookup"><span data-stu-id="398fc-107">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="398fc-108">Düğmeye tıkladığınızda, <xref:System.Windows.Forms.OpenFileDialog> oynatmak üzere bir dosya açabilmek için standart bir Windows iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="398fc-108">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="398fc-109">Bir dalga dosyası seçildiğinde, `PlaySound()` *winmm.dll* kitaplığının yöntemi kullanılarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="398fc-109">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="398fc-110">Bu yöntem hakkında daha fazla bilgi için bkz. [PlaySound Işlevini Waveform ses dosyalarıyla kullanma](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="398fc-110">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="398fc-111">. Wav uzantılı bir dosyaya gözatıp seçin ve ardından **Aç** ' a tıklayarak Wave dosyasını platform Invoke kullanarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="398fc-111">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="398fc-112">Bir metin kutusu seçili dosyanın tam yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="398fc-112">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="398fc-113">**Dosyaları Aç** iletişim kutusu, filtre ayarları aracılığıyla yalnızca. wav uzantılı dosyaları gösterecek şekilde filtrelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="398fc-113">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="398fc-114">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="398fc-114">Compiling the code</span></span>

1. <span data-ttu-id="398fc-115">Visual Studio 'da yeni bir C# Windows Forms uygulama projesi oluşturun ve **WinSound**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="398fc-115">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="398fc-116">Yukarıdaki kodu kopyalayın ve *Form1.cs* dosyasının içeriğinin üzerine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="398fc-116">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="398fc-117">Aşağıdaki kodu kopyalayın ve *Form1.Designer.cs* dosyasına, `InitializeComponent()` varsa, varolan herhangi bir koddan sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="398fc-117">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="398fc-118">Kodu derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="398fc-118">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="398fc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="398fc-119">See also</span></span>

- [<span data-ttu-id="398fc-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="398fc-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="398fc-121">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="398fc-121">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="398fc-122">Platform çağırma ' ye daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="398fc-122">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="398fc-123">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="398fc-123">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
