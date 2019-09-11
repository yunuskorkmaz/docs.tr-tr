---
title: Özel Belirteç
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: c3c6cfd9d1742f7e839d7b40220792ba455d7673
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855515"
---
# <a name="custom-token"></a><span data-ttu-id="baa13-102">Özel Belirteç</span><span class="sxs-lookup"><span data-stu-id="baa13-102">Custom Token</span></span>

<span data-ttu-id="baa13-103">Bu örnek, bir Windows Communication Foundation (WCF) uygulamasına özel bir belirteç uygulamasının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="baa13-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="baa13-104">Örnek, istemci kredi `CreditCardToken` kartlarıyla ilgili bilgileri hizmete güvenli bir şekilde geçirmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="baa13-105">Belirteç WS-Security İleti üstbilgisine geçirilir ve simetrik güvenlik bağlama öğesi ve ileti gövdesi ve diğer ileti üst bilgileri kullanılarak imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="baa13-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="baa13-106">Bu, yerleşik belirteçlerin yeterli olmadığı durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="baa13-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="baa13-107">Bu örnek, yerleşik belirteçlerden birini kullanmak yerine bir hizmete nasıl özel bir güvenlik belirteci sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="baa13-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="baa13-108">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="baa13-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="baa13-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="baa13-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="baa13-110">Özetlemek gerekirse, bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="baa13-110">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="baa13-111">Bir istemcinin bir hizmete özel bir güvenlik belirteci nasıl geçirebilirler.</span><span class="sxs-lookup"><span data-stu-id="baa13-111">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="baa13-112">Hizmetin özel bir güvenlik belirtecini tüketme ve doğrulayabileceği.</span><span class="sxs-lookup"><span data-stu-id="baa13-112">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="baa13-113">WCF hizmet kodu, özel güvenlik belirteci dahil olmak üzere alınan güvenlik belirteçleri hakkındaki bilgileri nasıl elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="baa13-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="baa13-114">Sunucu X. 509.440 sertifikası ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baa13-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="baa13-115">Özel bir güvenlik belirteci kullanarak istemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="baa13-115">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="baa13-116">Hizmet, ve `BindingHelper` `EchoServiceHost` sınıfları kullanılarak programlı bir şekilde oluşturulan tek bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="baa13-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="baa13-117">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="baa13-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="baa13-118">Bağlama, ve `SymmetricSecurityBindingElement` `HttpTransportBindingElement`kullanarak özel bir bağlama ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="baa13-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="baa13-119">Bu örnek, `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtarı korumak ve bir WS-Security ileti üst bilgisinde imzalanmış ve şifreli bir güvenlik belirteci olarak özel `CreditCardToken` bir geçiş yapmak için bir hizmetin X. 509.440 sertifikası kullanmak üzere öğesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="baa13-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="baa13-120">Davranış, istemci kimlik doğrulaması için kullanılacak hizmet kimlik bilgilerini ve ayrıca Service X. 509.440 sertifikası hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="baa13-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 <span data-ttu-id="baa13-121">İletide bir kredi kartı belirtecini kullanmak için örnek, bu işlevselliği sağlamak için özel hizmet kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="baa13-122">Hizmet kimlik bilgileri sınıfı `CreditCardServiceCredentials` sınıfında bulunur ve `EchoServiceHost.InitializeRuntime` yöntemindeki hizmet ana bilgisayarının davranış koleksiyonlarına eklenir.</span><span class="sxs-lookup"><span data-stu-id="baa13-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

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

 <span data-ttu-id="baa13-123">İstemci uç noktası, hizmet uç noktası gibi benzer şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="baa13-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="baa13-124">İstemci, bir bağlama oluşturmak `BindingHelper` için aynı sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="baa13-125">Kurulumun geri kalanı `Client` sınıfında bulunur.</span><span class="sxs-lookup"><span data-stu-id="baa13-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="baa13-126">İstemci Ayrıca, `CreditCardToken` istemci uç noktası davranışları koleksiyonuna doğru verilerle bir `CreditCardClientCredentials` örnek ekleyerek kurulum kodundaki Service X. 509.440 sertifikası hakkındaki bilgileri ve bilgileri de içerir.</span><span class="sxs-lookup"><span data-stu-id="baa13-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="baa13-127">Örnek, hizmet sertifikası `CN=localhost` olarak olarak ayarlanan konu adına sahip X. 509.440 sertifikasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a><span data-ttu-id="baa13-128">Özel güvenlik belirteci uygulama</span><span class="sxs-lookup"><span data-stu-id="baa13-128">Custom Security Token Implementation</span></span>

 <span data-ttu-id="baa13-129">WCF 'de özel bir güvenlik belirtecini etkinleştirmek için özel güvenlik belirtecinin nesne temsilini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="baa13-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="baa13-130">Örnek, `CreditCardToken` sınıfında bu gösterimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="baa13-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="baa13-131">Nesne gösterimi, tüm ilgili güvenlik belirteci bilgilerinin tutulması ve güvenlik belirtecinde bulunan güvenlik anahtarlarının bir listesini sağlamak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="baa13-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="baa13-132">Bu durumda, kredi kartı güvenlik belirteci herhangi bir güvenlik anahtarı içermez.</span><span class="sxs-lookup"><span data-stu-id="baa13-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="baa13-133">Sonraki bölümde, özel bir belirtecin kablo üzerinden aktarılmasını ve bir WCF uç noktası tarafından kullanılabilmesini sağlamak için ne yapılması gerektiğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="baa13-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

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
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="baa13-134">Iletiye/bilgisayardan özel kredi kartı belirteci alınıyor</span><span class="sxs-lookup"><span data-stu-id="baa13-134">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="baa13-135">WCF 'deki güvenlik belirteci serileştiricileri, iletideki XML 'den güvenlik belirteçlerinin bir nesne gösterimini oluşturmaktan ve güvenlik belirteçlerinin XML biçiminde oluşturulmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="baa13-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="baa13-136">Bunlar ayrıca güvenlik belirteçlerini gösteren anahtar tanımlayıcılarını okuma ve yazma gibi diğer işlevlerden sorumludur, ancak bu örnek yalnızca güvenlik belirteci ile ilgili işlevselliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="baa13-137">Özel bir belirteci etkinleştirmek için kendi güvenlik belirteci serileştiriciyi uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="baa13-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="baa13-138">Bu örnek, `CreditCardSecurityTokenSerializer` bu amaçla sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="baa13-139">Hizmette, özel seri hale getirici özel belirtecin XML formunu okur ve bundan özel belirteç nesnesi temsilini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baa13-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="baa13-140">İstemcisinde, `CreditCardSecurityTokenSerializer` sınıfı güvenlik belirteci Nesne temsilinde yer alan bilgileri XML yazıcısına yazar.</span><span class="sxs-lookup"><span data-stu-id="baa13-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

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

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

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
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="baa13-141">Belirteç sağlayıcısı ve belirteç Authenticator sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="baa13-141">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="baa13-142">İstemci ve hizmet kimlik bilgileri, güvenlik belirteci Yöneticisi örneğini sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="baa13-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="baa13-143">Güvenlik belirteci Yöneticisi örneği, belirteç sağlayıcılarını, belirteç kimlik doğrulayıcılar ve belirteç serileştiricileri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baa13-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="baa13-144">Belirteç sağlayıcısı, istemci veya hizmet kimlik bilgileriyle bulunan bilgilere göre belirtecin nesne temsilini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baa13-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="baa13-145">Belirteç nesnesi temsili daha sonra belirteç seri hale getirme kullanılarak iletiye yazılır (önceki bölümde ele alınmıştır).</span><span class="sxs-lookup"><span data-stu-id="baa13-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="baa13-146">Belirteç kimlik doğrulayıcısı iletiye ulaşan belirteçleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="baa13-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="baa13-147">Gelen belirteç nesnesi temsili, belirteç seri hale getirici tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baa13-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="baa13-148">Bu nesne temsili daha sonra doğrulama için belirteç kimlik doğrulayıcısı 'na geçirilir.</span><span class="sxs-lookup"><span data-stu-id="baa13-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="baa13-149">Belirteç başarılı bir şekilde doğrulandıktan sonra, belirteç kimlik doğrulayıcısı, belirteçte bulunan bilgileri `IAuthorizationPolicy` temsil eden nesnelerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="baa13-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="baa13-150">Bu bilgiler, yetkilendirme kararlarını gerçekleştirmek ve uygulama için talepler sağlamak üzere ileti işleme sırasında daha sonra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baa13-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="baa13-151">Bu örnekte, kredi kartı belirteç kimlik doğrulayıcısı bu amaçla `CreditCardTokenAuthorizationPolicy` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baa13-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="baa13-152">Belirteç seri hale getiricisi, belirtecin nesne gösterimini, hatta ve tel 'dan almak sorumludur.</span><span class="sxs-lookup"><span data-stu-id="baa13-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="baa13-153">Bu, önceki bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="baa13-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="baa13-154">Bu örnekte, yalnızca istemciden hizmete yönünde bir kredi kartı belirteci aktarmak istediğimiz için, yalnızca istemcide bir belirteç sağlayıcısı ve yalnızca bir belirteç kimlik doğrulayıcısı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="baa13-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="baa13-155">İstemcideki işlevsellik `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` ve `CreditCardTokenProvider` sınıflarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="baa13-155">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="baa13-156">Hizmette, `CreditCardServiceCredentials`işlevleri, `CreditCardTokenAuthenticator` ve `CreditCardServiceCredentialsSecurityTokenManager` sınıflarındabulunur.`CreditCardTokenAuthorizationPolicy`</span><span class="sxs-lookup"><span data-stu-id="baa13-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

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
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
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
                throw new ArgumentNullException(nameof(creditCardInfo));

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
                throw new ArgumentNullException(nameof(creditCardFile));

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
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
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
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
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
                throw new ArgumentNullException(nameof(issuedClaims));
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

