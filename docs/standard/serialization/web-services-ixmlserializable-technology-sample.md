---
title: Web Hizmetleri IXmlSerializable teknolojisi örneği
ms.date: 03/30/2017
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
ms.openlocfilehash: eb117f720e7541ac6460b5adfd0eecc7901f4fdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582720"
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="a2a71-102">Web Hizmetleri IXmlSerializable teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="a2a71-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="a2a71-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="a2a71-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="a2a71-104">Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Xml.Serialization.IXmlSerializable> ASP.NET Web Hizmetleri içinde özel türleri serileştirmek denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="a2a71-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a2a71-105">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a2a71-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="a2a71-106">Açık [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] seçip **yeni Web sitesi** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a2a71-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="a2a71-107">Sol bölmesinde **yeni Web sitesi** iletişim kutusunda, istediğiniz programlama dili seçin ve ardından sağ bölmeden **ASP.NET Web hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="a2a71-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="a2a71-108">Tür **IXmlSerializable** adı yeni Web hizmeti olarak.</span><span class="sxs-lookup"><span data-stu-id="a2a71-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="a2a71-109">Çözüm Gezgini penceresinde QuoteService.asmx'e değiştirin ve select için simgesini **silmek**; QuoteService.asmx'e değiştirin arkasındaki koda dosyası için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="a2a71-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="a2a71-110">Dizin ve select projeye sağ **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a2a71-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="a2a71-111">İletişim kutusunda, dile özgü dizininin hizmeti alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="a2a71-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="a2a71-112">QuoteService.asmx'e değiştirin seçin, sonra QuoteService.asmx'e değiştirin arkasındaki koda dosyası için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="a2a71-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="a2a71-113">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve yukarıdaki 3 adımda oluşturduğunuz IXmlSerializable dizinini içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="a2a71-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="a2a71-114">IXmlSerializable directory simgesine sağ tıklayın ve seçin **paylaşım ve güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="a2a71-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="a2a71-115">Web Paylaşımı sekmesini seçin **bu klasörü paylaş**ve IXmlSerializable adı dahil olmak üzere varsayılan ayarlarını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="a2a71-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="a2a71-116">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a2a71-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="a2a71-117">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a2a71-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="a2a71-118">Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.</span><span class="sxs-lookup"><span data-stu-id="a2a71-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="a2a71-119">Tür **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="a2a71-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a71-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2a71-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
