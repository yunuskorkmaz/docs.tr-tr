---
title: Yetkilendirme İlkesi
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: eaf4dfc6e1f02a1cd98d9ab48af70426e8ba6151
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217301"
---
# <a name="authorization-policy"></a>Yetkilendirme İlkesi

Bu örnek bir özel talep yetkilendirme ilkesi ve bir ilişkili özel hizmet Yetkilendirme Yöneticisi'ni uygulamak nasıl gösterir. Hizmet işlemlerine ve erişim denetimleri önce talep tabanlı erişim denetimlerini hizmet yapar verdiğinde çağıran belirli hakları kullanışlıdır. Bu örnek, talepleri ve bunun yanı sıra işlemi sonlandırılmış talepler kümesi karşı bir erişim denetimi yapmak için ekleme işlemini gösterir. Tüm uygulama iletileri istemci ve sunucu arasında imzalanmış ve şifrelenmiş. Varsayılan olarak `wsHttpBinding` bağlama, bir kullanıcı adı ve parola istemci tarafından sağlanan kullanılan oturum açmak için geçerli bir Windows NT hesap. Bu örnek nasıl özel bir gösterir <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` istemcinin kimliğini doğrulamak için. Ayrıca bu örnek, bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması istemci gösterir. Bu örnek uygulanışı gösterilmektedir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve <xref:System.ServiceModel.ServiceAuthorizationManager>, bunlar arasında belirli kullanıcılar için hizmetin belirli yöntemler için erişim verin. Bu örnek dayanır [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md), ama öncesinde bir talep dönüştürmeyi gerçekleştirmek nasıl gösterir <xref:System.ServiceModel.ServiceAuthorizationManager> çağrılan.

> [!NOTE]
> Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

 Özet olarak, bu örnek gösterir nasıl:

-   İstemci, bir kullanıcı adı parola kullanılarak doğrulanabilir.

-   İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.

-   Sunucu karşı özel bir istemci kimlik doğrulama `UsernamePassword` Doğrulayıcı.

-   Sunucu sunucusunun X.509 sertifikasını kullanarak kimlik doğrulaması yapılır.

-   Sunucu kullanabilir <xref:System.ServiceModel.ServiceAuthorizationManager> erişimi denetlemek için bazı yöntemler hizmetinde.

-   Nasıl uygulanacağı <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için iki uç noktalarını kullanıma sunar. Her uç nokta, adres, bağlama ve bir sözleşme oluşur. Standart ile yapılandırılmış bir bağlama `wsHttpBinding` bağlama kullanan WS-güvenlik ve istemci kimlik doğrulama kullanıcı adı. Bir standart yapılandırılmış diğer bağlama `wsHttpBinding` bağlaması, WS-güvenlik ve istemci sertifikası kimlik doğrulaması kullanır. [ \<Davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) hizmet kimlik doğrulaması için kullanılacak olan kullanıcı kimlik bilgilerini belirtir. Sunucu sertifikası için aynı değeri içermelidir `SubjectName` özelliği olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

