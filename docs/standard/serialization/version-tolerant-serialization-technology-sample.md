---
title: Sürüme Dayanıklı Serileştirme Teknolojisi Örneği
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960773"
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="3d090-102">Sürüme Dayanıklı Serileştirme Teknolojisi Örneği</span><span class="sxs-lookup"><span data-stu-id="3d090-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="3d090-103">Örnek indir</span><span class="sxs-lookup"><span data-stu-id="3d090-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="3d090-104">Bu örnek, .NET serileştirme 'in sürüm toleransı özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d090-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="3d090-105">Örnek farklı sürümleri kullanan uygulamalar oluşturur bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> hale getirmek ve veri serisini kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="3d090-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="3d090-106">Farklı bir türe sürümleri varlığını rağmen uygulamalar sorunsuz iletişim.</span><span class="sxs-lookup"><span data-stu-id="3d090-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="3d090-107">Daha fazla bilgi için bkz. [Sürüm dayanıklı serileştirme](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="3d090-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="3d090-108">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d090-108">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="3d090-109">Bir komut istemi penceresi açın ve örnek için dile özgü alt (altında uygulama V1 veya V2 uygulama) birine gidin.</span><span class="sxs-lookup"><span data-stu-id="3d090-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2. <span data-ttu-id="3d090-110">**MSBuild. exe \<ver> Application. sln** komutunu komut satırına (" \<ver> v1 veya v2) yazın.</span><span class="sxs-lookup"><span data-stu-id="3d090-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3d090-111">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d090-111">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="3d090-112">Dosya Gezgini 'ni açın ve örnek için dile özgü alt dizinlerden birine gidin.</span><span class="sxs-lookup"><span data-stu-id="3d090-112">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="3d090-113">Önceki adımda seçtiğiniz dizininin V1 uygulama alt gidin.</span><span class="sxs-lookup"><span data-stu-id="3d090-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3. <span data-ttu-id="3d090-114">Visual Studio'da dosyayı açmak V1 Application.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3d090-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4. <span data-ttu-id="3d090-115">**Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3d090-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="3d090-116">V2 uygulama alt dizinine gidin ve V2 uygulama oluşturmak için yukarıdaki iki adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="3d090-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="3d090-117">Uygulamaları varsayılan \bin veya \bin\debug'dır dizinlerde kendi ilgili proje dizinlerin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3d090-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="3d090-118">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3d090-118">To run the sample</span></span>  
  
1. <span data-ttu-id="3d090-119">Komut İstemi penceresinde örnek uygulamalar yapılandırıldığında seçtiğiniz dile özgü alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="3d090-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2. <span data-ttu-id="3d090-120">Her iki uygulamayı aynı anda çalıştırmak için komut satırına **runme. cmd** yazın.</span><span class="sxs-lookup"><span data-stu-id="3d090-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="3d090-121">Alternatif olarak, sıralı olarak çalıştırın ve yeni yürütülebilir dosyaları içeren dizinler gidin.</span><span class="sxs-lookup"><span data-stu-id="3d090-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d090-122">Örnek konsol uygulamaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d090-122">The sample builds console applications.</span></span> <span data-ttu-id="3d090-123">Başlatma ve bunları çıktılarını görüntülemek için komut istemi penceresinde Çalıştır gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d090-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d090-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d090-124">See also</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
