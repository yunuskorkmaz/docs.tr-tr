---
title: XmlSerializer ile özel serileştirme düzeni
ms.date: 03/30/2017
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
ms.openlocfilehash: 1dc9a73b45d8e62902ec8c6b7d810154a8a92566
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071953"
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="31a7f-102">XmlSerializer ile özel serileştirme düzeni</span><span class="sxs-lookup"><span data-stu-id="31a7f-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="31a7f-103">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="31a7f-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="31a7f-104">Bu örnek serileştirilmiş ve seri durumdan çıkarılmış öğelerin sırasını XML Serileştirmenin denetlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="31a7f-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="31a7f-105">Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.</span><span class="sxs-lookup"><span data-stu-id="31a7f-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="31a7f-106">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="31a7f-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="31a7f-107">Komut istemi açın ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="31a7f-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="31a7f-108">Tür **msbuild CustomOrder.sln** komut satırına.</span><span class="sxs-lookup"><span data-stu-id="31a7f-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="31a7f-109">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="31a7f-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="31a7f-110">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="31a7f-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="31a7f-111">Visual Studio'da dosyayı açmak CustomOrder.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="31a7f-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="31a7f-112">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="31a7f-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="31a7f-113">Uygulama örneği varsayılan \bin veya \bin\debug'dır alt üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="31a7f-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a7f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31a7f-114">See also</span></span>

- [<span data-ttu-id="31a7f-115">Temel Serileştirme</span><span class="sxs-lookup"><span data-stu-id="31a7f-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
- [<span data-ttu-id="31a7f-116">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="31a7f-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
- [<span data-ttu-id="31a7f-117">Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="31a7f-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [<span data-ttu-id="31a7f-118">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="31a7f-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="31a7f-119">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="31a7f-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
- [<span data-ttu-id="31a7f-120">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="31a7f-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
