---
title: "Özel Belirteç"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19593e61cc640068ac7c90a6abbd6ea0d6a3ff08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-token"></a><span data-ttu-id="7ed8f-102">Özel Belirteç</span><span class="sxs-lookup"><span data-stu-id="7ed8f-102">Custom Token</span></span>
<span data-ttu-id="7ed8f-103">Bu örnek özel bir belirteç uygulamasına eklemek nasıl gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-103">This sample demonstrates how to add a custom token implementation into a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="7ed8f-104">Örnek kullanan bir `CreditCardToken` hizmete istemci kredi kartı bilgilerini güvenli bir şekilde geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="7ed8f-105">Belirteç WS güvenliği ileti üstbilgisinde geçirilir ve imzalanır ve ileti gövdesi ve diğer ileti üstbilgilerini yanı sıra simetrik güvenlik bağlama öğesi kullanılarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="7ed8f-106">Bu, burada yerleşik belirteçleri yetersiz olduğu durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="7ed8f-107">Bu örnek, bir özel güvenlik belirteci yerleşik belirteçleri birini kullanmak yerine bir hizmet sağlamak üzere gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="7ed8f-108">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ed8f-109">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7ed8f-110">Özetlemek için bu örnek şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7ed8f-110">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="7ed8f-111">Nasıl bir istemci bir hizmet için bir özel güvenlik belirteci geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-111">How a client can pass a custom security token to a service.</span></span>  
  
-   <span data-ttu-id="7ed8f-112">Nasıl hizmeti kullanmak ve bir özel güvenlik belirteci doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-112">How the service can consume and validate a custom security token.</span></span>  
  
-   <span data-ttu-id="7ed8f-113">Nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] servis kodu özel güvenlik belirteci dahil olmak üzere alınan güvenlik belirteçleri hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-113">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code can obtain the information about received security tokens including the custom security token.</span></span>  
  
-   <span data-ttu-id="7ed8f-114">Nasıl sunucu X.509 sertifikasının ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="7ed8f-115">Bir özel güvenlik belirteci kullanarak istemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7ed8f-115">Client Authentication Using a Custom Security Token</span></span>  
 <span data-ttu-id="7ed8f-116">Hizmet program aracılığıyla kullanılarak oluşturulan tek bir uç noktasını kullanıma sunar `BindingHelper` ve `EchoServiceHost` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="7ed8f-117">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7ed8f-118">Özel bağlama kullanma bağlama yapılandırılmış `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="7ed8f-119">Bu örnek ayarlar `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtar korumak ve özel bir geçirmek için bir hizmetin X.509 sertifikası kullanmak üzere `CreditCardToken` imzalanmış ve şifrelenmiş güvenlik belirteci olarak WS-güvenlik ileti üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="7ed8f-120">Davranış istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında bilgi için kullanılacak olan hizmet kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>  
  
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
  
 <span data-ttu-id="7ed8f-121">Bir kredi kartı kullanmak için iletide belirteci örnek özel hizmeti kimlik bilgileri bu işlevselliği sağlayacak şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="7ed8f-122">Hizmet kimlik bilgilerini sınıfı bulunan `CreditCardServiceCredentials` sınıfı ve hizmet konağı davranışları koleksiyonlarına eklenen `EchoServiceHost.InitializeRuntime` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>  
  
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
  
 <span data-ttu-id="7ed8f-123">İstemci uç noktası hizmet uç noktası benzer bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="7ed8f-124">İstemci aynı kullanır `BindingHelper` sınıfı bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="7ed8f-125">Kurulumu geri kalanı bulunan `Client` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="7ed8f-126">İstemci ayrıca yer bilgilere ayarlar `CreditCardToken` ve hizmet X.509 sertifikası ekleyerek Kurulum kodu hakkında bilgi bir `CreditCardClientCredentials` uygun verileri istemci uç nokta davranışları koleksiyona örnekle.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="7ed8f-127">Örnek X.509 sertifikası konu adı ayarlamak kullanır. `CN=localhost` hizmet sertifikası.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>  
  
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
  
