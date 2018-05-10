---
title: Yetkilendirme İlkesi
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 3744afb20c06e1ca85b91dadde6549d87ac89337
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="authorization-policy"></a>Yetkilendirme İlkesi
Bu örnek, bir özel talep yetkilendirme ilkesini ve ilişkili özel hizmet Yetkilendirme Yöneticisi uygulama gösterilmiştir. Bu, belirli hakları çağıran hizmet işlemlerine ve erişim denetimleri öncesinde talep tabanlı erişim denetimlerini hizmeti yapar verir durumunda faydalı olur. Bu örnek talep sonlandırılmış kümesini karşı bir erişim denetimi yapmak için işlem yanı sıra talep ekleme işlemini gösterir. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Varsayılan olarak `wsHttpBinding` bağlama, bir kullanıcı adı ve istemci tarafından sağlanan parola kullanılan oturum açmak için geçerli bir Windows NT hesabı. Bu örnek, bir özel kullanmaya gösterilmiştir <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` istemci kimlik doğrulaması için. Ayrıca bu örnek, bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması istemci göstermektedir. Bu örnek uygulaması gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve <xref:System.ServiceModel.ServiceAuthorizationManager>, bunları aralarında hizmetinin belirli kullanıcılar için belirli yöntemler için erişim verin. Bu örnek dayanır [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md), ancak talep dönüştürmeyi öncesinde gerçekleştirmek nasıl gösteren <xref:System.ServiceModel.ServiceAuthorizationManager> çağrılan.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Özet olarak, bu örnek gösterilmektedir nasıl:  
  
-   İstemci, bir kullanıcı adı parolası kullanılarak doğrulanabilir.  
  
-   İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.  
  
-   Sunucu karşı özel bir istemci kimlik doğrulama `UsernamePassword` Doğrulayıcı.  
  
-   Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanır.  
  
-   Sunucu kullanabilir <xref:System.ServiceModel.ServiceAuthorizationManager> hizmet belirli yöntemlerine erişimi denetleme.  
  
-   Nasıl uygulanacağını <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
 Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için iki uç noktalarını kullanıma sunar. Her uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bir standart ile yapılandırılmış bir bağlama `wsHttpBinding` bağlaması WS güvenliği ve istemci kullanıcı adı kimlik doğrulaması kullanır. Bir standart yapılandırılmış diğer bağlama `wsHttpBinding` bağlaması WS güvenliği ve istemci sertifikası kimlik doğrulaması kullanır. [ \<Davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) hizmet kimlik doğrulaması için kullanılacak olan kullanıcı kimlik bilgilerini belirtir. Sunucu sertifikası için aynı değeri içermelidir `SubjectName` özelliği olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <!-- configure base address provided by host -->  
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>  
        </baseAddresses>  
      </host>  
      <!-- use base address provided by host, provide two endpoints -->  
      <endpoint address="username"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      <endpoint address="certificate"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding2"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Username binding -->  
      <binding name="Binding1">  
        <security mode="Message">  
    <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
      <!-- X509 certificate binding -->  
      <binding name="Binding2">  
        <security mode="Message">  
          <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior" >  
        <serviceDebug includeExceptionDetailInFaults ="true" />  
        <serviceCredentials>  
          <!--   
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.    
          -->  
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />  
          <!--   
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.  
          -->  
          <clientCertificate>  
            <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </clientCertificate>  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate.  
          A service certificate is used by a client to authenticate the service and provide message protection.  
          This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
          <!--   
          The serviceAuthorization behavior allows one to specify custom authorization policies.  
          -->  
          <authorizationPolicies>  
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
```  
  
 Her istemci uç nokta yapılandırması yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres oluşur. Bağlama istemci belirtildiği gibi uygun güvenlik moduyla bu durumda yapılandırılan [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ve `clientCredentialType` belirtilmiş [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- Username based endpoint -->  
      <endpoint name="Username"  
            address="http://localhost:8001/servicemodelsamples/service/username"   
    binding="wsHttpBinding"   
    bindingConfiguration="Binding1"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator" >  
      </endpoint>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
                        address="http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
            bindingConfiguration="Binding2"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- Username binding -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding2">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
    </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <behavior name="ClientCertificateBehavior">  
        <clientCredentials>  
          <serviceCertificate>  
            <!--   
            Setting the certificateValidationMode to PeerOrChainTrust  
            means that if the certificate   
            is in the user's Trusted People store, then it will be   
            trusted without performing a  
            validation of the certificate's issuer chain. This setting   
            is used here for convenience so that the   
            sample can be run without having to have certificates   
            issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust.   
            The security implications of this   
            setting should be carefully considered before using   
            PeerOrChainTrust in production code.   
            -->  
            <authentication certificateValidationMode = "PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Kullanıcı adı tabanlı uç noktası için istemci uygulaması kullanıcı adı ve parola ayarlar.  
  
```  
// Create a client with Username endpoint configuration  
CalculatorClient client1 = new CalculatorClient("Username");  
  
client1.ClientCredentials.UserName.UserName = "test1";  
client1.ClientCredentials.UserName.Password = "1tset";  
  
try  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client1.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
    ...  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
}  
  
client1.Close();  
```  
  
 Sertifika tabanlı uç noktası için istemci uygulaması istemci sertifikası kullanacak şekilde ayarlar.  
  
```  
// Create a client with Certificate endpoint configuration  
CalculatorClient client2 = new CalculatorClient("Certificate");  
  
client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
try  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client2.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
    ...  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
}  
  
client2.Close();  
```  
  
 Bu örnek, bir özel kullanmaktadır <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adları ve parolalar doğrulanacak. Örnek uygulayan `MyCustomUserNamePasswordValidator`, türetilmiş <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Belgelerine bakın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> daha fazla bilgi için. İle tümleştirme tanıtmak amacıyla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, bu özel Doğrulayıcı örnek uygulayan <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> burada belirtilen kullanıcı adıyla eşleşen parolayı aşağıdaki kodda gösterildiği gibi kullanıcı adı/parola çiftlerini kabul yöntemi.  
  
```  
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator  
{  
  // This method validates users. It allows in two users,   
  // test1 and test2 with passwords 1tset and 2tset respectively.  
  // This code is for illustration purposes only and   
  // MUST NOT be used in a production environment because it   
  // is NOT secure.      
  public override void Validate(string userName, string password)  
  {  
    if (null == userName || null == password)  
    {  
      throw new ArgumentNullException();  
    }  
  
    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))  
    {  
      throw new SecurityTokenException("Unknown Username or Password");  
    }  
  }  
}  
```  
  
 Doğrulayıcı hizmet kodunda tamamlandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgi sahibi olmak gerekir. Bu yapılır aşağıdaki kodu kullanarak.  
  
```  
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();  
```  
  
 Veya yapılandırma aynı şeyi yapabilirsiniz.  
  
```xml  
<behavior ...>  
    <serviceCredentials>  
      <!--   
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.    
      -->  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />  
    ...  
    </serviceCredentials>  
</behavior>  
```  
  
 Windows Communication Foundation (WCF) erişim denetimleri gerçekleştirmek için zengin talep tabanlı modeli sağlar. <xref:System.ServiceModel.ServiceAuthorizationManager> Nesne erişim denetimi gerçekleştirebilir ve istemciyle ilişkili talep hizmet yöntemi erişimi için gereken koşulları karşılamak olup olmadığını belirlemek için kullanılır.  
  
 Tanıtım amacıyla, bu örnek uygulaması gösterir <xref:System.ServiceModel.ServiceAuthorizationManager> uygulayan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> türü talep tabanlı yöntemleri kullanıcının erişmesine izin vermek için yöntemini http://example.com/claims/allowedoperation değeri olan olan işlem eylem URI'sini çağrılacak izin verilir.  
  
```  
public class MyServiceAuthorizationManager : ServiceAuthorizationManager  
{  
  protected override bool CheckAccessCore(OperationContext operationContext)  
  {                  
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;  
    Console.WriteLine("action: {0}", action);  
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)  
    {  
      if ( cs.Issuer == ClaimSet.System )  
      {  
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))  
        {  
          Console.WriteLine("resource: {0}", c.Resource.ToString());  
          if (action == c.Resource.ToString())  
            return true;  
        }  
      }  
    }  
    return false;                   
  }  
}  
```  
  
 Özel <xref:System.ServiceModel.ServiceAuthorizationManager> olan uygulanan, hizmet ana bilgisayarı hakkında bilgi sahibi olmak gerekir <xref:System.ServiceModel.ServiceAuthorizationManager> kullanmak için. Bu aşağıdaki kodda gösterildiği gibi gerçekleştirilir.  
  
```xml  
<behavior ...>  
    ...  
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
        ...  
    </serviceAuthorization>  
</behavior>  
```  
  
 Birincil <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulamak için yöntem <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi.  
  
```  
public class MyAuthorizationPolicy : IAuthorizationPolicy  
{  
    string id;  
  
    public MyAuthorizationPolicy()  
    {  
    id =  Guid.NewGuid().ToString();  
    }  
  
    public bool Evaluate(EvaluationContext evaluationContext,   
                                            ref object state)  
    {  
        bool bRet = false;  
        CustomAuthState customstate = null;  
  
        if (state == null)  
        {  
            customstate = new CustomAuthState();  
            state = customstate;  
        }  
        else  
            customstate = (CustomAuthState)state;  
        Console.WriteLine("In Evaluate");  
        if (!customstate.ClaimsAdded)  
        {  
           IList<Claim> claims = new List<Claim>();  
  
           foreach (ClaimSet cs in evaluationContext.ClaimSets)  
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,   
                                         Rights.PossessProperty))  
                  foreach (string s in   
                        GetAllowedOpList(c.Resource.ToString()))  
                  {  
                       claims.Add(new  
               Claim("http://example.com/claims/allowedoperation",   
                                    s, Rights.PossessProperty));  
                            Console.WriteLine("Claim added {0}", s);  
                      }  
                   evaluationContext.AddClaimSet(this,   
                           new DefaultClaimSet(this.Issuer,claims));  
                   customstate.ClaimsAdded = true;  
                   bRet = true;  
                }  
         else  
         {  
              bRet = true;  
         }  
         return bRet;  
     }  
...  
}  
```  
  
 Önceki kodun gösterdiği nasıl <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi denetler, işleme etkiler ve belirli talep ekler yeni bir talep eklenmiştir. İzin verilen talep elde edilen `GetAllowedOpList` belirli bir kullanıcının gerçekleştirmesine izin verilen işlemler listesini döndürmek için uygulanması yöntemi. Yetkilendirme İlkesi belirli bir işlemi erişmek için talep ekler. Bu daha sonra tarafından kullanılan <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararlarını gerçekleştirmek için.  
  
 Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , hizmet ana bilgisayarı Yetkilendirme İlkeleri hakkında bilgi sahibi olmak gerekir kullanmak için uygulanır.  
  
```xml  
<serviceAuthorization ...>  
       <authorizationPolicies>   
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />  
       </authorizationPolicies>   
</serviceAuthorization>  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci başarıyla ekleme ve çıkarma birden çok yöntemi çağırır ve bölme yöntemini çağırmak çalışırken bir "Erişim engellendi" iletisi alır. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni sunucusunun adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost varsayılan değerdir.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. Makecert.exe tarafından oluşturulan sertifikalarını örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   İstemci sertifikası oluşturma.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak istemci sertifikası oluşturun. % USER_NAME % değişkeni sunucusunun adını belirtir. Bu ad olduğu için bu değer "test1" ayarlanır `IAuthorizationPolicy` arar. USER_NAME % değerini değiştirirseniz, karşılık gelen değer değiştirmelisiniz `IAuthorizationPolicy.Evaluate` yöntemi.  
  
     Sertifika Currentuser'a depolama konumu altında (Kişisel) My deposunda saklanır.  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   İstemci sertifikası sunucunun güvenilen sertifika deposuna yükleme.  
  
     Setup.bat toplu iş dosyası aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalayın. Makecert.exe tarafından oluşturulan sertifikalarını örtük olarak sunucu sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir güvenilen kök sertifika kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — istemci sertifikası ile sunucu sertifika depolama doldurma, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] örnek yükleme klasöründen çalıştırma Setup.bat ve yönetici ayrıcalıkları ile komut istemi penceresi. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
2.  Visual Studio'da Setup.bat çalıştırmak örnekten yönetici ayrıcalıklarıyla açılmış bir komut istemi yükleme klasörü. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
3.  Service.exe service\bin başlatın.  
  
4.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
5.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyalarını \service\bin hizmeti bilgisayarında dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat, GetComputerName.vbs ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  Bir dizin üzerinde istemci computerfor istemci ikili dosyalarının oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişkeni computerand dışarı tam etki alanı adı ile bir hizmet sertifikası Service.cer adlı bir dosyaya hizmet sertifikası oluşturur.  
  
6.  Yeni sertifika yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu. Ayrıca, computername değiştirmek \<hizmet > /\<baseAddresses > localhost öğesine hizmeti bilgisayarın tam adı.  
  
7.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci üzerinde çalışan `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `client` bağımsız değişkeni test1 adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
9. İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin. Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.  
  
10. Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
11. İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
12. Sunucu üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportClientCert.bat çalıştırın. Bu istemci sertifikası LocalMachine - TrustedPeople deposunda Client.cer dosyadan alır.  
  
13. Sunucu bilgisayarda komut istemi penceresinden Service.exe başlatın.  
  
14. İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın. Bu sunucu ve istemci sertifikaları sertifika deposundan kaldırır.  
  
> [!NOTE]
>  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikalar kullanmak, Currentuser'a - yüklü hizmet sertifikalarını temizlediğinizden emin WCF örnekleri çalıştırırsanız TrustedPeople depolar. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca Bkz.
