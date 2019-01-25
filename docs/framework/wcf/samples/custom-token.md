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
# <a name="custom-token"></a><span data-ttu-id="159d1-102">Özel Belirteç</span><span class="sxs-lookup"><span data-stu-id="159d1-102">Custom Token</span></span>
<span data-ttu-id="159d1-103">Bu örnek, bir Windows Communication Foundation (WCF) uygulamasına özel bir belirteç uygulamasını ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="159d1-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="159d1-104">Örnekte bir `CreditCardToken` istemci kredi kartı bilgilerini güvenli bir şekilde hizmetine geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="159d1-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="159d1-105">Belirteç WS-güvenlik ileti üstbilgisinde imzalanır ve yanı sıra ileti gövdesi ve diğer ileti üstbilgileri simetrik güvenlik bağlama öğesi kullanılarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="159d1-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="159d1-106">Bu, yerleşik belirteçleri yeterli olmadığı durumlarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="159d1-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="159d1-107">Bu örnek, bir yerleşik belirteçlerin kullanmak yerine bir hizmete özel güvenlik belirteci gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="159d1-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="159d1-108">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="159d1-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
>  <span data-ttu-id="159d1-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="159d1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="159d1-110">Özetlemek gerekirse, bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="159d1-110">To summarize, this sample demonstrates the following:</span></span>

-   <span data-ttu-id="159d1-111">Nasıl bir istemci bir hizmete bir özel güvenlik belirteci geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="159d1-111">How a client can pass a custom security token to a service.</span></span>

-   <span data-ttu-id="159d1-112">Nasıl hizmet kullanabilir ve bir özel güvenlik belirteci doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-112">How the service can consume and validate a custom security token.</span></span>

-   <span data-ttu-id="159d1-113">Nasıl WCF hizmet kodunun, özel güvenlik belirteci dahil olmak üzere alınan güvenlik belirteçleri hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="159d1-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

