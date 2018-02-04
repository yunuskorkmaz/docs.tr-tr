---
title: "Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 10c2490255565de872396a0155bb588f9d696b24
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="c2fda-102">Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2fda-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="c2fda-103">Aşağıdaki C# kod örneğinde nasıl platform kullanılacağını anlatan Windows işletim sisteminde ses wave dosyasını oynatmak için hizmetlerini çağırma.</span><span class="sxs-lookup"><span data-stu-id="c2fda-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2fda-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2fda-104">Example</span></span>  
 <span data-ttu-id="c2fda-105">Bu kod örneği kullanan `DllImport` almak için `winmm.dll`'s `PlaySound` yöntemi giriş noktası olarak `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="c2fda-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="c2fda-106">Örnek basit bir Windows formunda bir düğme vardır.</span><span class="sxs-lookup"><span data-stu-id="c2fda-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="c2fda-107">Düğmesine tıkladığınızda açılır standart windows <xref:System.Windows.Forms.OpenFileDialog> iletişim kutusunu yürütmek için bir dosyayı açın.</span><span class="sxs-lookup"><span data-stu-id="c2fda-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="c2fda-108">Wave dosyasını seçildiğinde kullanarak çalınır `PlaySound()` WINMM yöntemi. DLL derleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2fda-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="c2fda-109">Winmm.dll'ın hakkında daha fazla bilgi için `PlaySound` yöntemi, bkz: [dalga biçiminin ses dosyaları ile PlaySound işlevini kullanarak](https://msdn.microsoft.com/library/aa910379.aspx).</span><span class="sxs-lookup"><span data-stu-id="c2fda-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx).</span></span> <span data-ttu-id="c2fda-110">Gözat ve .wav uzantılı bir dosya seçin ve ardından **açık** oynatmak için platform kullanarak wave dosyasını çağırır.</span><span class="sxs-lookup"><span data-stu-id="c2fda-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="c2fda-111">Bir metin kutusu seçili dosyasının tam yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2fda-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="c2fda-112">**Açık dosyalar** iletişim kutusu filtre filtre ayarları aracılığıyla .wav uzantısı olan dosyaları göstermek için:</span><span class="sxs-lookup"><span data-stu-id="c2fda-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2fda-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c2fda-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="c2fda-114">Kodu derlemek için</span><span class="sxs-lookup"><span data-stu-id="c2fda-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="c2fda-115">Visual Studio'da yeni bir C# Windows uygulama projesi oluşturun ve adlandırın **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="c2fda-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="c2fda-116">Yukarıdaki kodu kopyalayabilir ve üzerinde içeriğini yapıştırın `Form1.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="c2fda-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="c2fda-117">Aşağıdaki kodu kopyalayın ve yapıştırın `Form1.Designer.cs` dosyasında `InitializeComponent()` tüm var olan koddan sonra yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2fda-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="c2fda-118">Derleme ve kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c2fda-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c2fda-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c2fda-119">.NET Framework Security</span></span>  
 <span data-ttu-id="c2fda-120">Daha fazla bilgi için bkz: [.NET Framework Güvenliği](https://technet.microsoft.com/en-us/security/).</span><span class="sxs-lookup"><span data-stu-id="c2fda-120">For more information, see [.NET Framework Security](https://technet.microsoft.com/en-us/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2fda-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2fda-121">See Also</span></span>  
 [<span data-ttu-id="c2fda-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c2fda-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c2fda-123">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c2fda-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="c2fda-124">Yakından Platform çağırma</span><span class="sxs-lookup"><span data-stu-id="c2fda-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [<span data-ttu-id="c2fda-125">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c2fda-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
