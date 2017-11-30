---
title: "Web Hizmetleri IXmlSerializable teknolojisi örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 72c7e9e1cbf47dd54726a16ddeb58a193d62dc31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="0fd7b-102">Web Hizmetleri IXmlSerializable teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="0fd7b-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="0fd7b-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="0fd7b-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="0fd7b-104">Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Xml.Serialization.IXmlSerializable> ASP.NET Web Hizmetleri içinde özel türleri serileştirmek denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="0fd7b-105">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0fd7b-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="0fd7b-106">Açık [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] seçip **yeni Web sitesi** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="0fd7b-107">Sol bölmesinde **yeni Web sitesi** iletişim kutusunda, istediğiniz programlama dili seçin ve ardından sağ bölmeden **ASP.NET Web hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="0fd7b-108">Tür **IXmlSerializable** adı yeni Web hizmeti olarak.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="0fd7b-109">Çözüm Gezgini penceresinde QuoteService.asmx'e değiştirin ve select için simgesini **silmek**; QuoteService.asmx'e değiştirin arkasındaki koda dosyası için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="0fd7b-110">Dizin ve select projeye sağ **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="0fd7b-111">İletişim kutusunda, dile özgü dizininin hizmeti alt dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="0fd7b-112">QuoteService.asmx'e değiştirin seçin, sonra QuoteService.asmx'e değiştirin arkasındaki koda dosyası için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="0fd7b-113">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve yukarıdaki 3 adımda oluşturduğunuz IXmlSerializable dizinini içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="0fd7b-114">IXmlSerializable directory simgesine sağ tıklayın ve seçin **paylaşım ve güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="0fd7b-115">Web Paylaşımı sekmesini seçin **bu klasörü paylaş**ve IXmlSerializable adı dahil olmak üzere varsayılan ayarlarını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="0fd7b-116">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="0fd7b-117">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0fd7b-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="0fd7b-118">Bir tarayıcı penceresi açın ve kendi adres çubuğuna seçin.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="0fd7b-119">Tür **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd7b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0fd7b-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
