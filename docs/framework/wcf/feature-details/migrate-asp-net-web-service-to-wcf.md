---
title: "Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e56d2481785a9a8486174e611001b9d800c7c869
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="d24a6-102">Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma</span><span class="sxs-lookup"><span data-stu-id="d24a6-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="d24a6-103">Aşağıdaki yordam, ASP.NET Web hizmeti için geçirmeyi açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d24a6-103">The following procedure describes how to migrate an ASP.NET Web Service to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d24a6-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="d24a6-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="d24a6-105">WCF için ASP.NET Web hizmeti kodunu geçirmek için</span><span class="sxs-lookup"><span data-stu-id="d24a6-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="d24a6-106">Kapsamlı bir emin testleri kümesi hizmeti için mevcut.</span><span class="sxs-lookup"><span data-stu-id="d24a6-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="d24a6-107">Hizmeti için WSDL oluşturmak ve hizmetin .asmx dosya ile aynı klasörde bir kopyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="d24a6-108">ASP.NET Web hizmetini .NET 2.0 kullanacak biçimde yükseltin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="d24a6-109">Önce .NET Framework 2.0 IIS uygulama dağıtın ve sonra Visual Studio 2005 kod dönüştürme işlemini otomatikleştirmek için açıklandığı gibi [adım adım kılavuzu gelen Visual Studio .NET 2002/2003 Visual Studio Dönüştürme Web projeleri için 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span><span class="sxs-lookup"><span data-stu-id="d24a6-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="d24a6-110">Test kümesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="d24a6-111">Açık değerlerini sağlamanız `Namespace` ve `Name` parametrelerinin <xref:System.Web.Services.WebService> zaten değil sağlandıysa öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="d24a6-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="d24a6-112">Aynı işlemi gerçekleştirmek `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d24a6-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="d24a6-113">Tarafından istekleri yönlendirilir yöntemleri için ardından açıkça SOAPAction HTTP üstbilgileri varsayılan değerini belirtmek için açık değerler zaten sağlanmamışsa `Action` parametresiyle bir <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d24a6-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  <span data-ttu-id="d24a6-114">Değişiklik sınayın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="d24a6-115">Sınıfının yöntemlerini gövdeleri substantive herhangi kodda özgün sınıfı kullanmak için yapılan ayrı bir sınıf taşıyın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  <span data-ttu-id="d24a6-116">Değişiklik sınayın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="d24a6-117">Başvurular ekleyin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] derlemelere System.ServiceModel ve System.Runtime.Serialization ASP.NET Web hizmeti projesi.</span><span class="sxs-lookup"><span data-stu-id="d24a6-117">Add references to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="d24a6-118">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL istemci sınıfından.</span><span class="sxs-lookup"><span data-stu-id="d24a6-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class from the WSDL.</span></span> <span data-ttu-id="d24a6-119">Oluşturulan sınıf modülü çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="d24a6-120">Önceki adımda oluşturulan sınıf modülü bir arabirim tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="d24a6-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     <span data-ttu-id="d24a6-121">ASP.NET Web hizmeti sınıfının tanımını sınıfı bu arabirimi gerçekleştiren olarak aşağıdaki örnek kodda gösterildiği gibi tanımlanan şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. <span data-ttu-id="d24a6-122">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-122">Compile the project.</span></span> <span data-ttu-id="d24a6-123">Bazı hatalar nedeniyle bazı tür tanımları yinelenen dokuz adımda oluşturulan kodu olabilir.</span><span class="sxs-lookup"><span data-stu-id="d24a6-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="d24a6-124">Bu hatalar genellikle türlerinin önceden varolan tanımlarını silerek onarın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="d24a6-125">Değişiklik sınayın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-125">Test the change.</span></span>  
  
12. <span data-ttu-id="d24a6-126">ASP.NET özel öznitelikleri gibi kaldırmak <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d24a6-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. <span data-ttu-id="d24a6-127">Artık sınıfını Yapılandır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet gerektirecek şekilde türünü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET Web hizmeti aşağıdakilerden birini dayanıyordu, ASP.NET uyumluluk modu:</span><span class="sxs-lookup"><span data-stu-id="d24a6-127">Configure the class, which is now a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service type, to require [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="d24a6-128"><xref:System.Web.HttpContext> Sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d24a6-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="d24a6-129">ASP.NET profiller.</span><span class="sxs-lookup"><span data-stu-id="d24a6-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="d24a6-130">.Asmx dosyalarını ACL'lerin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="d24a6-131">IIS kimlik doğrulaması seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="d24a6-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="d24a6-132">ASP.NET kimliğe bürünme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="d24a6-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="d24a6-133">ASP.NET Genelleştirme.</span><span class="sxs-lookup"><span data-stu-id="d24a6-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="d24a6-134">Özgün .asmx dosyayı yeniden adlandırın. asmx.old.</span><span class="sxs-lookup"><span data-stu-id="d24a6-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="d24a6-135">Oluşturma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet hizmet için dosya, uzantısı verin, .asmx ve IIS uygulama kökü içine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-135">Create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="d24a6-136">Ekleme bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , Web.config dosyasında hizmeti için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d24a6-136">Add a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration for the service to its Web.config file.</span></span> <span data-ttu-id="d24a6-137">Hizmetini kullanacak şekilde yapılandırmanız [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), önceki adımlarda oluşturduğunuz .asmx uzantısı ile hizmet dosyası kullanılacak ve WSDL kendisi için değil oluşturulacak, ancak iki adımdan WSDL kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="d24a6-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="d24a6-138">Ayrıca gerekirse, ASP.NET uyumluluğu modunu kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address=""  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
17. <span data-ttu-id="d24a6-139">Yapılandırmayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="d24a6-140">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="d24a6-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="d24a6-141">Tüm değişiklikleri çalıştığından emin olmak için test kümesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d24a6-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d24a6-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d24a6-142">See Also</span></span>  
 [<span data-ttu-id="d24a6-143">Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma</span><span class="sxs-lookup"><span data-stu-id="d24a6-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
