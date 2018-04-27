---
title: Sürüm dayanıklı seri hale getirme teknolojisi örneği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ddeea50bafe250addad33a024c563258ede357c4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="50219-102">Sürüm dayanıklı seri hale getirme teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="50219-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="50219-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="50219-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="50219-104">Bu örnek .NET seri hale getirme sürüm dayanıklılık özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50219-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="50219-105">Örnek farklı sürümleri kullanan uygulamalar oluşturur bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> hale getirmek ve veri serisini kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="50219-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="50219-106">Farklı bir türe sürümleri varlığını rağmen uygulamalar sorunsuz iletişim.</span><span class="sxs-lookup"><span data-stu-id="50219-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="50219-107">Daha fazla bilgi için bkz: [sürüm dayanıklı serileştirme](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="50219-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="50219-108">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="50219-108">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="50219-109">Bir komut istemi penceresi açın ve örnek için dile özgü alt (altında uygulama V1 veya V2 uygulama) birine gidin.</span><span class="sxs-lookup"><span data-stu-id="50219-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2.  <span data-ttu-id="50219-110">Tür **msbuild.exe \<ver > application.sln** komut satırında (burada \<ver > v1 veya v2).</span><span class="sxs-lookup"><span data-stu-id="50219-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="50219-111">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="50219-111">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="50219-112">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="50219-112">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="50219-113">Önceki adımda seçtiğiniz dizininin V1 uygulama alt gidin.</span><span class="sxs-lookup"><span data-stu-id="50219-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3.  <span data-ttu-id="50219-114">Visual Studio'da dosyayı açmak V1 Application.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="50219-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4.  <span data-ttu-id="50219-115">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="50219-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="50219-116">V2 uygulama alt dizinine gidin ve V2 uygulama oluşturmak için yukarıdaki iki adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="50219-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="50219-117">Uygulamaları varsayılan \bin veya \bin\debug'dır dizinlerde kendi ilgili proje dizinlerin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="50219-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="50219-118">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="50219-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="50219-119">Komut İstemi penceresinde örnek uygulamalar yapılandırıldığında seçtiğiniz dile özgü alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="50219-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2.  <span data-ttu-id="50219-120">Tür **runme.cmd** iki uygulamanın aynı anda çalıştırmak için komut satırında.</span><span class="sxs-lookup"><span data-stu-id="50219-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="50219-121">Alternatif olarak, sıralı olarak çalıştırın ve yeni yürütülebilir dosyaları içeren dizinler gidin.</span><span class="sxs-lookup"><span data-stu-id="50219-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50219-122">Örnek konsol uygulamaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50219-122">The sample builds console applications.</span></span> <span data-ttu-id="50219-123">Başlatma ve bunları çıktılarını görüntülemek için komut istemi penceresinde Çalıştır gerekir.</span><span class="sxs-lookup"><span data-stu-id="50219-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50219-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50219-124">See Also</span></span>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.IO.FileStream>