## <a name="custom-security-token-implementation"></a><span data-ttu-id="7ed8f-128">Özel güvenlik belirteci uygulama</span><span class="sxs-lookup"><span data-stu-id="7ed8f-128">Custom Security Token Implementation</span></span>  
 <span data-ttu-id="7ed8f-129">Bir özel güvenlik belirteci etkinleştirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bir nesne temsili özel güvenlik belirteci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-129">To enable a custom security token in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], create an object representation of the custom security token.</span></span> <span data-ttu-id="7ed8f-130">Bu gösterim örnek sahip `CreditCardToken` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="7ed8f-131">Nesne temsili tüm ilgili güvenlik belirteci bilgilerini tutan ve güvenlik belirtecinde yer alan güvenlik anahtarları listesini sağlamak üzere sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="7ed8f-132">Bu durumda, kredi kartı güvenlik belirteci tüm güvenlik anahtarı içermiyor.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-132">In this case, the credit card security token does not contain any security key.</span></span>  
  
 <span data-ttu-id="7ed8f-133">Ne kablo üzerinden iletilmesi özel bir belirteç etkinleştirmek için yapılır ve gerekir tarafından tüketilen sonraki bölümde açıklandığı bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint.</span></span>  
  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="7ed8f-134">Özel kredi kartı için ve iletisi belirteci alma</span><span class="sxs-lookup"><span data-stu-id="7ed8f-134">Getting the Custom Credit Card Token to and from the Message</span></span>  
 <span data-ttu-id="7ed8f-135">Güvenlik belirteci serileştiricileri içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletisi XML'den güvenlik belirteçlerinin bir nesne temsili oluşturma ve güvenlik belirteçlerinin XML form oluşturma sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-135">Security token serializers in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="7ed8f-136">Aynı zamanda okuma ve yazma güvenlik belirteçleri işaret eden anahtar tanımlayıcıları gibi diğer işlevleri sorumlu olan, ancak bu örnek yalnızca güvenlik belirteci ile ilgili işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="7ed8f-137">Özel bir etkinleştirmek için belirteç, kendi güvenlik belirteci seri hale getirici uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="7ed8f-138">Bu örnekte `CreditCardSecurityTokenSerializer` bu amaç için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>  
  
 <span data-ttu-id="7ed8f-139">Hizmet özel seri hale getirici özel belirteç XML formunu okur ve özel belirteç nesne gösterimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>  
  
 <span data-ttu-id="7ed8f-140">İstemci üzerindeki `CreditCardSecurityTokenSerializer` sınıfı XML yazıcıyı güvenlik belirteci nesne gösterimine içinde yer alan bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>  
  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="7ed8f-141">Belirteç sağlayıcısı ve belirteç kimlik doğrulayıcı sınıfları nasıl oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7ed8f-141">How Token Provider and Token Authenticator Classes are Created</span></span>  
 <span data-ttu-id="7ed8f-142">İstemci ve hizmet kimlik bilgilerini güvenlik belirteci yöneticisi örneği sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="7ed8f-143">Güvenlik belirteci yöneticisi örneği belirteci sağlayıcıları, belirteç kimlik doğrulayan ve belirteç serileştiricileri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>  
  
 <span data-ttu-id="7ed8f-144">Belirteç sağlayıcı istemci veya hizmet kimlik bilgilerini yer alan bilgileri temel alarak belirteci nesne gösterimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="7ed8f-145">Belirteç nesne gösterimi (önceki bölümde tartışılan) belirteci seri hale getirici kullanarak ileti sonra yazılır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>  
  
 <span data-ttu-id="7ed8f-146">Belirteç kimlik doğrulayıcı iletisi gelmesini belirteçlerini doğrular.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="7ed8f-147">Gelen belirteç nesne temsili belirteci seri hale getirici tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="7ed8f-148">Bu nesne temsili, daha sonra belirteç kimlik doğrulayıcı için doğrulama geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="7ed8f-149">Belirteç başarıyla doğrulandıktan sonra belirteç kimlik doğrulayıcı koleksiyonunu döndürür `IAuthorizationPolicy` belirtecinde yer alan bilgileri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="7ed8f-150">Bu bilgiler daha sonra ileti işleme sırasında yetkilendirme kararları gerçekleştirmek ve uygulama için talepler sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="7ed8f-151">Bu örnekte, kredi kartı belirteç kimlik doğrulayıcı kullanan `CreditCardTokenAuthorizationPolicy` bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>  
  
 <span data-ttu-id="7ed8f-152">Belirteci seri hale getirici, belirtecin kablo gelen ve giden nesne gösterimini almak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="7ed8f-153">Bu, önceki bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-153">This is discussed in the previous section.</span></span>  
  
 <span data-ttu-id="7ed8f-154">Bir kredi kartı belirteci yalnızca istemci hizmeti yönde iletmeye istiyoruz çünkü bu örnekte, bir belirteç sağlayıcısı yalnızca istemci ve bir belirteç kimlik doğrulayıcısı yalnızca hizmette üzerinde kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>  
  
 <span data-ttu-id="7ed8f-155">İstemci üzerinde işlevselliği bulunan `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` ve `CreditCardTokenProvider` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>  
  
 <span data-ttu-id="7ed8f-156">Hizmette işlevselliği bulunan `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` ve `CreditCardTokenAuthorizationPolicy` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>  
  
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
  
