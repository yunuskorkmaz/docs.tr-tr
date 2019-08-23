---
title: Özel Belirteç
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 7203b55b01f51851fa94fedc4950a05343b792bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953572"
---
# <a name="custom-token"></a>Özel Belirteç
Bu örnek, bir Windows Communication Foundation (WCF) uygulamasına özel bir belirteç uygulamasının nasıl ekleneceğini gösterir. Örnek, istemci kredi `CreditCardToken` kartlarıyla ilgili bilgileri hizmete güvenli bir şekilde geçirmek için bir kullanır. Belirteç WS-Security İleti üstbilgisine geçirilir ve simetrik güvenlik bağlama öğesi ve ileti gövdesi ve diğer ileti üst bilgileri kullanılarak imzalanır ve şifrelenir. Bu, yerleşik belirteçlerin yeterli olmadığı durumlarda faydalıdır. Bu örnek, yerleşik belirteçlerden birini kullanmak yerine bir hizmete nasıl özel bir güvenlik belirteci sağlayabileceğinizi gösterir. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Özetlemek gerekirse, bu örnek şunları gösterir:

- Bir istemcinin bir hizmete özel bir güvenlik belirteci nasıl geçirebilirler.

- Hizmetin özel bir güvenlik belirtecini tüketme ve doğrulayabileceği.

- WCF hizmet kodu, özel güvenlik belirteci dahil olmak üzere alınan güvenlik belirteçleri hakkındaki bilgileri nasıl elde edebilir.

- Sunucu X. 509.440 sertifikası ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.

## <a name="client-authentication-using-a-custom-security-token"></a>Özel bir güvenlik belirteci kullanarak istemci kimlik doğrulaması
 Hizmet, ve `BindingHelper` `EchoServiceHost` sınıfları kullanılarak programlı bir şekilde oluşturulan tek bir uç noktayı kullanıma sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, ve `SymmetricSecurityBindingElement` `HttpTransportBindingElement`kullanarak özel bir bağlama ile yapılandırılır. Bu örnek, `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtarı korumak ve bir WS-Security ileti üst bilgisinde imzalanmış ve şifreli bir güvenlik belirteci olarak özel `CreditCardToken` bir geçiş yapmak için bir hizmetin X. 509.440 sertifikası kullanmak üzere öğesini ayarlar. Davranış, istemci kimlik doğrulaması için kullanılacak hizmet kimlik bilgilerini ve ayrıca Service X. 509.440 sertifikası hakkındaki bilgileri belirtir.

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

 İletide bir kredi kartı belirtecini kullanmak için örnek, bu işlevselliği sağlamak için özel hizmet kimlik bilgilerini kullanır. Hizmet kimlik bilgileri sınıfı `CreditCardServiceCredentials` sınıfında bulunur ve `EchoServiceHost.InitializeRuntime` yöntemindeki hizmet ana bilgisayarının davranış koleksiyonlarına eklenir.

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

 İstemci uç noktası, hizmet uç noktası gibi benzer şekilde yapılandırılır. İstemci, bir bağlama oluşturmak `BindingHelper` için aynı sınıfı kullanır. Kurulumun geri kalanı `Client` sınıfında bulunur. İstemci Ayrıca, `CreditCardToken` istemci uç noktası davranışları koleksiyonuna doğru verilerle bir `CreditCardClientCredentials` örnek ekleyerek kurulum kodundaki Service X. 509.440 sertifikası hakkındaki bilgileri ve bilgileri de içerir. Örnek, hizmet sertifikası `CN=localhost` olarak olarak ayarlanan konu adına sahip X. 509.440 sertifikasını kullanır.

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
 WCF 'de özel bir güvenlik belirtecini etkinleştirmek için özel güvenlik belirtecinin nesne temsilini oluşturun. Örnek, `CreditCardToken` sınıfında bu gösterimine sahiptir. Nesne gösterimi, tüm ilgili güvenlik belirteci bilgilerinin tutulması ve güvenlik belirtecinde bulunan güvenlik anahtarlarının bir listesini sağlamak için sorumludur. Bu durumda, kredi kartı güvenlik belirteci herhangi bir güvenlik anahtarı içermez.

 Sonraki bölümde, özel bir belirtecin kablo üzerinden aktarılmasını ve bir WCF uç noktası tarafından kullanılabilmesini sağlamak için ne yapılması gerektiğini açıklanmaktadır.

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Iletiye/bilgisayardan özel kredi kartı belirteci alınıyor
 WCF 'deki güvenlik belirteci serileştiricileri, iletideki XML 'den güvenlik belirteçlerinin bir nesne gösterimini oluşturmaktan ve güvenlik belirteçlerinin XML biçiminde oluşturulmasından sorumludur. Bunlar ayrıca güvenlik belirteçlerini gösteren anahtar tanımlayıcılarını okuma ve yazma gibi diğer işlevlerden sorumludur, ancak bu örnek yalnızca güvenlik belirteci ile ilgili işlevselliği kullanır. Özel bir belirteci etkinleştirmek için kendi güvenlik belirteci serileştiriciyi uygulamanız gerekir. Bu örnek, `CreditCardSecurityTokenSerializer` bu amaçla sınıfını kullanır.

 Hizmette, özel seri hale getirici özel belirtecin XML formunu okur ve bundan özel belirteç nesnesi temsilini oluşturur.

 İstemcisinde, `CreditCardSecurityTokenSerializer` sınıfı güvenlik belirteci Nesne temsilinde yer alan bilgileri XML yazıcısına yazar.

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Belirteç sağlayıcısı ve belirteç Authenticator sınıfları oluşturma
 İstemci ve hizmet kimlik bilgileri, güvenlik belirteci Yöneticisi örneğini sağlamaktan sorumludur. Güvenlik belirteci Yöneticisi örneği, belirteç sağlayıcılarını, belirteç kimlik doğrulayıcılar ve belirteç serileştiricileri almak için kullanılır.

 Belirteç sağlayıcısı, istemci veya hizmet kimlik bilgileriyle bulunan bilgilere göre belirtecin nesne temsilini oluşturur. Belirteç nesnesi temsili daha sonra belirteç seri hale getirme kullanılarak iletiye yazılır (önceki bölümde ele alınmıştır).

 Belirteç kimlik doğrulayıcısı iletiye ulaşan belirteçleri doğrular. Gelen belirteç nesnesi temsili, belirteç seri hale getirici tarafından oluşturulur. Bu nesne temsili daha sonra doğrulama için belirteç kimlik doğrulayıcısı 'na geçirilir. Belirteç başarılı bir şekilde doğrulandıktan sonra, belirteç kimlik doğrulayıcısı, belirteçte bulunan bilgileri `IAuthorizationPolicy` temsil eden nesnelerin bir koleksiyonunu döndürür. Bu bilgiler, yetkilendirme kararlarını gerçekleştirmek ve uygulama için talepler sağlamak üzere ileti işleme sırasında daha sonra kullanılır. Bu örnekte, kredi kartı belirteç kimlik doğrulayıcısı bu amaçla `CreditCardTokenAuthorizationPolicy` kullanılır.

 Belirteç seri hale getiricisi, belirtecin nesne gösterimini, hatta ve tel 'dan almak sorumludur. Bu, önceki bölümde ele alınmıştır.

 Bu örnekte, yalnızca istemciden hizmete yönünde bir kredi kartı belirteci aktarmak istediğimiz için, yalnızca istemcide bir belirteç sağlayıcısı ve yalnızca bir belirteç kimlik doğrulayıcısı kullanıyoruz.

 İstemcideki işlevsellik `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` ve `CreditCardTokenProvider` sınıflarında bulunur.

 Hizmette, `CreditCardServiceCredentials`işlevleri, `CreditCardTokenAuthenticator` ve `CreditCardServiceCredentialsSecurityTokenManager` sınıflarındabulunur.`CreditCardTokenAuthorizationPolicy`

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

## <a name="displaying-the-callers-information"></a>Arayanların bilgilerini görüntüleme
 Arayanın bilgilerini göstermek için aşağıdaki örnek kodda gösterildiği `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` gibi kullanın. Geçerli çağıran ile ilişkili yetkilendirme taleplerini içerir.`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Talepler, `CreditCardToken` `AuthorizationPolicies` koleksiyonunda sınıfı tarafından sağlanır.

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

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu
 Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren IIS tarafından barındırılan uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.