-   <span data-ttu-id="159d1-114">Sunucu X.509 sertifikasının nasıl ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="159d1-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="159d1-115">Özel güvenlik belirteci kullanılarak istemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="159d1-115">Client Authentication Using a Custom Security Token</span></span>
 <span data-ttu-id="159d1-116">Hizmeti kullanarak program aracılığıyla oluşturulan tek bir uç noktasını kullanıma sunar `BindingHelper` ve `EchoServiceHost` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="159d1-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="159d1-117">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="159d1-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="159d1-118">Özel bağlama kullanma yapılandırılmış bağlama `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="159d1-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="159d1-119">Bu örnek ayarlar `SymmetricSecurityBindingElement` simetrik anahtar aktarım sırasında korumak ve özel bir geçirmek için bir hizmetin X.509 sertifikası kullanılacak `CreditCardToken` WS-güvenlik ileti üstbilgisinde bir imzalanmış ve şifrelenmiş güvenlik belirteci olarak.</span><span class="sxs-lookup"><span data-stu-id="159d1-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="159d1-120">Davranış, istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında daha fazla bilgi için kullanılacak hizmet kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="159d1-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

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

 <span data-ttu-id="159d1-121">Kredi kartı kullanmak için iletide, belirteç örnek özel hizmet kimlik bilgilerini bu işlevselliği sağlayacak şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="159d1-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="159d1-122">Hizmet kimlik bilgilerini sınıfı bulunan `CreditCardServiceCredentials` sınıfı ve davranışları koleksiyonlarına hizmet ana bilgisayar eklenir `EchoServiceHost.InitializeRuntime` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="159d1-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

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

 <span data-ttu-id="159d1-123">İstemci uç noktası benzer şekilde, hizmet uç noktası olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="159d1-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="159d1-124">Aynı istemcinin kullandığı `BindingHelper` bağlama oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="159d1-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="159d1-125">Kurulumu geri kalanını bulunan `Client` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="159d1-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="159d1-126">İstemci ayrıca içindeki bilgilere ayarlar `CreditCardToken` ve hizmet X.509 sertifikasını ekleyerek Kurulum kodu hakkında bilgi bir `CreditCardClientCredentials` istemci uç nokta davranışları koleksiyona uygun veri örneği.</span><span class="sxs-lookup"><span data-stu-id="159d1-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="159d1-127">Örnek X.509 sertifikası konu adı ayarlamak kullanır. `CN=localhost` hizmet sertifikası olarak.</span><span class="sxs-lookup"><span data-stu-id="159d1-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

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

## <a name="custom-security-token-implementation"></a><span data-ttu-id="159d1-128">Özel güvenlik belirteci uygulama</span><span class="sxs-lookup"><span data-stu-id="159d1-128">Custom Security Token Implementation</span></span>
 <span data-ttu-id="159d1-129">Bir özel güvenlik belirteci WCF etkinleştirmek için bir nesne temsili özel güvenlik belirteci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="159d1-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="159d1-130">Bu gösterim örneği sahip `CreditCardToken` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="159d1-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="159d1-131">Tüm ilgili güvenlik belirteci bilgilerini tutan ve güvenlik anahtarları güvenlik belirtecinde yer alan bir listesini sağlamak üzere bir nesne temsili sorumludur.</span><span class="sxs-lookup"><span data-stu-id="159d1-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="159d1-132">Bu durumda, kredi kartı güvenlik belirteci, tüm güvenlik anahtarı içermiyor.</span><span class="sxs-lookup"><span data-stu-id="159d1-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="159d1-133">Sonraki bölümde, ne olmalı kablo üzerinden iletilmesi için özel bir belirteç etkinleştirmek için yapılır ve bir WCF uç noktası tarafından kullanılan açıklar.</span><span class="sxs-lookup"><span data-stu-id="159d1-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="159d1-134">Özel bir kredi kartı ileti gelen ve giden belirteci alma</span><span class="sxs-lookup"><span data-stu-id="159d1-134">Getting the Custom Credit Card Token to and from the Message</span></span>
 <span data-ttu-id="159d1-135">Wcf'de güvenlik belirteci serileştiricileri XML iletisi bir nesne temsili güvenlik belirteçleri oluşturma ve güvenlik belirteçlerini XML biçiminin oluşturarak sorumludur.</span><span class="sxs-lookup"><span data-stu-id="159d1-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="159d1-136">Ayrıca güvenlik belirteçleri işaret eden anahtarı tanımlayıcıları yazma ve okuma gibi diğer işlevleri sorumlu olduğu, ancak bu örnek yalnızca güvenlik belirteci ile ilgili işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="159d1-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="159d1-137">Özel bir etkinleştirme belirteci kendi güvenlik belirteci serileştiriciye uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="159d1-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="159d1-138">Bu örnekte `CreditCardSecurityTokenSerializer` bu amaç için sınıf.</span><span class="sxs-lookup"><span data-stu-id="159d1-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="159d1-139">Hizmet özel seri hale getirici XML biçimi özel belirteç okur ve özel belirteç nesne gösterimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="159d1-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="159d1-140">İstemci üzerindeki `CreditCardSecurityTokenSerializer` sınıfı XML yazıcısı güvenlik belirteci nesne gösterimine içinde yer alan bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="159d1-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="159d1-141">Belirteç sağlayıcısı ve belirteç kimlik doğrulayıcısı sınıfları nasıl oluşturulur</span><span class="sxs-lookup"><span data-stu-id="159d1-141">How Token Provider and Token Authenticator Classes are Created</span></span>
 <span data-ttu-id="159d1-142">Hizmet ve istemci kimlik bilgileri güvenlik belirteci yöneticisi örneği sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="159d1-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="159d1-143">Güvenlik belirteci yöneticisi örneği belirteci sağlayıcıları, belirteç Doğrulayıcı ve belirteci seri hale getiricileri genişletme almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="159d1-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="159d1-144">Belirteç sağlayıcısı, belirteç istemci veya hizmet kimlik bilgilerini yer alan bilgiler temel nesne temsilini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="159d1-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="159d1-145">Belirteç nesnesi gösterimi ardından iletiyi belirteç serializer özelliği (önceki bölümde anlatılmaktadır) kullanarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="159d1-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="159d1-146">Belirteç kimlik doğrulayıcısı iletisinde gelen belirteçlerini doğrular.</span><span class="sxs-lookup"><span data-stu-id="159d1-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="159d1-147">Gelen belirteci bir nesne temsili belirteci seri hale getirici tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="159d1-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="159d1-148">Bu nesne temsili, ardından belirteci kimlik doğrulayıcı için doğrulama için geçirilir.</span><span class="sxs-lookup"><span data-stu-id="159d1-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="159d1-149">Belirteç başarıyla doğrulandıktan sonra belirteç kimlik doğrulayıcısı koleksiyonunu döndürür. `IAuthorizationPolicy` belirtecinde yer alan bilgileri temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="159d1-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="159d1-150">Bu bilgiler daha sonra ileti işleme sırasında yetkilendirme kararları gerçekleştirmek ve uygulama için talep sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="159d1-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="159d1-151">Bu örnekte, kredi kartı belirteci kimlik doğrulayıcı kullanan `CreditCardTokenAuthorizationPolicy` bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="159d1-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="159d1-152">Belirteç serializer özelliği, belirtecin kablo gelen ve giden bir nesne temsili almak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="159d1-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="159d1-153">Bu, önceki bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="159d1-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="159d1-154">Yalnızca istemci hizmeti yönde bir kredi kartı belirteç aktarmaya istediğimizden Bu örnekte, bir belirteç sağlayıcısı istemci ve hizmet üzerinde yalnızca bir belirteç kimlik doğrulayıcısı kullanırız.</span><span class="sxs-lookup"><span data-stu-id="159d1-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="159d1-155">İstemci işlevselliği bulunan `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` ve `CreditCardTokenProvider` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="159d1-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="159d1-156">İşlevi hizmette yer `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` ve `CreditCardTokenAuthorizationPolicy` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="159d1-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

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

## <a name="displaying-the-callers-information"></a><span data-ttu-id="159d1-157">Çağıranlar bilgileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="159d1-157">Displaying the Callers' Information</span></span>
 <span data-ttu-id="159d1-158">Arayanın bilgileri görüntülemek için kullanın `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="159d1-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="159d1-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir.</span><span class="sxs-lookup"><span data-stu-id="159d1-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="159d1-160">Talepleri tarafından sağlanan `CreditCardToken` sınıfını kendi `AuthorizationPolicies` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="159d1-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

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

 <span data-ttu-id="159d1-161">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="159d1-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="159d1-162">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="159d1-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="159d1-163">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="159d1-163">Setup Batch File</span></span>
 <span data-ttu-id="159d1-164">Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren IIS tarafından barındırılan uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="159d1-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="159d1-165">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="159d1-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="159d1-166">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="159d1-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

