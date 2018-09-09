---
title: Web Hizmetleri IXmlSerializable teknolojisi örneği
ms.date: 03/30/2017
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
ms.openlocfilehash: 343755c062fc13891d84131a5f7682e2e1466a5a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252798"
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="69595-102">Web Hizmetleri IXmlSerializable teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="69595-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="69595-103">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="69595-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="69595-104">Bu örnek nasıl kullanılacağını gösterir <xref:System.Xml.Serialization.IXmlSerializable> ASP.NET Web Hizmetleri özel türleri serileştirmek denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="69595-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="69595-105">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69595-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="69595-106">Açık [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] seçip **yeni Web sitesi** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="69595-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="69595-107">Sol bölmesinde **yeni Web sitesi** iletişim kutusunda, istediğiniz programlama dili seçin, sonra sağ bölmeden **ASP.NET Web hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="69595-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="69595-108">Tür **IXmlSerializable** olarak yeni bir Web hizmeti adı.</span><span class="sxs-lookup"><span data-stu-id="69595-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="69595-109">Çözüm Gezgini penceresinde QuoteService.asmx'e değiştirin ve seçin için simgesini sağ tıklatın **Sil**; QuoteService.asmx'e değiştirin arkasındaki koda dosyası için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="69595-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="69595-110">Dizin ve select projeyi sağ **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="69595-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="69595-111">İletişim kutusunda, dile özgü dizininin hizmeti alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="69595-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="69595-112">QuoteService.asmx'e değiştirin seçin, sonra QuoteService.asmx'e değiştirin arkasındaki koda dosyası için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="69595-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="69595-113">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve yukarıdaki 3 adımda oluşturduğunuz IXmlSerializable dizinini içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="69595-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="69595-114">IXmlSerializable dizini simgesini sağ tıklayıp **paylaşım ve güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="69595-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="69595-115">Web Paylaşımı sekmesini seçin **bu klasörü paylaş**, varsayılan ayarları IXmlSerializable adı da dahil olmak üzere, onaylayın.</span><span class="sxs-lookup"><span data-stu-id="69595-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="69595-116">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="69595-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="69595-117">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="69595-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="69595-118">Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.</span><span class="sxs-lookup"><span data-stu-id="69595-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="69595-119">Tür **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="69595-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69595-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69595-120">See also</span></span>

- <xref:System.Xml.Serialization.IXmlSerializable>  
- <xref:System.Xml.Serialization>  
- <xref:System.Xml.XmlConvert>  
- <xref:System.Xml.XmlQualifiedName>  
- <xref:System.Xml.XmlReader>  
- <xref:System.Xml.Schema.XmlSchema>  
- <xref:System.Xml.Schema.XmlSchemaSet>  
- <xref:System.Xml.XmlUrlResolver>  
- <xref:System.Xml.XmlWriter>
