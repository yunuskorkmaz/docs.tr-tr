---
title: "Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d037e17ef48ebfdd5cfd860efbacf195e7b6a76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="d71e1-102">Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d71e1-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="d71e1-103">Aşağıdaki C# kod örneğinde nasıl platform kullanılacağını anlatan Windows işletim sisteminde ses wave dosyasını oynatmak için hizmetlerini çağırma.</span><span class="sxs-lookup"><span data-stu-id="d71e1-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d71e1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d71e1-104">Example</span></span>  
 <span data-ttu-id="d71e1-105">Bu kod örneği kullanan `DllImport` almak için `winmm.dll`'s `PlaySound` yöntemi giriş noktası olarak `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="d71e1-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="d71e1-106">Örnek basit bir Windows formunda bir düğme vardır.</span><span class="sxs-lookup"><span data-stu-id="d71e1-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="d71e1-107">Düğmesine tıkladığınızda açılır standart windows <xref:System.Windows.Forms.OpenFileDialog> iletişim kutusunu yürütmek için bir dosyayı açın.</span><span class="sxs-lookup"><span data-stu-id="d71e1-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="d71e1-108">Wave dosyasını seçildiğinde kullanarak çalınır `PlaySound()` WINMM yöntemi. DLL derleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d71e1-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="d71e1-109">Winmm.dll'ın hakkında daha fazla bilgi için `PlaySound` yöntemi, bkz: [dalga biçiminin ses dosyaları ile PlaySound işlevini kullanarak](http://go.microsoft.com/fwlink/?LinkId=148553).</span><span class="sxs-lookup"><span data-stu-id="d71e1-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553).</span></span> <span data-ttu-id="d71e1-110">Gözat ve .wav uzantılı bir dosya seçin ve ardından **açık** oynatmak için platform kullanarak wave dosyasını çağırır.</span><span class="sxs-lookup"><span data-stu-id="d71e1-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="d71e1-111">Bir metin kutusu seçili dosyasının tam yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d71e1-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="d71e1-112">**Açık dosyalar** iletişim kutusu filtre filtre ayarları aracılığıyla .wav uzantısı olan dosyaları göstermek için:</span><span class="sxs-lookup"><span data-stu-id="d71e1-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d71e1-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d71e1-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="d71e1-114">Kodu derlemek için</span><span class="sxs-lookup"><span data-stu-id="d71e1-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="d71e1-115">Visual Studio'da yeni bir C# Windows uygulama projesi oluşturun ve adlandırın **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="d71e1-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="d71e1-116">Yukarıdaki kodu kopyalayabilir ve üzerinde içeriğini yapıştırın `Form1.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="d71e1-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="d71e1-117">Aşağıdaki kodu kopyalayın ve yapıştırın `Form1.Designer.cs` dosyasında `InitializeComponent()` tüm var olan koddan sonra yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d71e1-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="d71e1-118">Derleme ve kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d71e1-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d71e1-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d71e1-119">.NET Framework Security</span></span>  
 <span data-ttu-id="d71e1-120">Daha fazla bilgi için bkz: [.NET Framework Güvenliği](http://go.microsoft.com/fwlink/?LinkId=37122).</span><span class="sxs-lookup"><span data-stu-id="d71e1-120">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71e1-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d71e1-121">See Also</span></span>  
 [<span data-ttu-id="d71e1-122">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d71e1-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d71e1-123">Birlikte çalışabilirliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="d71e1-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="d71e1-124">Birlikte çalışabilirliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="d71e1-124">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="d71e1-125">Yakından Platform çağırma</span><span class="sxs-lookup"><span data-stu-id="d71e1-125">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="d71e1-126">Platform Çağırma ile veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="d71e1-126">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
