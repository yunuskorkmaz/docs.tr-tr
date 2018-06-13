---
title: "Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma"
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491136"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="2a1f3-102">Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma</span><span class="sxs-lookup"><span data-stu-id="2a1f3-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="2a1f3-103">Aşağıdaki yordamda, ASP.NET Web hizmeti istemci kodunu WCF'ye taşıma için izlenmesi gereken genel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to WCF.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="2a1f3-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="2a1f3-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="2a1f3-105">WCF için ASP.NET Web hizmeti istemci kodunu geçirmek için</span><span class="sxs-lookup"><span data-stu-id="2a1f3-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="2a1f3-106">Kapsamlı bir emin testleri kümesini istemci için mevcut.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="2a1f3-107">.NET 2.0 istemci uygulamaya yükseltmek için Visual Studio 2005 kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="2a1f3-108">Test kümesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="2a1f3-109">ASP.NET istemci kodu istemci projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="2a1f3-110">Kod modülleri WSDL.exe aracı kullanılarak oluşturulan olduğunu.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="2a1f3-111">WCF istemci kodu kullanarak Oluştur [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2a1f3-111">Generate WCF client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="2a1f3-112">Bu kod istemci projenize ekleyin ve istemcinin var olan yapılandırma dosyasına yapılandırma çıktısını birleştirin.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="2a1f3-113">Uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-113">Compile the application.</span></span> <span data-ttu-id="2a1f3-114">Derleme hataları yeni WCF istemci türlerini başvuruları eski ASP.NET istemci tür başvuruları değiştirerek onarın.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new WCF client types.</span></span>  
  
6.  <span data-ttu-id="2a1f3-115">Test kümesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1f3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a1f3-116">See Also</span></span>  
 [<span data-ttu-id="2a1f3-117">Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma</span><span class="sxs-lookup"><span data-stu-id="2a1f3-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
