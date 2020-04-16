---
title: Yetkilendirme İlkesi
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463942"
---
# <a name="authorization-policy"></a>Yetkilendirme İlkesi

Bu örnek, özel talep yetkilendirme ilkesi nin ve ilişkili bir özel hizmet yetkilendirme yöneticisinin nasıl uygulanacağını gösterir. Bu, hizmet işlemlerine talep tabanlı erişim denetimleri yaptığında ve erişim denetimlerinden önce arayana belirli haklar verdiğinde yararlıdır. Bu örnek, hem talep ekleme işlemini hem de kesinleşen talep kümesine karşı bir erişim denetimi yapma işlemini gösterir. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Varsayılan `wsHttpBinding` olarak bağlama ile, istemci tarafından sağlanan bir kullanıcı adı ve parola geçerli bir Windows NT hesabına oturum açmak için kullanılır. Bu örnek, istemcinin kimliğini <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> doğrulamak için bir özelin nasıl kullanılacağını gösterir. Ayrıca bu örnek, X.509 sertifikası kullanarak hizmete kimlik doğrulayan istemciyi gösterir. Bu örnek, aralarında <xref:System.IdentityModel.Policy.IAuthorizationPolicy> <xref:System.ServiceModel.ServiceAuthorizationManager>belirli kullanıcılar için hizmetin belirli yöntemlerine erişim sağlayan bir uygulama gösterir. Bu örnek İleti [Güvenliği Kullanıcı Adını](../../../../docs/framework/wcf/samples/message-security-user-name.md)temel alıyor, ancak çağrılmadan <xref:System.ServiceModel.ServiceAuthorizationManager> önce bir talep dönüştürmesinin nasıl gerçekleştiriltigerektiğini gösterir.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

 Özetle, bu örnek nasıl gösterir:

- İstemcinin kimliği bir kullanıcı adı parolası kullanılarak doğrulanabilir.

- İstemci X.509 sertifikası kullanılarak kimlik doğrulanabilir.

- Sunucu, istemci kimlik bilgilerini özel `UsernamePassword` bir doğrulayıcıya karşı doğrular.

- Sunucu, sunucunun X.509 sertifikası kullanılarak kimlik doğrulanır.

- Sunucu, hizmetteki belirli yöntemlere erişimi denetlemek için kullanabilir. <xref:System.ServiceModel.ServiceAuthorizationManager>

- Nasıl uygulanır. <xref:System.IdentityModel.Policy.IAuthorizationPolicy>

