---
title: Yetkilendirme İlkesi
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 9b73eea1f51454dd82ba577c4d4d5fd5a1c0efd4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990197"
---
# <a name="authorization-policy"></a>Yetkilendirme İlkesi

Bu örnek, bir özel talep yetkilendirme ilkesinin ve ilişkili bir özel hizmet Yetkilendirme yöneticisinin nasıl uygulanacağını gösterir. Hizmet, hizmet işlemlerine talep tabanlı erişim denetimleri yaptığında ve erişim denetimlerinden önce, çağırana belirli haklar verdiğinde yararlı olur. Bu örnek, hem talep ekleme sürecini hem de son talep kümesinde erişim denetimi yapma işlemini gösterir. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Varsayılan olarak, `wsHttpBinding` bağlama ile, istemci tarafından sağlanan bir Kullanıcı adı ve parola, geçerli bir Windows NT hesabında oturum açmak için kullanılır. Bu örnek, istemcinin kimliğini doğrulamak için bir <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> özel nasıl kullanacağınızı gösterir. Buna ek olarak, bir X. 509.440 sertifikası kullanarak hizmette kimlik doğrulaması yapan istemciyi gösterir. Bu örnek, ve ' nin <xref:System.IdentityModel.Policy.IAuthorizationPolicy> bir <xref:System.ServiceModel.ServiceAuthorizationManager>uygulamasını gösterir ve bu, belirli kullanıcılar için hizmetin belirli yöntemlerine erişim izni verir. Bu örnek, [ileti güvenliği Kullanıcı adına](../../../../docs/framework/wcf/samples/message-security-user-name.md)dayalıdır, ancak çağrılmadan önce <xref:System.ServiceModel.ServiceAuthorizationManager> bir talep dönüşümünün nasıl gerçekleştirileceğini gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Özet bölümünde bu örnek şunları gösterir:

- İstemci, bir Kullanıcı adı-parolası kullanılarak kimlik doğrulaması yapılabilir.

- İstemcinin kimliği bir X. 509.440 sertifikası kullanılarak yapılabilir.

- Sunucu, istemci kimlik bilgilerini özel `UsernamePassword` bir doğrulayıcı ile doğrular.

- Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılır.

- Sunucu, hizmette belirli <xref:System.ServiceModel.ServiceAuthorizationManager> yöntemlere erişimi denetlemek için kullanabilir.

- Nasıl uygulanır <xref:System.IdentityModel.Policy.IAuthorizationPolicy>?

Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için iki uç nokta sunar. Her uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bir bağlama, WS-Security ve `wsHttpBinding` istemci Kullanıcı adı kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır. Diğer bağlama, WS-Security ve istemci `wsHttpBinding` sertifikası kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır. Davranış >, Kullanıcı kimlik bilgilerinin hizmet kimlik doğrulaması için kullanılacağını belirtir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Sunucu sertifikası, `SubjectName` `findValue` [ServiceCertificate > özniteliği olarak özelliği için \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)aynı değeri içermelidir.

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

Her istemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur. İstemci bağlama, [ \<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) bu durumda belirtilen şekilde ve `clientCredentialType` [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)belirtilen şekilde, uygun güvenlik moduyla yapılandırılır.

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

Kullanıcı adı tabanlı uç nokta için, istemci uygulama kullanılacak kullanıcı adını ve parolayı ayarlar.

```csharp
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

Sertifika tabanlı uç nokta için istemci uygulama, kullanılacak istemci sertifikasını ayarlar.

```csharp
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

Bu örnek, Kullanıcı adlarını <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve parolalarını doğrulamak için özel bir kullanır. Örnek `MyCustomUserNamePasswordValidator`, öğesinden <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilir. Daha fazla bilgi <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> için belgelerine bakın. İle <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>tümleştirmeyi gösterme amaçları doğrultusunda, bu özel Doğrulayıcı örneği, aşağıdaki kodda gösterildiği gibi Kullanıcı <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> adının parolayla eşleştiği Kullanıcı adı/parola çiftlerini kabul etmek için yöntemini uygular.

```csharp
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

Doğrulayıcı hizmet koduna uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir. Bu, aşağıdaki kod kullanılarak yapılır:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Ya da yapılandırmada aynı şeyi yapabilirsiniz:

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

Windows Communication Foundation (WCF), erişim denetimleri gerçekleştirmek için zengin bir talep tabanlı model sağlar. <xref:System.ServiceModel.ServiceAuthorizationManager> Nesnesi, erişim denetimini gerçekleştirmek ve istemciyle ilişkili taleplerin hizmet yöntemine erişmek için gereken gereksinimleri karşılayıp karşılamadığını tespit etmek için kullanılır.

Gösterim amaçları doğrultusunda, bu örnek, bir kullanıcının, değeri bir <xref:System.ServiceModel.ServiceAuthorizationManager> işlemin işlem URI <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 'si olan tür `http://example.com/claims/allowedoperation` taleplerini temel alan yöntemlere erişimi sağlamak için yöntemini uygulayan uygulamasının bir uygulamasını gösterir. çağrılmasına izin verildi.