- Sunucu sertifikası oluşturuluyor:

     `Setup.bat` Toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%` Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki varsayılan değer localhost 'tur. `%SERVER_NAME%` Değişkeni değiştirirseniz, Client.cs ve Service.cs dosyalarını ziyaret etmeniz ve tüm localhost örneklerini Setup. bat komut dosyasında kullandığınız sunucu adı ile değiştirmeniz gerekir.

     Sertifika, `LocalMachine` depolama konumu altında (kişisel) deposunda depolanır. Sertifika, IIS tarafından barındırılan hizmetler için LocalMachine deposunda depolanır. Şirket içinde barındırılan hizmetler için, LocalMachine dizesini CurrentUser ile değiştirerek, istemci sertifikasını geçerli kullanıcı deposu konumunda depolayacak şekilde toplu iş dosyasını değiştirmelisiniz.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:

     Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- IIS tarafından barındırılan hizmetten sertifika özel anahtarına erişimi etkinleştirmek için, IIS tarafından barındırılan işlemin çalıştığı kullanıcı hesabına özel anahtar için uygun izinler verilmelidir. Bu, Setup. bat betiğinin son adımları tarafından gerçekleştirilir.

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
> Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.

#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yönetici ayrıcalıklarıyla bir Visual Studio 2012 komut Istemi penceresi açın ve örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar. Yolun, MakeCert. exe ' nin bulunduğu klasörü içerdiğinden emin olun.

> [!NOTE]
> Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırmayı unutmayın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
1. Client\bin dizininden Client. exe ' yi başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
2. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computer"></a>Örneği bilgisayar genelinde çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın. CreditCardFile. txt dosyasını kopyalamayı unutmayın. Aksi takdirde, kredi kartı kimlik doğrulayıcısı istemciden gönderilen kredi kartı bilgilerini doğrulayamaz. Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.  
  
3. Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir. `%SERVER_NAME%` Değişkeni, hizmetin barındırıldığı bilgisayarın tam adı olarak değiştirirseniz Setup. bat kullanarak bir tane oluşturabilirsiniz. Setup. bat dosyasının, yönetici ayrıcalıklarıyla açılan bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın.  
  
4. Sunucu sertifikasını istemcideki CurrentUser-Trustedkişiler deposuna kopyalayın. Bunu yalnızca, sunucu sertifikası güvenilen bir veren tarafından verilmediği takdirde yapmanız gerekir.  
  
5. EchoServiceHost.cs dosyasında, sertifika konu adının değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.  
  
6. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.  
  
7. Client.cs dosyasında, bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
8. Client.cs dosyasında, Service X. 509.952 sertifikasının konu adını localhost yerine uzak konağın tam bilgisayar adıyla eşleşecek şekilde değiştirin.  
  
9. İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın.  
  
10. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
