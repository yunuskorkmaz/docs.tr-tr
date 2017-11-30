---
title: "XmlSerializer siparişle özel seri hale getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 16032a7df2df374d6201f8da18d563deceeeb5bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="66443-102">XmlSerializer siparişle özel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="66443-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="66443-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="66443-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="66443-104">Bu örnek XML serileştirme için seri duruma getirilmiş ve seri durumdan çıkarılmış öğelerin sırasını denetleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="66443-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="66443-105">Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.</span><span class="sxs-lookup"><span data-stu-id="66443-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="66443-106">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="66443-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="66443-107">Komut istemi açın ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="66443-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="66443-108">Tür **msbuild CustomOrder.sln** komut satırında.</span><span class="sxs-lookup"><span data-stu-id="66443-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="66443-109">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="66443-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="66443-110">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="66443-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="66443-111">Visual Studio'da dosyayı açmak CustomOrder.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="66443-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="66443-112">İçinde **yapı** menüsünde, select **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="66443-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="66443-113">Uygulama örneği varsayılan \bin veya \bin\debug'dır alt üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66443-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66443-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66443-114">See Also</span></span>  
 [<span data-ttu-id="66443-115">Temel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="66443-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="66443-116">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="66443-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="66443-117">XML serileştirme özniteliklerini kullanarak denetleme</span><span class="sxs-lookup"><span data-stu-id="66443-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="66443-118">Giriş XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="66443-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="66443-119">Seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="66443-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="66443-120">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="66443-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