```csharp
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

Özel <xref:System.ServiceModel.ServiceAuthorizationManager> uygulandıktan sonra, hizmet ana bilgisayarının kullanım <xref:System.ServiceModel.ServiceAuthorizationManager> hakkında bilgilendirilmesi gerekir. Bu, aşağıdaki kodda gösterildiği gibi yapılır.

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<xref:System.IdentityModel.Policy.IAuthorizationPolicy> Uygulanacak<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> birincil yöntem yöntemidir.

```csharp
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

Önceki kod, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yönteminin işlemeyi etkileyen ve belirli talepler ekleyen hiçbir yeni talep bulunmadığını denetlemesini gösterir. İzin verilen talepler, kullanıcının gerçekleştirmesine izin verilen işlemlerin `GetAllowedOpList` belirli bir listesini döndürmek için uygulanan yönteminden alınır. Yetkilendirme ilkesi, belirli bir işleme erişim taleplerini ekler. Bu daha sonra, <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararlarını gerçekleştirmek için tarafından kullanılır.

Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak yetkilendirme ilkeleri hakkında bilgilendirilmesi gerekir.

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci, Ekle, çıkart ve birden çok yöntemi başarıyla çağırır ve bölme yöntemini çağırmaya çalışırken bir "erişim reddedildi" iletisi alır. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu

Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.

Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sunar:

- Sunucu sertifikası oluşturuluyor.

    Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. % SERVER_NAME% değişkeni sunucu adını belirtiyor. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Varsayılan değer localhost 'tur.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.

    Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediği için gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- İstemci sertifikası oluşturuluyor.

    Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur. % USER_NAME% değişkeni sunucu adını belirtiyor. Bu değer "test1" olarak ayarlanır çünkü bu ad, `IAuthorizationPolicy` için arama yapar. % User_name% değerini değiştirirseniz, `IAuthorizationPolicy.Evaluate` yönteminde karşılık gelen değeri değiştirmeniz gerekir.

    Sertifika, CurrentUser Store konumu altında (kişisel) deposunda depolanır.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.

    Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, istemci sertifikasını güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikalara sunucu sistemi tarafından örtük olarak güvenilmediği için gereklidir. Güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), sunucu sertifika deposunu istemci sertifikası ile doldurmak için bu adım gerekli değildir.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için

1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

2. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.

> [!NOTE]
> Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil. exe ' yi kullanırsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yönetici ayrıcalıklarıyla Visual Studio için Geliştirici Komut İstemi açın ve örnek yükleme klasöründen *Setup. bat* dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup. bat toplu iş dosyası, Visual Studio için Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır. Visual Studio için Geliştirici Komut İstemi içinde ayarlanan yol ortamı değişkeni *Setup. bat* betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.

1. *Service\bin*' den Service. exe ' yi başlatın.

1. *\Client\bin*adresinden Client. exe ' yi başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.

İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için

1. Hizmet bilgisayarında bir dizin oluşturun.

2. Hizmet programı dosyalarını *\service\bin* konumundan hizmet bilgisayarındaki dizine kopyalayın. Ayrıca Setup. bat, Cleanup. bat, GetComputerName. vbs ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.

3. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.

4. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.

5. Sunucusunda, yönetici ayrıcalıklarıyla açılan `setup.bat service` Visual Studio için geliştirici komut istemi ' de çalıştırın.

    Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` , bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını *Service. cer*adlı bir dosyaya aktarır.

6. *Service. exe. config dosyasını* , bilgisayarın tam etki alanı adıyla aynı olan yeni `findValue` sertifika adını ( [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)özniteliğinde) yansıtacak şekilde düzenleyin. Ayrıca \<Service >/\<BaseAddresses > öğesindeki **ComputerName** öğesini localhost 'dan hizmet bilgisayarınızın tam adına değiştirin.

7. Service *. cer* dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.

8. İstemcisinde, yönetici ayrıcalıklarıyla açılan `setup.bat client` Visual Studio için geliştirici komut istemi ' de çalıştırın.

    Bağımsız `setup.bat` değişkeniyle birlikte `client` çalıştırmak, **test1** adlı bir istemci sertifikası oluşturur ve istemci sertifikasını *Client. cer*adlı bir dosyaya aktarır.

9. İstemci bilgisayardaki *Client. exe. config* dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. **Localhost** 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.

10. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.

11. İstemcisinde, yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut İstemi 'de *ImportServiceCert. bat* dosyasını çalıştırın.

    Bu, hizmet sertifikasını Service. cer dosyasından **CurrentUser-Trustedkişiler** deposuna aktarır.

12. Sunucusunda, yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut İstemi 'de *ImportClientCert. bat* dosyasını çalıştırın.

    Bu, istemci sertifikasını Client. cer dosyasından **LocalMachine-Trustedkişiler** deposuna aktarır.

13. Sunucu bilgisayarda, komut istemi penceresinden Service. exe ' yi başlatın.

14. İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın.

    İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Örnekten sonra temizle

Örnekten sonra temizlemek için, örneği çalıştırmayı bitirdiğinizde Samples klasöründe *Cleanup. bat* dosyasını çalıştırın. Bu, sunucu ve istemci sertifikalarını sertifika deposundan kaldırır.

> [!NOTE]
> Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan WCF örnekleri çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