İstemci uç nokta yapılandırması her bir yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres oluşur. Bağlama istemci belirtildiği gibi uygun güvenlik moduyla bu durumda yapılandırılan [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ve `clientCredentialType` belirtilmiş [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

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

Kullanıcı adı tabanlı uç noktası için istemci uygulaması, kullanıcı adını ve parolayı ayarlar.

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

Sertifika tabanlı uç noktası için kullanılacak istemci sertifikası istemci uygulaması ayarlar.

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

Bu örnek bir özel kullanan <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adları ve parolaları doğrulamak için. Örnek uygulayan `MyCustomUserNamePasswordValidator`, türetilmiş <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Belgelere bakın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> daha fazla bilgi için. İle tümleştirme tanıtmak amacıyla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, bu özel Doğrulayıcı sağlayıcısı örnek uygulayan <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> burada belirtilen kullanıcı adıyla eşleşen parola aşağıdaki kodda gösterildiği gibi kullanıcı adı/parola çiftlerini kabul etmek için yöntemi.

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

Doğrulayıcı hizmeti kodunda uygulandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir. Bu yapılır aşağıdaki kodu kullanarak:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Ya da aynı şeyi yapılandırmasında yapabilirsiniz:

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

Windows Communication Foundation (WCF) erişim denetimi gerçekleştirmek için zengin talep tabanlı modeli sağlar. <xref:System.ServiceModel.ServiceAuthorizationManager> Nesne erişim denetimi gerçekleştirmek ve istemci ile ilişkili talep hizmet yöntemi erişimi gereksinimleri karşılayıp olup olmadığını belirlemek için kullanılır.

Gösterim amaçları doğrultusunda, bu örnek uygulanışı gösterilmektedir. <xref:System.ServiceModel.ServiceAuthorizationManager> uygulayan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> talep türü tabanlı yöntemler bir kullanıcının erişmesine izin vermek için yöntemini http://example.com/claims/allowedoperation değeri olan işlem eylemi URI'si çağrılacak izin verilir.

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

Özel <xref:System.ServiceModel.ServiceAuthorizationManager> olduğu uygulanan, hizmet ana bilgisayarı hakkında bilgilendirilmesi gereken <xref:System.ServiceModel.ServiceAuthorizationManager> kullanılacak. Bu, aşağıdaki kodda gösterildiği gibi gerçekleştirilir.

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Birincil <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulamak için yöntem <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi.

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

Önceki kodun gösterdiği nasıl <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi yeni talep işleme etkiler ve belirli bir talep ekler eklendiğinizi denetler. İzin verilen bir talep elde edilen `GetAllowedOpList` belirli bir kullanıcının gerçekleştirmesine izin işlemleri listesini döndürmek için uygulanan yöntem. Yetkilendirme İlkesi, belirli bir işlemi erişmek için talep ekler. Bu daha sonra tarafından kullanılan <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararları gerçekleştirilecek.

Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , hizmet ana bilgisayarı Yetkilendirme İlkeleri hakkında bilgilendirilmesi kullanmak için uygulanır.

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci başarıyla ekleme, çıkarma ve birden çok yöntem çağrıları ve bölme yöntem çağrılmaya çalışılırken "Erişim engellendi" iletisi alır. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası

Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar.

Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:

-   Sunucu sertifikası oluşturuluyor.

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost varsayılan değerdir.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. Makecert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   İstemci sertifikası oluşturuluyor.

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak istemci sertifikası oluşturun. % USER_NAME % değişkeni, sunucu adını belirtir. Bu ad olduğundan, bu değer "test1" için ayarlanır `IAuthorizationPolicy` arar. USER_NAME % değerini değiştirirseniz, karşılık gelen değer değiştirmelisiniz `IAuthorizationPolicy.Evaluate` yöntemi.

     Sertifika CurrentUser depolama konumu altında (Kişisel) My deposunda depolanır.

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   İstemci sertifikası sunucusunun güvenilen sertifika depolama alanına yükleme.

     Setup.bat toplu iş dosyasında aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikaları sunucu sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir. Bir güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — istemci sertifikası ile sunucu sertifika deposuna yerleştirmek, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.

> [!NOTE]
> Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Geliştirici komut istemi için Visual Studio'yu yönetici ayrıcalıklarıyla açıp çalıştırın *Setup.bat* örnek yükleme klasöründen. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    > Setup.bat toplu iş dosyası, Visual Studio için geliştirici komut isteminden çalıştırılması için tasarlanmıştır. Visual Studio tarafından gereken yürütülebilir dosyaları içeren dizine işaret için geliştirici komut istemi içinde PATH ortam değişkenini ayarlama *Setup.bat* betiği.

1. Gelen Service.exe başlatma *service\bin*.

1. Gelen Client.exe başlatma *\client\bin*. İstemci etkinliği istemci konsol uygulamasında görüntülenir.

  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için

1. Hizmet bilgisayarda bir dizin oluşturun.

2. Hizmet programı dosyaların kopyalanacağı *\service\bin* hizmeti bilgisayarında dizinine. Ayrıca hizmet bilgisayara Setup.bat, Cleanup.bat GetComputerName.vbs ve ImportClientCert.bat dosyaları kopyalayın.

3. İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.

4. İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.

5. Sunucu üzerinde çalışan `setup.bat service` , yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi.

   Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası adlı bir dosyaya dışarı aktarır *Service.cer*.

6. Düzen *Service.exe.config* yeni sertifika adını yansıtacak şekilde (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) tam etki alanı adıyla aynı olduğu bilgisayarı. Ayrıca değiştirmek **computername** içinde \<hizmet > /\<baseAddresses > localhost öğesine hizmet bilgisayarınızın tam adı.

7. Kopyalama *Service.cer* hizmet dizininden istemci bilgisayarda dosya istemci dizine.

8. Bir istemcide çalışmasına `setup.bat client` , yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi.

   Çalışan `setup.bat` ile `client` bağımsız değişkeni oluşturur adlı bir istemci sertifikası **test1** ve istemci sertifikasını adlı bir dosyaya dışarı aktarır *Client.cer*.

9. İçinde *Client.exe.config* dosyasını istemci bilgisayarda, hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin. Değiştirerek bunu **localhost** sunucusunun tam etki alanı adı ile.

10. Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.

11. Bir istemcide çalışmasına *ImportServiceCert.bat* , yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi.

   Bu hizmet sertifikası Service.cer dosyasına alır **CurrentUser - TrustedPeople** depolayın.

12. Sunucu üzerinde çalışan *ImportClientCert.bat* , yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi.

   Bu istemci sertifikasını Client.cer dosyasına alır **LocalMachine - TrustedPeople** depolayın.

13. Sunucu bilgisayarında, komut istemi penceresinden Service.exe başlatın.

14. İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.

   İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="clean-up-after-the-sample"></a>Sonra örnek temizleme

Sonra örnek temizlemek için çalıştırma *Cleanup.bat* örnek çalıştırmayı tamamladığınızda samples klasöründe. Bu, sunucu ve istemci sertifikaları sertifika deposundan kaldırır.

> [!NOTE]
> Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bu bilgisayarlar arasında sertifikalar kullanmak, içinde CurrentUser - yüklü hizmet sertifikalarını temizlendiğinden emin WCF örnekleri çalıştırırsanız TrustedPeople depolayın. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.