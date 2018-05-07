---
title: "Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma"
ms.date: 03/30/2017
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
ms.openlocfilehash: 90a6109a56299ec1bcaff4a35141abc194484772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a>Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma
Aşağıdaki yordam, Windows Communication Foundation (WCF) için bir ASP.NET Web hizmeti geçirmeyi açıklar.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a>WCF için ASP.NET Web hizmeti kodunu geçirmek için  
  
1.  Kapsamlı bir emin testleri kümesi hizmeti için mevcut.  
  
2.  Hizmeti için WSDL oluşturmak ve hizmetin .asmx dosya ile aynı klasörde bir kopyasını kaydedin.  
  
3.  ASP.NET Web hizmetini .NET 2.0 kullanacak biçimde yükseltin. Önce .NET Framework 2.0 IIS uygulama dağıtın ve sonra Visual Studio 2005 kod dönüştürme işlemini otomatikleştirmek için açıklandığı gibi [adım adım kılavuzu gelen Visual Studio .NET 2002/2003 Visual Studio Dönüştürme Web projeleri için 2005](http://go.microsoft.com/fwlink/?LinkId=96492). Test kümesini çalıştırın.  
  
4.  Açık değerlerini sağlamanız `Namespace` ve `Name` parametrelerinin <xref:System.Web.Services.WebService> zaten değil sağlandıysa öznitelikleri. Aynı işlemi gerçekleştirmek `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>. Tarafından istekleri yönlendirilir yöntemleri için ardından açıkça SOAPAction HTTP üstbilgileri varsayılan değerini belirtmek için açık değerler zaten sağlanmamışsa `Action` parametresiyle bir <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
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
  
5.  Değişiklik sınayın.  
  
6.  Sınıfının yöntemlerini gövdeleri substantive herhangi kodda özgün sınıfı kullanmak için yapılan ayrı bir sınıf taşıyın.  
  
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
  
7.  Değişiklik sınayın.  
  
8.  WCF derlemelerine System.ServiceModel ve System.Runtime.Serialization başvurular ASP.NET Web hizmeti projeye ekleyin.  
  
9. Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSDL WCF istemci sınıfı oluşturmak için. Oluşturulan sınıf modülü çözüme ekleyin.  
  
10. Önceki adımda oluşturulan sınıf modülü bir arabirim tanımını içerir.  
  
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
  
     ASP.NET Web hizmeti sınıfının tanımını sınıfı bu arabirimi gerçekleştiren olarak aşağıdaki örnek kodda gösterildiği gibi tanımlanan şekilde değiştirin.  
  
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
  
11. Projeyi derleyin. Bazı hatalar nedeniyle bazı tür tanımları yinelenen dokuz adımda oluşturulan kodu olabilir. Bu hatalar genellikle türlerinin önceden varolan tanımlarını silerek onarın. Değişiklik sınayın.  
  
12. ASP.NET özel öznitelikleri gibi kaldırmak <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> ve <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
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
  
13. ASP.NET Web hizmeti aşağıdakilerden birini dayanıyordu, WCF ASP.NET uyumluluk modu gerektirecek şekilde bir WCF hizmeti türü sunulmuştur sınıfı yapılandırın:  
  
    -   <xref:System.Web.HttpContext> Sınıfı.  
  
    -   ASP.NET profiller.  
  
    -   .Asmx dosyalarını ACL'lerin.  
  
    -   IIS kimlik doğrulaması seçenekleri.  
  
    -   ASP.NET kimliğe bürünme seçenekleri.  
  
    -   ASP.NET Genelleştirme.  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. Özgün .asmx dosyayı yeniden adlandırın. asmx.old.  
  
15. Hizmet için bir WCF hizmeti dosya oluşturma, uzantısı verin, .asmx ve IIS uygulama kökü içine kaydedin.  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. Bir WCF Yapılandırma hizmeti için Web.config dosyasına ekleyin. Hizmetini kullanacak şekilde yapılandırmanız [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), önceki adımlarda oluşturduğunuz .asmx uzantısı ile hizmet dosyası kullanılacak ve WSDL kendisi için değil oluşturulacak, ancak iki adımdan WSDL kullanılacak. Ayrıca gerekirse, ASP.NET uyumluluğu modunu kullanacak şekilde yapılandırın.  
  
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
  
17. Yapılandırmayı kaydedin.  
  
18. Projeyi derleyin.  
  
19. Tüm değişiklikleri çalıştığından emin olmak için test kümesini çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