-   <span data-ttu-id="159d1-167">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="159d1-167">Creating the server certificate:</span></span>

     <span data-ttu-id="159d1-168">Aşağıdaki satırları gelen `Setup.bat` toplu iş dosyası kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="159d1-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="159d1-169">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="159d1-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="159d1-170">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="159d1-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="159d1-171">Bu toplu iş dosyasında localhost varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="159d1-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="159d1-172">Değiştirirseniz `%SERVER_NAME%` değişken Client.cs ve adını da dosyalara gidin ve gerekir localhost tüm örneklerini Setup.bat betikte kullandığınız sunucu adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="159d1-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="159d1-173">Sertifika altında (Kişisel) My deposunda saklanır `LocalMachine` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="159d1-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="159d1-174">Depolanmış bir sertifikayla IIS tarafından barındırılan hizmetleri LocalMachine deposunda.</span><span class="sxs-lookup"><span data-stu-id="159d1-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="159d1-175">Şirket içinde barındırılan hizmetler için istemci sertifikası LocalMachine dize CurrentUser ile değiştirerek CurrentUser deposu konumda depolamak için toplu iş dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="159d1-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="159d1-176">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:</span><span class="sxs-lookup"><span data-stu-id="159d1-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="159d1-177">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="159d1-178">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="159d1-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="159d1-179">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="159d1-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="159d1-180">IIS barındırılan hizmeti için sertifika özel anahtar erişimi etkinleştirmek için IIS tarafından barındırılan işlem altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="159d1-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="159d1-181">Bu, son adımda Setup.bat betiği tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="159d1-181">This is accomplished by last steps in the Setup.bat script.</span></span>

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
>  <span data-ttu-id="159d1-182">Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="159d1-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="159d1-183">PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="159d1-184">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="159d1-184">To set up and build the sample</span></span>

1.  <span data-ttu-id="159d1-185">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="159d1-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="159d1-186">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="159d1-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="159d1-187">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="159d1-187">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="159d1-188">Yönetici ayrıcalıklarına sahip bir Visual Studio 2012 komut istemi penceresi açın ve örnek yükleme klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="159d1-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="159d1-189">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler. Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="159d1-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
>  <span data-ttu-id="159d1-190">Sertifikaları örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak kaldırmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="159d1-191">Diğer güvenlik örnekleri aynı sertifikalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="159d1-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="159d1-192">Client.exe client\bin dizinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="159d1-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="159d1-193">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="159d1-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="159d1-194">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="159d1-194">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="159d1-195">Bilgisayar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="159d1-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="159d1-196">Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="159d1-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="159d1-197">Hizmet dizini hizmeti bilgisayarında hizmet program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="159d1-198">CreditCardFile.txt kopyalamak unutmayın; Aksi takdirde kredi kartı authenticator istemciden gönderilen kredi kartı bilgileri doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="159d1-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="159d1-199">Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="159d1-200">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="159d1-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="159d1-201">Setup.bat değiştirirseniz kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` değişkenini hizmetin barındırıldığı bilgisayarın tam adı.</span><span class="sxs-lookup"><span data-stu-id="159d1-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="159d1-202">Setup.bat dosyasının Visual Studio için geliştirici komut isteminden çalıştırılmalıdır Not yönetici ayrıcalıklarıyla açılan.</span><span class="sxs-lookup"><span data-stu-id="159d1-202">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="159d1-203">Sunucu sertifikası istemci CurrentUser TrustedPeople deponuzu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="159d1-204">Yalnızca sunucu sertifikası güvenilir bir veren tarafından yazılmazsa bunu yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="159d1-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="159d1-205">EchoServiceHost.cs dosyasında localhost yerine tam bilgisayar adını belirtmek için sertifika konu adı değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="159d1-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="159d1-206">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="159d1-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="159d1-207">Client.cs dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="159d1-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="159d1-208">Client.cs dosyasında localhost yerine uzak ana bilgisayar tam olarak nitelenmiş adını eşleştirmek için hizmet X.509 sertifikasının konu adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="159d1-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="159d1-209">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="159d1-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="159d1-210">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="159d1-210">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="159d1-211">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="159d1-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="159d1-212">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="159d1-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159d1-213">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="159d1-213">See also</span></span>
