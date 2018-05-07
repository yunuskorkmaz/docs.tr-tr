---
title: Özel Belirteç
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 5850f97d6d3a66aacf82ab1cb2338240a75a00fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-token"></a>Özel Belirteç
Bu örnek bir Windows Communication Foundation (WCF) uygulamaya özel bir belirteç uygulamasını ekleneceği gösterilmektedir. Örnek kullanan bir `CreditCardToken` hizmete istemci kredi kartı bilgilerini güvenli bir şekilde geçirilecek. Belirteç WS güvenliği ileti üstbilgisinde geçirilir ve imzalanır ve ileti gövdesi ve diğer ileti üstbilgilerini yanı sıra simetrik güvenlik bağlama öğesi kullanılarak şifrelenir. Bu, burada yerleşik belirteçleri yetersiz olduğu durumlarda yararlıdır. Bu örnek, bir özel güvenlik belirteci yerleşik belirteçleri birini kullanmak yerine bir hizmet sağlamak üzere gösterilmiştir. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Özetlemek için bu örnek şunlar gösterilmektedir:  
  
-   Nasıl bir istemci bir hizmet için bir özel güvenlik belirteci geçirebilirsiniz.  
  
-   Nasıl hizmeti kullanmak ve bir özel güvenlik belirteci doğrulanamıyor.  
  
-   Nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] servis kodu özel güvenlik belirteci dahil olmak üzere alınan güvenlik belirteçleri hakkında bilgi edinebilirsiniz.  
  
-   Nasıl sunucu X.509 sertifikasının ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.  
  
## <a name="client-authentication-using-a-custom-security-token"></a>Bir özel güvenlik belirteci kullanarak istemci kimlik doğrulaması  
 Hizmet program aracılığıyla kullanılarak oluşturulan tek bir uç noktasını kullanıma sunar `BindingHelper` ve `EchoServiceHost` sınıfları. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Özel bağlama kullanma bağlama yapılandırılmış `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`. Bu örnek ayarlar `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtar korumak ve özel bir geçirmek için bir hizmetin X.509 sertifikası kullanmak üzere `CreditCardToken` imzalanmış ve şifrelenmiş güvenlik belirteci olarak WS-güvenlik ileti üstbilgisinde. Davranış istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında bilgi için kullanılacak olan hizmet kimlik bilgilerini belirtir.  
  
```  
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
  
 Bir kredi kartı kullanmak için iletide belirteci örnek özel hizmeti kimlik bilgileri bu işlevselliği sağlayacak şekilde kullanır. Hizmet kimlik bilgilerini sınıfı bulunan `CreditCardServiceCredentials` sınıfı ve hizmet konağı davranışları koleksiyonlarına eklenen `EchoServiceHost.InitializeRuntime` yöntemi.  
  
```  
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
  
 İstemci uç noktası hizmet uç noktası benzer bir şekilde yapılandırılır. İstemci aynı kullanır `BindingHelper` sınıfı bir bağlama oluşturun. Kurulumu geri kalanı bulunan `Client` sınıfı. İstemci ayrıca yer bilgilere ayarlar `CreditCardToken` ve hizmet X.509 sertifikası ekleyerek Kurulum kodu hakkında bilgi bir `CreditCardClientCredentials` uygun verileri istemci uç nokta davranışları koleksiyona örnekle. Örnek X.509 sertifikası konu adı ayarlamak kullanır. `CN=localhost` hizmet sertifikası.  
  
```  
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
  
// Create a client with given client endpoint configuration  
channelFactory =   
new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);  
  
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
 Bir özel güvenlik belirteci etkinleştirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bir nesne temsili özel güvenlik belirteci oluşturun. Bu gösterim örnek sahip `CreditCardToken` sınıfı. Nesne temsili tüm ilgili güvenlik belirteci bilgilerini tutan ve güvenlik belirtecinde yer alan güvenlik anahtarları listesini sağlamak üzere sorumludur. Bu durumda, kredi kartı güvenlik belirteci tüm güvenlik anahtarı içermiyor.  
  
 Ne kablo üzerinden iletilmesi özel bir belirteç etkinleştirmek için yapılır ve gerekir tarafından tüketilen sonraki bölümde açıklandığı bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası.  
  
