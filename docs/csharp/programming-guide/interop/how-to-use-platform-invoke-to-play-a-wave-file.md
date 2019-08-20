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
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="a89c7-102">Nasıl yapılır: Bir Wave dosyasını oynatmak için platform çağırma kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a89c7-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="a89c7-103">Aşağıdaki C# kod örneği, Windows işletim sisteminde bir Wave ses dosyası oynatmak için platform çağırma hizmetleri 'ni nasıl kullanacağınızı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a89c7-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a89c7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a89c7-104">Example</span></span>  
 <span data-ttu-id="a89c7-105">Bu örnek kod, `DllImport` `PlaySound` yöntemi giriş `winmm.dll`noktasını olarak `Form1 PlaySound()`içeri aktarmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a89c7-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="a89c7-106">Örnekte, bir düğme içeren basit bir Windows formu vardır.</span><span class="sxs-lookup"><span data-stu-id="a89c7-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="a89c7-107">Düğmeye tıkladığınızda, oynatmak üzere bir dosya <xref:System.Windows.Forms.OpenFileDialog> açabilmek için standart bir Windows iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="a89c7-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="a89c7-108">Bir dalga dosyası seçildiğinde, `PlaySound()` `winmm.dll` kitaplığın yöntemi kullanılarak oynatılır.</span><span class="sxs-lookup"><span data-stu-id="a89c7-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="a89c7-109">Bu yöntem hakkında daha fazla bilgi için bkz. [PlaySound Işlevini Waveform ses dosyalarıyla kullanma](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="a89c7-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="a89c7-110">. Wav uzantılı bir dosyaya gözatıp seçin ve ardından **Aç** ' a tıklayarak Wave dosyasını platform Invoke kullanarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="a89c7-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="a89c7-111">Bir metin kutusu seçili dosyanın tam yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a89c7-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="a89c7-112">**Dosyaları Aç** iletişim kutusu, filtre ayarları aracılığıyla yalnızca. wav uzantılı dosyaları gösterecek şekilde filtrelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="a89c7-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a89c7-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a89c7-113">Compiling the Code</span></span>  
  
1. <span data-ttu-id="a89c7-114">Visual Studio 'da C# yeni bir Windows uygulaması projesi oluşturun ve bunu **WinSound**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a89c7-114">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2. <span data-ttu-id="a89c7-115">Yukarıdaki kodu kopyalayın ve `Form1.cs` dosyanın içeriğini yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a89c7-115">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3. <span data-ttu-id="a89c7-116">Aşağıdaki kodu kopyalayın ve `Form1.Designer.cs` dosyasına `InitializeComponent()` , varsa, varolan herhangi bir koddan sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a89c7-116">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. <span data-ttu-id="a89c7-117">Kodu derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a89c7-117">Compile and run the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89c7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a89c7-118">See also</span></span>

- [<span data-ttu-id="a89c7-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a89c7-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a89c7-120">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a89c7-120">Interoperability Overview</span></span>](./interoperability-overview.md)
- [<span data-ttu-id="a89c7-121">Platform çağırma ' ye daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="a89c7-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="a89c7-122">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a89c7-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
