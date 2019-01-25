---
title: Özel Belirteç
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 93de9ae8d1d0604efbbc07fae61463599a8b9acf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572714"
---
# <a name="custom-token"></a>Özel Belirteç
Bu örnek, bir Windows Communication Foundation (WCF) uygulamasına özel bir belirteç uygulamasını ekleme gösterir. Örnekte bir `CreditCardToken` istemci kredi kartı bilgilerini güvenli bir şekilde hizmetine geçirilecek. Belirteç WS-güvenlik ileti üstbilgisinde imzalanır ve yanı sıra ileti gövdesi ve diğer ileti üstbilgileri simetrik güvenlik bağlama öğesi kullanılarak şifrelenir. Bu, yerleşik belirteçleri yeterli olmadığı durumlarda kullanışlıdır. Bu örnek, bir yerleşik belirteçlerin kullanmak yerine bir hizmete özel güvenlik belirteci gösterilmiştir. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.

> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

 Özetlemek gerekirse, bu örnek aşağıdaki gösterir:

-   Nasıl bir istemci bir hizmete bir özel güvenlik belirteci geçirebilirsiniz.

-   Nasıl hizmet kullanabilir ve bir özel güvenlik belirteci doğrulayın.

-   Nasıl WCF hizmet kodunun, özel güvenlik belirteci dahil olmak üzere alınan güvenlik belirteçleri hakkında bilgi edinebilirsiniz.

-   Sunucu X.509 sertifikasının nasıl ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.

