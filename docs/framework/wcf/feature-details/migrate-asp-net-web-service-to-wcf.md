---
title: "Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma"
ms.date: 03/30/2017
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
ms.openlocfilehash: 90a6109a56299ec1bcaff4a35141abc194484772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496705"
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="054d2-102">Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma</span><span class="sxs-lookup"><span data-stu-id="054d2-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="054d2-103">Aşağıdaki yordam, Windows Communication Foundation (WCF) için bir ASP.NET Web hizmeti geçirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="054d2-103">The following procedure describes how to migrate an ASP.NET Web Service to Windows Communication Foundation (WCF).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="054d2-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="054d2-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="054d2-105">WCF için ASP.NET Web hizmeti kodunu geçirmek için</span><span class="sxs-lookup"><span data-stu-id="054d2-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="054d2-106">Kapsamlı bir emin testleri kümesi hizmeti için mevcut.</span><span class="sxs-lookup"><span data-stu-id="054d2-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="054d2-107">Hizmeti için WSDL oluşturmak ve hizmetin .asmx dosya ile aynı klasörde bir kopyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="054d2-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="054d2-108">ASP.NET Web hizmetini .NET 2.0 kullanacak biçimde yükseltin.</span><span class="sxs-lookup"><span data-stu-id="054d2-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="054d2-109">Önce .NET Framework 2.0 IIS uygulama dağıtın ve sonra Visual Studio 2005 kod dönüştürme işlemini otomatikleştirmek için açıklandığı gibi [adım adım kılavuzu gelen Visual Studio .NET 2002/2003 Visual Studio Dönüştürme Web projeleri için 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span><span class="sxs-lookup"><span data-stu-id="054d2-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="054d2-110">Test kümesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="054d2-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="054d2-111">Açık değerlerini sağlamanız `Namespace` ve `Name` parametrelerinin <xref:System.Web.Services.WebService> zaten değil sağlandıysa öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="054d2-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="054d2-112">Aynı işlemi gerçekleştirmek `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="054d2-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="054d2-113">Tarafından istekleri yönlendirilir yöntemleri için ardından açıkça SOAPAction HTTP üstbilgileri varsayılan değerini belirtmek için açık değerler zaten sağlanmamışsa `Action` parametresiyle bir <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="054d2-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
5.  <span data-ttu-id="054d2-114">Değişiklik sınayın.</span><span class="sxs-lookup"><span data-stu-id="054d2-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="054d2-115">Sınıfının yöntemlerini gövdeleri substantive herhangi kodda özgün sınıfı kullanmak için yapılan ayrı bir sınıf taşıyın.</span><span class="sxs-lookup"><span data-stu-id="054d2-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
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
  
7.  <span data-ttu-id="054d2-116">Değişiklik sınayın.</span><span class="sxs-lookup"><span data-stu-id="054d2-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="054d2-117">WCF derlemelerine System.ServiceModel ve System.Runtime.Serialization başvurular ASP.NET Web hizmeti projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="054d2-117">Add references to WCF assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="054d2-118">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSDL WCF istemci sınıfı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="054d2-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a WCF client class from the WSDL.</span></span> <span data-ttu-id="054d2-119">Oluşturulan sınıf modülü çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="054d2-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="054d2-120">Önceki adımda oluşturulan sınıf modülü bir arabirim tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="054d2-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
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
  
     <span data-ttu-id="054d2-121">ASP.NET Web hizmeti sınıfının tanımını sınıfı bu arabirimi gerçekleştiren olarak aşağıdaki örnek kodda gösterildiği gibi tanımlanan şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="054d2-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
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
  
11. <span data-ttu-id="054d2-122">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="054d2-122">Compile the project.</span></span> <span data-ttu-id="054d2-123">Bazı hatalar nedeniyle bazı tür tanımları yinelenen dokuz adımda oluşturulan kodu olabilir.</span><span class="sxs-lookup"><span data-stu-id="054d2-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="054d2-124">Bu hatalar genellikle türlerinin önceden varolan tanımlarını silerek onarın.</span><span class="sxs-lookup"><span data-stu-id="054d2-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="054d2-125">Değişiklik sınayın.</span><span class="sxs-lookup"><span data-stu-id="054d2-125">Test the change.</span></span>  
  
12. <span data-ttu-id="054d2-126">ASP.NET özel öznitelikleri gibi kaldırmak <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="054d2-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
13. <span data-ttu-id="054d2-127">ASP.NET Web hizmeti aşağıdakilerden birini dayanıyordu, WCF ASP.NET uyumluluk modu gerektirecek şekilde bir WCF hizmeti türü sunulmuştur sınıfı yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="054d2-127">Configure the class, which is now a WCF service type, to require WCF ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="054d2-128"><xref:System.Web.HttpContext> Sınıfı.</span><span class="sxs-lookup"><span data-stu-id="054d2-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="054d2-129">ASP.NET profiller.</span><span class="sxs-lookup"><span data-stu-id="054d2-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="054d2-130">.Asmx dosyalarını ACL'lerin.</span><span class="sxs-lookup"><span data-stu-id="054d2-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="054d2-131">IIS kimlik doğrulaması seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="054d2-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="054d2-132">ASP.NET kimliğe bürünme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="054d2-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="054d2-133">ASP.NET Genelleştirme.</span><span class="sxs-lookup"><span data-stu-id="054d2-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="054d2-134">Özgün .asmx dosyayı yeniden adlandırın. asmx.old.</span><span class="sxs-lookup"><span data-stu-id="054d2-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="054d2-135">Hizmet için bir WCF hizmeti dosya oluşturma, uzantısı verin, .asmx ve IIS uygulama kökü içine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="054d2-135">Create a WCF service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="054d2-136">Bir WCF Yapılandırma hizmeti için Web.config dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="054d2-136">Add a WCF configuration for the service to its Web.config file.</span></span> <span data-ttu-id="054d2-137">Hizmetini kullanacak şekilde yapılandırmanız [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), önceki adımlarda oluşturduğunuz .asmx uzantısı ile hizmet dosyası kullanılacak ve WSDL kendisi için değil oluşturulacak, ancak iki adımdan WSDL kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="054d2-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="054d2-138">Ayrıca gerekirse, ASP.NET uyumluluğu modunu kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="054d2-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
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
  
17. <span data-ttu-id="054d2-139">Yapılandırmayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="054d2-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="054d2-140">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="054d2-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="054d2-141">Tüm değişiklikleri çalıştığından emin olmak için test kümesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="054d2-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054d2-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="054d2-142">See Also</span></span>  
 [<span data-ttu-id="054d2-143">Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma</span><span class="sxs-lookup"><span data-stu-id="054d2-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