```  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Özel kredi kartı için ve iletisi belirteci alma  
 Güvenlik belirteci serileştiricileri içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletisi XML'den güvenlik belirteçlerinin bir nesne temsili oluşturma ve güvenlik belirteçlerinin XML form oluşturma sorumludur. Aynı zamanda okuma ve yazma güvenlik belirteçleri işaret eden anahtar tanımlayıcıları gibi diğer işlevleri sorumlu olan, ancak bu örnek yalnızca güvenlik belirteci ile ilgili işlevleri kullanır. Özel bir etkinleştirmek için belirteç, kendi güvenlik belirteci seri hale getirici uygulamalıdır. Bu örnekte `CreditCardSecurityTokenSerializer` bu amaç için sınıf.  
  
 Hizmet özel seri hale getirici özel belirteç XML formunu okur ve özel belirteç nesne gösterimini oluşturur.  
  
 İstemci üzerindeki `CreditCardSecurityTokenSerializer` sınıfı XML yazıcıyı güvenlik belirteci nesne gösterimine içinde yer alan bilgileri yazar.  
  
```  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Belirteç sağlayıcısı ve belirteç kimlik doğrulayıcı sınıfları nasıl oluşturulur  
 İstemci ve hizmet kimlik bilgilerini güvenlik belirteci yöneticisi örneği sağlamaktan sorumludur. Güvenlik belirteci yöneticisi örneği belirteci sağlayıcıları, belirteç kimlik doğrulayan ve belirteç serileştiricileri almak için kullanılır.  
  
 Belirteç sağlayıcı istemci veya hizmet kimlik bilgilerini yer alan bilgileri temel alarak belirteci nesne gösterimini oluşturur. Belirteç nesne gösterimi (önceki bölümde tartışılan) belirteci seri hale getirici kullanarak ileti sonra yazılır.  
  
 Belirteç kimlik doğrulayıcı iletisi gelmesini belirteçlerini doğrular. Gelen belirteç nesne temsili belirteci seri hale getirici tarafından oluşturulur. Bu nesne temsili, daha sonra belirteç kimlik doğrulayıcı için doğrulama geçirilir. Belirteç başarıyla doğrulandıktan sonra belirteç kimlik doğrulayıcı koleksiyonunu döndürür `IAuthorizationPolicy` belirtecinde yer alan bilgileri temsil eden nesne. Bu bilgiler daha sonra ileti işleme sırasında yetkilendirme kararları gerçekleştirmek ve uygulama için talepler sağlamak için kullanılır. Bu örnekte, kredi kartı belirteç kimlik doğrulayıcı kullanan `CreditCardTokenAuthorizationPolicy` bu amaç için.  
  
 Belirteci seri hale getirici, belirtecin kablo gelen ve giden nesne gösterimini almak için sorumludur. Bu, önceki bölümde ele alınmıştır.  
  
 Bir kredi kartı belirteci yalnızca istemci hizmeti yönde iletmeye istiyoruz çünkü bu örnekte, bir belirteç sağlayıcısı yalnızca istemci ve bir belirteç kimlik doğrulayıcısı yalnızca hizmette üzerinde kullanıyoruz.  
  
 İstemci üzerinde işlevselliği bulunan `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` ve `CreditCardTokenProvider` sınıfları.  
  
 Hizmette işlevselliği bulunan `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` ve `CreditCardTokenAuthorizationPolicy` sınıfları.  
  
```  
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
  
## <a name="displaying-the-callers-information"></a>Arayanlar bilgileri görüntüleme  
 Arayanın bilgileri görüntülemek için kullanın `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki örnek kodda gösterildiği gibi. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir. Talep tarafından sağlanan `CreditCardToken` sınıfını kendi `AuthorizationPolicies` koleksiyonu.  
  
```  
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)  
{  
    claimValue = null;  
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType,  
        Rights.PossessProperty);  
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
                 return String.Format(  
                   "Credit card '{0}' issued by '{1}'",   
                   creditCardNumber, issuer);  
        }  
    }  
    return "Credit card is not known";  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren IIS tarafından barındırılan uygulamayı çalıştırmayı ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor:  
  
     Aşağıdaki satırları `Setup.bat` toplu iş dosyası kullanılması için sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki localhost varsayılandır. Değiştirirseniz `%SERVER_NAME%` değişken, Client.cs ve adını da dosyalarıyla gidin ve gerekir localhost tüm örneklerini Setup.bat komut dosyasında kullandığınız sunucu adı ile değiştirin.  
  
     Sertifika altında (Kişisel) My deposunda saklanır `LocalMachine` depolama konumu. Sertifika saklanır IIS tarafından barındırılan hizmetler için LocalMachine deposundaki. Kendini barındıran Hizmetleri için istemci sertifikası LocalMachine dize Currentuser'a ile değiştirerek Currentuser'a deposu konumda depolamak için toplu iş dosyasını değiştirmeniz gerekir.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   IIS barındırılan hizmeti sertifika özel anahtarına erişimi etkinleştirmek için IIS tarafından barındırılan işlemin altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir. Bu son adımda Setup.bat komut dosyası tarafından gerçekleştirilir.  
  
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
>  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] örnek yükleme klasöründen çalıştırma Setup.bat ve yönetici ayrıcalıkları ile komut istemi penceresi. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler. Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.  
  
> [!NOTE]
>  Örnekle bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
1.  Client.exe client\bin dizininden başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
2.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computer"></a>Bilgisayar örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet dizin hizmeti bilgisayarında hizmet program dosyalarını kopyalayın. CreditCardFile.txt kopyalamak unutmayın; Aksi takdirde kredi kartı Doğrulayıcı istemciden gönderilen kredi kartı bilgileri doğrulanamıyor. Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Değiştirirseniz Setup.bat kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` değişken hizmet barındırıldığı bilgisayarın tam adı. Visual Studio komut istemini yönetici ayrıcalıklarıyla açılmış içinde Setup.bat dosya çalıştırmanız gerektiğini unutmayın.  
  
4.  İstemci üzerinde Currentuser'a TrustedPeople deposuna sunucu sertifikasını kopyalayın. Yalnızca sunucu sertifikası güvenilir bir veren tarafından verilmemiş varsa bunu yapmanız gerekir.  
  
5.  EchoServiceHost.cs dosyasında localhost yerine bir tam bilgisayar adını belirtmek için sertifika konu adı değerini değiştirin.  
  
6.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
7.  Client.cs dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.  
  
8.  Client.cs dosyasında localhost yerine uzak ana bilgisayarın tam bilgisayar adı ile eşleşmesi için hizmet X.509 sertifikasının konu adını değiştirin.  
  
9. İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.  
  
10. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