## <a name="displaying-the-callers-information"></a><span data-ttu-id="7ed8f-157">Arayanlar bilgileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7ed8f-157">Displaying the Callers' Information</span></span>  
 <span data-ttu-id="7ed8f-158">Arayanın bilgileri görüntülemek için kullanın `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="7ed8f-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="7ed8f-160">Talep tarafından sağlanan `CreditCardToken` sınıfını kendi `AuthorizationPolicies` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>  
  
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
  
 <span data-ttu-id="7ed8f-161">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7ed8f-162">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-162">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="7ed8f-163">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="7ed8f-163">Setup Batch File</span></span>  
 <span data-ttu-id="7ed8f-164">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren IIS tarafından barındırılan uygulamayı çalıştırmayı ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="7ed8f-165">Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="7ed8f-166">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="7ed8f-167">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="7ed8f-167">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="7ed8f-168">Aşağıdaki satırları `Setup.bat` toplu iş dosyası kullanılması için sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="7ed8f-169">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="7ed8f-170">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="7ed8f-171">Bu toplu iş dosyasındaki localhost varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="7ed8f-172">Değiştirirseniz `%SERVER_NAME%` değişken, Client.cs ve adını da dosyalarıyla gidin ve gerekir localhost tüm örneklerini Setup.bat komut dosyasında kullandığınız sunucu adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>  
  
     <span data-ttu-id="7ed8f-173">Sertifika altında (Kişisel) My deposunda saklanır `LocalMachine` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="7ed8f-174">Sertifika saklanır IIS tarafından barındırılan hizmetler için LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="7ed8f-175">Kendini barındıran Hizmetleri için istemci sertifikası LocalMachine dize Currentuser'a ile değiştirerek Currentuser'a deposu konumda depolamak için toplu iş dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="7ed8f-176">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="7ed8f-176">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="7ed8f-177">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7ed8f-178">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7ed8f-179">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="7ed8f-180">IIS barındırılan hizmeti sertifika özel anahtarına erişimi etkinleştirmek için IIS tarafından barındırılan işlemin altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="7ed8f-181">Bu son adımda Setup.bat komut dosyası tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-181">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
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
>  <span data-ttu-id="7ed8f-182">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-182">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="7ed8f-183">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-183">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7ed8f-184">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ed8f-184">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="7ed8f-185">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8f-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7ed8f-186">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8f-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7ed8f-187">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7ed8f-187">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="7ed8f-188">Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] örnek yükleme klasöründen çalıştırma Setup.bat ve yönetici ayrıcalıkları ile komut istemi penceresi.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-188">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="7ed8f-189">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler. Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ed8f-190">Örnekle bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="7ed8f-191">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="7ed8f-192">Client.exe client\bin dizininden başlatın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="7ed8f-193">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="7ed8f-194">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7ed8f-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="7ed8f-195">Bilgisayar örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7ed8f-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="7ed8f-196">Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="7ed8f-197">Hizmet dizin hizmeti bilgisayarında hizmet program dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="7ed8f-198">CreditCardFile.txt kopyalamak unutmayın; Aksi takdirde kredi kartı Doğrulayıcı istemciden gönderilen kredi kartı bilgileri doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="7ed8f-199">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="7ed8f-200">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="7ed8f-201">Değiştirirseniz Setup.bat kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` değişken hizmet barındırıldığı bilgisayarın tam adı.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="7ed8f-202">Visual Studio komut istemini yönetici ayrıcalıklarıyla açılmış içinde Setup.bat dosya çalıştırmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-202">Note that the Setup.bat file must be run in a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="7ed8f-203">İstemci üzerinde Currentuser'a TrustedPeople deposuna sunucu sertifikasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="7ed8f-204">Yalnızca sunucu sertifikası güvenilir bir veren tarafından verilmemiş varsa bunu yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="7ed8f-205">EchoServiceHost.cs dosyasında localhost yerine bir tam bilgisayar adını belirtmek için sertifika konu adı değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="7ed8f-206">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="7ed8f-207">Client.cs dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="7ed8f-208">Client.cs dosyasında localhost yerine uzak ana bilgisayarın tam bilgisayar adı ile eşleşmesi için hizmet X.509 sertifikasının konu adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="7ed8f-209">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="7ed8f-210">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7ed8f-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7ed8f-211">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="7ed8f-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="7ed8f-212">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed8f-213">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ed8f-213">See Also</span></span>