Hizmet, uygulama dosyası App.config kullanılarak tanımlanan hizmetle iletişim kurmak için iki uç noktayı ortaya çıkarır. Her bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur. Bir bağlama, WS-Security `wsHttpBinding` ve istemci kullanıcı adı kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır. Diğer bağlama WS-Security ve `wsHttpBinding` istemci sertifikası kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır. [ \<Davranış>,](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) kullanıcı kimlik bilgilerinin hizmet kimlik doğrulaması için kullanılacağını belirtir. Sunucu sertifikası, `SubjectName` `findValue` [ \<hizmetSertifikası>'ndeki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikile özellik için aynı değeri içermelidir.

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

Her istemci uç nokta yapılandırması bir yapılandırma adı, hizmet bitiş noktası için mutlak bir adres, bağlama ve sözleşme oluşur. İstemci bağlama, [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) bu durumda belirtildiği gibi uygun `clientCredentialType` güvenlik modu ile ve [ \<>iletide ](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)belirtildiği gibi yapılandırılır.

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

Kullanıcı adı tabanlı bitiş noktası için istemci uygulaması kullanılacak kullanıcı adını ve parolayı ayarlar.

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

Sertifika tabanlı bitiş noktası için istemci uygulaması istemci sertifikasını kullanacak şekilde ayarlar.

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

Bu örnek, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adlarını ve parolaları doğrulamak için özel bir kullanır. Örnek uygular `MyCustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilmiştir. Daha fazla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> bilgi için ilgili belgelere bakın. <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>Bu özel doğrulayıcı örnek, kullanıcı adının aşağıdaki kodda gösterildiği <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> parolayla eşleştiği kullanıcı adı/parola çiftlerini kabul etme yöntemini uygular.

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

Geçerlilik hizmeti kodunda uygulandıktan sonra, hizmet barındırıcısı kullanılacak geçerlilik örneği hakkında bilgilendirilmelidir. Bu, aşağıdaki kod kullanılarak yapılır:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Veya yapılandırmada aynı şeyi yapabilirsiniz:

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF), erişim denetimleri gerçekleştirmek için zengin bir talep tabanlı model sağlar. Nesne, <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimini gerçekleştirmek ve istemciyle ilişkili taleplerin hizmet yöntemine erişmek için gerekli gereksinimleri karşılayıp karşılamadığını belirlemek için kullanılır.

Bu örnek, gösteri amacıyla, kullanıcının, <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> adı verilmesine izin verilen işlemin Eylem URI değeri `http://example.com/claims/allowedoperation` olan tür iddialarına dayalı yöntemlere erişimini sağlayan yöntemi uygulayan bir uygulama gösterir.

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

Özel uygulama <xref:System.ServiceModel.ServiceAuthorizationManager> uygulandıktan sonra, hizmet ana bilgisayar <xref:System.ServiceModel.ServiceAuthorizationManager> kullanılacak hakkında bilgilendirilmelidir. Bu, aşağıdaki kodda gösterildiği gibi yapılır.

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Uygulanacak <xref:System.IdentityModel.Policy.IAuthorizationPolicy> birincil yöntem <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemdir.

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

Önceki kod, yöntemin <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> işlemi etkileyen yeni iddiaların eklenmediğini nasıl denetler ve belirli talepler ekler. İzin verilen talepler, kullanıcının `GetAllowedOpList` gerçekleştirmesine izin verilen belirli bir işlem listesini döndürmek için uygulanan yöntemden elde edilir. Yetkilendirme ilkesi, belirli bir işlem için talepler ekler. Bu daha sonra <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararları gerçekleştirmek için kullanılır.

Özel uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulandıktan sonra, hizmet ana bilgisayar kullanılacak yetkilendirme ilkeleri hakkında bilgilendirilmelidir.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci, Ekle, Çıkarma ve Çoklu yöntemleri başarıyla çağırır ve Böl yöntemini çağırmaya çalışırken "Erişim reddedildi" iletisi alır. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum Toplu Dosya

Bu örnekte yer alan Setup.bat toplu dosyası, sunucu sertifikası tabanlı güvenlik gerektiren kendi kendine barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.

Aşağıda, toplu iş dosyalarının uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için farklı bölümlerine kısa bir genel bakış sağlanacaktır:

- Sunucu sertifikası oluşturma.

    Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. %SERVER_NAME değişkeni sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Varsayılan değer yerel ana bilgisayardır.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.

    Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. Zaten istemci güvenilen bir kök sertifikası köklü bir sertifika varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- sunucu sertifikası ile istemci sertifika deposu doldurma bu adım gerekli değildir.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- İstemci sertifikasıoluşturma.

    Setup.bat toplu iş dosyasındaki aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur. %USER_NAME değişkeni sunucu adını belirtir. Bu değer "test1" olarak ayarlanır, çünkü `IAuthorizationPolicy` bu, aradığı addır. %USER_NAME değerini değiştirirseniz, `IAuthorizationPolicy.Evaluate` yöntemdeki karşılık gelen değeri değiştirmeniz gerekir.

    Sertifika, CurrentUser mağazasının altında Benim (Kişisel) mağazamda depolanır.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- İstemci sertifikasını sunucunun güvenilir sertifika deposuna yükleme.

    Setup.bat toplu iş dosyasındaki aşağıdaki satırlar istemci sertifikasını güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar sunucu sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. Zaten güvenilir bir kök sertifikaya dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- sunucu sertifikası deposunu istemci sertifikasıyla doldurma adımı gerekmez.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve oluşturmak için

1. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

2. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak için aşağıdaki yönergeleri kullanın.

> [!NOTE]
> Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yönetici ayrıcalıklarıyla Visual Studio için Geliştirici Komut Komut Ustem'i açın ve örnek yükleme klasöründen *Setup.bat* çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.

    > [!NOTE]
    > Setup.bat toplu dosyası Visual Studio için Geliştirici Komut Komut Istem'den çalıştırılacak şekilde tasarlanmıştır. Visual Studio için Geliştirici Komut İstemi'nde ayarlanan PATH ortamı değişkeni, *Setup.bat* komut dosyasının gerektirdiği yürütülebilir leri içeren dizine işaret eder.

1. Service.exe'yi *service\bin'den*başlat.

1. *\client\bin'den*Client.exe'yi başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.

İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.

### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlarda çalıştırmak için

1. Hizmet bilgisayarında bir dizin oluşturun.

2. Hizmet programı dosyalarını *\service\bin'den* hizmet bilgisayarındaki dizine kopyalayın. Ayrıca Setup.bat, Cleanup.bat, GetComputerName.vbs ve ImportClientCert.bat dosyalarını servis bilgisayarına kopyalayın.

3. İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.

4. İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.

5. Sunucuda, Yönetici `setup.bat service` ayrıcalıkları ile açılan Visual Studio için Geliştirici Komut Komut Ustem'de çalıştırın.

    Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını *Service.cer*adlı bir dosyaya aktarın. `service`

6. Bilgisayarın tam nitelikli alan adı ile aynı olan yeni `findValue` sertifika adını [ \<(serviceCertificate>'daki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde *Service.exe.config'i* edin. Ayrıca, hizmet>/\<baseAddresses> öğesindeki **bilgisayar adını** localhost'tan hizmet bilgisayarınızın tam nitelikli adına değiştirin. \<

7. *Service.cer* dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.

8. İstemci de, Yönetici ayrıcalıkları ile açılan Visual Studio için Geliştirici Komut Komut Ustem'de çalıştırın. `setup.bat client`

    Bağımsız değişkenle birlikte çalışmak `setup.bat` **test1** adında bir istemci sertifikası oluşturur ve istemci sertifikasını *Client.cer*adlı bir dosyaya aktarın. `client`

9. İstemci bilgisayarındaki *Client.exe.config* dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin. Bunu, **localhost'u** sunucunun tam nitelikli etki alanı adı ile değiştirerek yapın.

10. Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.

11. İstemci de, Yönetici ayrıcalıkları ile açılan Visual Studio için Geliştirici Komut Komut Ustem'de *ImportServiceCert.bat* çalıştırın.

    Bu, hizmet sertifikasını Service.cer dosyasından **CurrentUser - Trusted People** deposuna aktarabilir.

12. Sunucuda, Yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem'inde *ImportClientCert.bat* çalıştırın.

    Bu, istemci sertifikasını Client.cer dosyasından **LocalMachine - Trusted People** deposuna aktarın.

13. Sunucu bilgisayarında Service.exe komut istemi penceresinden başlatın.

14. İstemci bilgisayarında, komut istemi penceresinden Client.exe'yi başlatın.

    İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.

### <a name="clean-up-after-the-sample"></a>Örnekten sonra temizleme

Örnekten sonra temizlemek için, örneği çalıştırmayı bitirdiğinizde örnekler klasöründe *Cleanup.bat* çalıştırın. Bu, sunucu ve istemci sertifikalarını sertifika deposundan kaldırır.

> [!NOTE]
> Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlarda sertifika kullanan WCF örnekleri çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