## <a name="displaying-the-callers-information"></a><span data-ttu-id="baa13-157">Arayanların bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="baa13-157">Displaying the Callers' Information</span></span>

 <span data-ttu-id="baa13-158">Arayanın bilgilerini göstermek için aşağıdaki örnek kodda gösterildiği `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="baa13-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="baa13-159">Geçerli çağıran ile ilişkili yetkilendirme taleplerini içerir.`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`</span><span class="sxs-lookup"><span data-stu-id="baa13-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="baa13-160">Talepler, `CreditCardToken` `AuthorizationPolicies` koleksiyonunda sınıfı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

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

 <span data-ttu-id="baa13-161">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="baa13-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="baa13-162">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="baa13-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="baa13-163">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="baa13-163">Setup Batch File</span></span>

 <span data-ttu-id="baa13-164">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren IIS tarafından barındırılan uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="baa13-165">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="baa13-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="baa13-166">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="baa13-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="baa13-167">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="baa13-167">Creating the server certificate:</span></span>

     <span data-ttu-id="baa13-168">`Setup.bat` Toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baa13-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="baa13-169">`%SERVER_NAME%` Değişken, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="baa13-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="baa13-170">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="baa13-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="baa13-171">Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="baa13-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="baa13-172">`%SERVER_NAME%` Değişkeni değiştirirseniz, Client.cs ve Service.cs dosyalarını ziyaret etmeniz ve tüm localhost örneklerini Setup. bat komut dosyasında kullandığınız sunucu adı ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="baa13-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="baa13-173">Sertifika, `LocalMachine` depolama konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="baa13-174">Sertifika, IIS tarafından barındırılan hizmetler için LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="baa13-175">Şirket içinde barındırılan hizmetler için, LocalMachine dizesini CurrentUser ile değiştirerek, istemci sertifikasını geçerli kullanıcı deposu konumunda depolayacak şekilde toplu iş dosyasını değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="baa13-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="baa13-176">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="baa13-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="baa13-177">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="baa13-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="baa13-178">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="baa13-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="baa13-179">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="baa13-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="baa13-180">IIS tarafından barındırılan hizmetten sertifika özel anahtarına erişimi etkinleştirmek için, IIS tarafından barındırılan işlemin çalıştığı kullanıcı hesabına özel anahtar için uygun izinler verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="baa13-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="baa13-181">Bu, Setup. bat betiğinin son adımları tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="baa13-181">This is accomplished by last steps in the Setup.bat script.</span></span>

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
> <span data-ttu-id="baa13-182">Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="baa13-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="baa13-183">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="baa13-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="baa13-184">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="baa13-184">To set up and build the sample</span></span>

1. <span data-ttu-id="baa13-185">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="baa13-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="baa13-186">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="baa13-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="baa13-187">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="baa13-187">To run the sample on the same computer</span></span>

1. <span data-ttu-id="baa13-188">Yönetici ayrıcalıklarıyla bir Visual Studio 2012 komut Istemi penceresi açın ve örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="baa13-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="baa13-189">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar. Yolun, MakeCert. exe ' nin bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="baa13-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="baa13-190">Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="baa13-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="baa13-191">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="baa13-191">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="baa13-192">Client\bin dizininden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="baa13-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="baa13-193">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="baa13-193">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="baa13-194">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="baa13-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="baa13-195">Örneği bilgisayar genelinde çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="baa13-195">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="baa13-196">Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="baa13-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="baa13-197">Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="baa13-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="baa13-198">CreditCardFile. txt dosyasını kopyalamayı unutmayın. Aksi takdirde, kredi kartı kimlik doğrulayıcısı istemciden gönderilen kredi kartı bilgilerini doğrulayamaz.</span><span class="sxs-lookup"><span data-stu-id="baa13-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="baa13-199">Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="baa13-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="baa13-200">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="baa13-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="baa13-201">`%SERVER_NAME%` Değişkeni, hizmetin barındırıldığı bilgisayarın tam adı olarak değiştirirseniz Setup. bat kullanarak bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baa13-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="baa13-202">Setup. bat dosyasının, yönetici ayrıcalıklarıyla açılan bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="baa13-202">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="baa13-203">Sunucu sertifikasını istemcideki CurrentUser-Trustedkişiler deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="baa13-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="baa13-204">Bunu yalnızca, sunucu sertifikası güvenilen bir veren tarafından verilmediği takdirde yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="baa13-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="baa13-205">EchoServiceHost.cs dosyasında, sertifika konu adının değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="baa13-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="baa13-206">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="baa13-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="baa13-207">Client.cs dosyasında, bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="baa13-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="baa13-208">Client.cs dosyasında, Service X. 509.952 sertifikasının konu adını localhost yerine uzak konağın tam bilgisayar adıyla eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="baa13-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="baa13-209">İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="baa13-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="baa13-210">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="baa13-210">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="baa13-211">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="baa13-211">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="baa13-212">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="baa13-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