## <a name="client-authentication-using-a-custom-security-token"></a>Özel güvenlik belirteci kullanılarak istemci kimlik doğrulaması
 Hizmeti kullanarak program aracılığıyla oluşturulan tek bir uç noktasını kullanıma sunar `BindingHelper` ve `EchoServiceHost` sınıfları. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Özel bağlama kullanma yapılandırılmış bağlama `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`. Bu örnek ayarlar `SymmetricSecurityBindingElement` simetrik anahtar aktarım sırasında korumak ve özel bir geçirmek için bir hizmetin X.509 sertifikası kullanılacak `CreditCardToken` WS-güvenlik ileti üstbilgisinde bir imzalanmış ve şifrelenmiş güvenlik belirteci olarak. Davranış, istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında daha fazla bilgi için kullanılacak hizmet kimlik bilgilerini belirtir.

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        SymmetricSecurityBindingElement messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 Kredi kartı kullanmak için iletide, belirteç örnek özel hizmet kimlik bilgilerini bu işlevselliği sağlayacak şekilde kullanır. Hizmet kimlik bilgilerini sınıfı bulunan `CreditCardServiceCredentials` sınıfı ve davranışları koleksiyonlarına hizmet ana bilgisayar eklenir `EchoServiceHost.InitializeRuntime` yöntemi.

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 İstemci uç noktası benzer şekilde, hizmet uç noktası olarak yapılandırılır. Aynı istemcinin kullandığı `BindingHelper` bağlama oluşturmak için sınıf. Kurulumu geri kalanını bulunan `Client` sınıfı. İstemci ayrıca içindeki bilgilere ayarlar `CreditCardToken` ve hizmet X.509 sertifikasını ekleyerek Kurulum kodu hakkında bilgi bir `CreditCardClientCredentials` istemci uç nokta davranışları koleksiyona uygun veri örneği. Örnek X.509 sertifikası konu adı ayarlamak kullanır. `CN=localhost` hizmet sertifikası olarak.

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// configure the credit card credentials on the channel factory
CreditCardClientCredentials credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// configure the service certificate on the credentials
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// replace ClientCredentials with CreditCardClientCredentials
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine("Echo service returned: {0}", client.Echo());

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a>Özel güvenlik belirteci uygulama
 Bir özel güvenlik belirteci WCF etkinleştirmek için bir nesne temsili özel güvenlik belirteci oluşturun. Bu gösterim örneği sahip `CreditCardToken` sınıfı. Tüm ilgili güvenlik belirteci bilgilerini tutan ve güvenlik anahtarları güvenlik belirtecinde yer alan bir listesini sağlamak üzere bir nesne temsili sorumludur. Bu durumda, kredi kartı güvenlik belirteci, tüm güvenlik anahtarı içermiyor.

 Sonraki bölümde, ne olmalı kablo üzerinden iletilmesi için özel bir belirteç etkinleştirmek için yapılır ve bir WCF uç noktası tarafından kullanılan açıklar.

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException("cardInfo");

        if (id == null)
            throw new ArgumentNullException("id");

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Özel bir kredi kartı ileti gelen ve giden belirteci alma
 Wcf'de güvenlik belirteci serileştiricileri XML iletisi bir nesne temsili güvenlik belirteçleri oluşturma ve güvenlik belirteçlerini XML biçiminin oluşturarak sorumludur. Ayrıca güvenlik belirteçleri işaret eden anahtarı tanımlayıcıları yazma ve okuma gibi diğer işlevleri sorumlu olduğu, ancak bu örnek yalnızca güvenlik belirteci ile ilgili işlevleri kullanır. Özel bir etkinleştirme belirteci kendi güvenlik belirteci serileştiriciye uygulamanız gerekir. Bu örnekte `CreditCardSecurityTokenSerializer` bu amaç için sınıf.

 Hizmet özel seri hale getirici XML biçimi özel belirteç okur ve özel belirteç nesne gösterimini oluşturur.

 İstemci üzerindeki `CreditCardSecurityTokenSerializer` sınıfı XML yazıcısı güvenlik belirteci nesne gösterimine içinde yer alan bilgileri yazar.

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            CreditCardInfo cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;

        else
            return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null) { throw new ArgumentNullException("writer"); }
        if (token == null) { throw new ArgumentNullException("token"); }

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Belirteç sağlayıcısı ve belirteç kimlik doğrulayıcısı sınıfları nasıl oluşturulur
 Hizmet ve istemci kimlik bilgileri güvenlik belirteci yöneticisi örneği sağlamaktan sorumludur. Güvenlik belirteci yöneticisi örneği belirteci sağlayıcıları, belirteç Doğrulayıcı ve belirteci seri hale getiricileri genişletme almak için kullanılır.

 Belirteç sağlayıcısı, belirteç istemci veya hizmet kimlik bilgilerini yer alan bilgiler temel nesne temsilini oluşturur. Belirteç nesnesi gösterimi ardından iletiyi belirteç serializer özelliği (önceki bölümde anlatılmaktadır) kullanarak yazılır.

 Belirteç kimlik doğrulayıcısı iletisinde gelen belirteçlerini doğrular. Gelen belirteci bir nesne temsili belirteci seri hale getirici tarafından oluşturulur. Bu nesne temsili, ardından belirteci kimlik doğrulayıcı için doğrulama için geçirilir. Belirteç başarıyla doğrulandıktan sonra belirteç kimlik doğrulayıcısı koleksiyonunu döndürür. `IAuthorizationPolicy` belirtecinde yer alan bilgileri temsil eden nesneleri. Bu bilgiler daha sonra ileti işleme sırasında yetkilendirme kararları gerçekleştirmek ve uygulama için talep sağlamak için kullanılır. Bu örnekte, kredi kartı belirteci kimlik doğrulayıcı kullanan `CreditCardTokenAuthorizationPolicy` bu amaç için.

 Belirteç serializer özelliği, belirtecin kablo gelen ve giden bir nesne temsili almak için sorumludur. Bu, önceki bölümde ele alınmıştır.

 Yalnızca istemci hizmeti yönde bir kredi kartı belirteç aktarmaya istediğimizden Bu örnekte, bir belirteç sağlayıcısı istemci ve hizmet üzerinde yalnızca bir belirteç kimlik doğrulayıcısı kullanırız.

 İstemci işlevselliği bulunan `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` ve `CreditCardTokenProvider` sınıfları.

 İşlevi hizmette yer `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` ve `CreditCardTokenAuthorizationPolicy` sınıfları.

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException("creditCardInfo");

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // handle this token for Custom
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // return server cert
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
            {
                throw new ArgumentNullException("creditCardInfo");
            }
            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException("creditCardFile");

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            DefaultClaimSet cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            DefaultClaimSet cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (StreamReader myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException("issuedClaims");
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a>Çağıranlar bilgileri görüntüleme
 Arayanın bilgileri görüntülemek için kullanın `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki örnek kodda gösterildiği gibi. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir. Talepleri tarafından sağlanan `CreditCardToken` sınıfını kendi `AuthorizationPolicies` koleksiyonu.

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren IIS tarafından barındırılan uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.

-   Sunucu sertifikası oluşturuluyor:

     Aşağıdaki satırları gelen `Setup.bat` toplu iş dosyası kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasında localhost varsayılandır. Değiştirirseniz `%SERVER_NAME%` değişken Client.cs ve adını da dosyalara gidin ve gerekir localhost tüm örneklerini Setup.bat betikte kullandığınız sunucu adı ile değiştirin.

     Sertifika altında (Kişisel) My deposunda saklanır `LocalMachine` depolama konumu. Depolanmış bir sertifikayla IIS tarafından barındırılan hizmetleri LocalMachine deposunda. Şirket içinde barındırılan hizmetler için istemci sertifikası LocalMachine dize CurrentUser ile değiştirerek CurrentUser deposu konumda depolamak için toplu iş dosyasını değiştirmeniz gerekir.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   IIS barındırılan hizmeti için sertifika özel anahtar erişimi etkinleştirmek için IIS tarafından barındırılan işlem altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir. Bu, son adımda Setup.bat betiği tarafından gerçekleştirilir.

    ```
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.

#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1.  Yönetici ayrıcalıklarına sahip bir Visual Studio 2012 komut istemi penceresi açın ve örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler. Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.

> [!NOTE]
>  Sertifikaları örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak kaldırmayı unutmayın. Diğer güvenlik örnekleri aynı sertifikalarını kullanın.  
  
1.  Client.exe client\bin dizinden başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
2.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computer"></a>Bilgisayar arasında örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet dizini hizmeti bilgisayarında hizmet program dosyaları kopyalayın. CreditCardFile.txt kopyalamak unutmayın; Aksi takdirde kredi kartı authenticator istemciden gönderilen kredi kartı bilgileri doğrulanamıyor. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Setup.bat değiştirirseniz kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` değişkenini hizmetin barındırıldığı bilgisayarın tam adı. Setup.bat dosyasının Visual Studio için geliştirici komut isteminden çalıştırılmalıdır Not yönetici ayrıcalıklarıyla açılan.  
  
4.  Sunucu sertifikası istemci CurrentUser TrustedPeople deponuzu kopyalayın. Yalnızca sunucu sertifikası güvenilir bir veren tarafından yazılmazsa bunu yapmanız gerekir.  
  
5.  EchoServiceHost.cs dosyasında localhost yerine tam bilgisayar adını belirtmek için sertifika konu adı değerini değiştirin.  
  
6.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.  
  
7.  Client.cs dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
8.  Client.cs dosyasında localhost yerine uzak ana bilgisayar tam olarak nitelenmiş adını eşleştirmek için hizmet X.509 sertifikasının konu adı değiştirin.  
  
9. İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.  
  
10. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1.  Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.
