---
title: "SAML Belirteç Sağlayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc6eaa916507c7e1c530d4ee757097bf0bffcd34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="saml-token-provider"></a><span data-ttu-id="e2fe2-102">SAML Belirteç Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="e2fe2-102">SAML Token Provider</span></span>
<span data-ttu-id="e2fe2-103">Bu örnek, özel bir istemci SAML belirteç sağlayıcı uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="e2fe2-104">Bir belirteç sağlayıcısı [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik altyapısı için kimlik bilgileri sağladığını için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="e2fe2-105">Belirteç sağlayıcı genel hedef inceler ve böylece güvenlik altyapısı ileti güvenliğini sağlayabilirsiniz sorunları kimlik bilgileri gerekli.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e2fe2-106">Varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-106"> ships with the default Credential Manager Token Provider.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e2fe2-107">Ayrıca birlikte bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-107"> also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="e2fe2-108">Özel belirteç sağlayıcılarını aşağıdaki durumlarda yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="e2fe2-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="e2fe2-109">Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="e2fe2-110">Kullanıcı ayrıntılarını geldiğinde sağladığında kimlik bilgilerini noktadan dönüştürme için kendi özel mekanizması sağlamak istiyorsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci framework kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="e2fe2-111">Özel belirteç oluşturuluyorsa.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="e2fe2-112">Bu örnek dışında alınan bir SAML belirtecine sağlayan özel bir belirteç sağlayıcısı oluşturmak nasıl göstermektedir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanılacak istemci framework.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework to be used.</span></span>  
  
 <span data-ttu-id="e2fe2-113">Özetlemek için bu örnek şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e2fe2-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="e2fe2-114">Nasıl bir istemci bir özel belirteç sağlayıcısı ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="e2fe2-115">Nasıl bir SAML belirtecine için özel istemci kimlik bilgileri geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-115">How a SAML token can be passed to the custom client credentials.</span></span>  
  
-   <span data-ttu-id="e2fe2-116">SAML belirteci için nasıl sağlandığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci framework.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-116">How the SAML token is provided to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework.</span></span>  
  
-   <span data-ttu-id="e2fe2-117">Sunucu sunucunun X.509 sertifikası kullanarak istemci tarafından kimlik doğrulamasının nasıl.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="e2fe2-118">Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için iki uç noktalarını kullanıma sunar. Her uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e2fe2-119">Bağlama ile standart bir yapılandırılmış `wsFederationHttpBinding`, ileti güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="e2fe2-120">Diğer asimetrik kanıtını anahtarı kullanan bir SAML belirteci ile kimlik doğrulaması için istemci beklediği sırada simetrik kanıt anahtarı kullanan bir SAML belirteci ile kimlik doğrulaması için istemci bir uç nokta bekler.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="e2fe2-121">Hizmetini kullanarak sertifika hizmetini de yapılandırır `serviceCredentials` davranışı.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="e2fe2-122">`serviceCredentials` Davranış bir hizmet sertifikası yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="e2fe2-123">Bir hizmet sertifikası, hizmetin kimliğini doğrulamak ve ileti koruma sağlamak için bir istemci tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="e2fe2-124">Aşağıdaki yapılandırma, bu konunun sonunda kurulum yönergelerini açıklandığı gibi örnek Kurulum sırasında yüklü "localhost" Sertifika başvurur.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="e2fe2-125">`serviceCredentials` Davranışı de SAML belirteçleri imzalamak için güvenilir sertifikaları yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="e2fe2-126">Aşağıdaki yapılandırma sırasında örnek yüklü 'Alice' sertifika başvurur.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>  
  
```xml  
<system.serviceModel>  
 <services>  
  <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
   <host>  
    <baseAddresses>  
     <!-- configure base address provided by host -->  
     <add    
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />  
    </baseAddresses>  
   </host>  
   <!-- use base address provided by host -->  
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->  
   <endpoint address="calc/symm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->  
   <endpoint address="calc/asymm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding2"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
 </services>  
  
 <bindings>  
  <wsFederationHttpBinding>  
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->  
   <binding name="Binding1">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"   
              issuedKeyType="SymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>  
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->  
   <binding name="Binding2">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"  
              issuedKeyType="AsymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>          
  </wsFederationHttpBinding>  
 </bindings>  
  
 <behaviors>  
  <serviceBehaviors>  
   <behavior name="CalculatorServiceBehavior">  
    <!--   
    The serviceCredentials behavior allows one to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
    This configuration references the "localhost" certificate installed during the setup instructions.  
    -->  
    <serviceCredentials>  
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->  
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >  
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->  
      <knownCertificates>  
       <add storeLocation="LocalMachine"   
            storeName="TrustedPeople"   
            x509FindType="FindBySubjectName"   
            findValue="Alice"/>  
      </knownCertificates>  
     </issuedTokenAuthentication>  
     <serviceCertificate storeLocation="LocalMachine"  
                         storeName="My"  
                         x509FindType="FindBySubjectName"  
                         findValue="localhost"  />  
    </serviceCredentials>  
   </behavior>  
  </serviceBehaviors>  
 </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e2fe2-127">Aşağıdaki adımlar, özel bir SAML belirteç sağlayıcı geliştirmek ve ile tümleştirmek nasıl gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: güvenlik framework:</span><span class="sxs-lookup"><span data-stu-id="e2fe2-127">The following steps show how to develop a custom SAML token provider and integrate it with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: security framework:</span></span>  
  
1.  <span data-ttu-id="e2fe2-128">Özel bir SAML belirteç sağlayıcı yazma.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-128">Write a custom SAML token provider.</span></span>  
  
     <span data-ttu-id="e2fe2-129">Örnek oluşturma sırasında sağlanan bir SAML onayı temel alarak bir güvenlik belirteci verir bir özel SAML belirteç sağlayıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>  
  
     <span data-ttu-id="e2fe2-130">Bu görevi gerçekleştirmek için özel belirteç sağlayıcı türetildiği <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="e2fe2-131">Bu yöntem oluşturur ve yeni bir döndürür `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-131">This method creates and returns a new `SecurityToken`.</span></span>  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
     // Create a SamlSecurityToken from the provided assertion  
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);  
  
     // Create a SecurityTokenSerializer that will be used to   
     // serialize the SamlSecurityToken  
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();  
     // Create a memory stream to write the serialized token into  
     // Use an initial size of 64Kb  
     MemoryStream s = new MemoryStream(UInt16.MaxValue);  
  
     // Create an XmlWriter over the stream  
     XmlWriter xw = XmlWriter.Create(s);  
  
     // Write the SamlSecurityToken into the stream  
     ser.WriteToken(xw, samlToken);  
  
     // Seek back to the beginning of the stream  
     s.Seek(0, SeekOrigin.Begin);  
  
     // Load the serialized token into a DOM  
     XmlDocument dom = new XmlDocument();  
     dom.Load(s);  
  
     // Create a KeyIdentifierClause for the SamlSecurityToken  
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();  
  
    // Return a GenericXmlToken from the XML for the   
    // SamlSecurityToken, the proof token, the valid from and valid  
    // until times from the assertion and the key identifier clause  
    // created above  
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);  
    }  
    ```  
  
2.  <span data-ttu-id="e2fe2-132">Özel güvenlik belirteci yöneticisi yazma.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-132">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="e2fe2-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Sınıfı oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="e2fe2-134">Bir güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayan ve belirteci seri hale getirici oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmayan.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="e2fe2-135">Bu özel güvenlik belirteci yöneticisi devraldığı örnek <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri belirtmek özel SAML belirteç sağlayıcı SAML belirteci döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="e2fe2-136">İstemci kimlik bilgileri sınıfı (3. adıma bakın) bir onaylama belirtmediyse, güvenlik belirteci yöneticisi uygun bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>  
  
    ```  
    public class SamlSecurityTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
     SamlClientCredentials samlClientCredentials;  
  
     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)  
      : base(samlClientCredentials)  
     {  
      // Store the creating client credentials  
      this.samlClientCredentials = samlClientCredentials;  
     }  
  
     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
     {  
      // If token requirement matches SAML token return the   
      // custom SAML token provider  
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||  
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")  
      {  
       // Retrieve the SAML assertion and proof token from the   
       // client credentials  
       SamlAssertion assertion = this.samlClientCredentials.Assertion;  
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;  
  
       // If either the assertion of proof token is null...  
       if (assertion == null || prooftoken == null)  
       {  
        // ...get the SecurityBindingElement and then the   
        // specified algorithm suite  
        SecurityBindingElement sbe = null;  
        SecurityAlgorithmSuite sas = null;  
  
        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))  
        {  
         sas = sbe.DefaultAlgorithmSuite;  
        }  
  
        // If the token requirement is for a SymmetricKey based token..  
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)  
        {  
         // Create a symmetric proof token  
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );  
         // and a corresponding assertion based on the claims specified in the client credentials  
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);  
        }  
        // otherwise...  
        else  
        {  
         // Create an asymmetric proof token  
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();  
         // and a corresponding assertion based on the claims   
         // specified in the client credentials  
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );  
        }  
       }  
  
       // Create a SamlSecurityTokenProvider based on the assertion and proof token  
       return new SamlSecurityTokenProvider(assertion, prooftoken);  
      }  
      // otherwise use base implementation  
      else  
      {  
       return base.CreateSecurityTokenProvider(tokenRequirement);  
      }  
    }  
    ```  
  
3.  <span data-ttu-id="e2fe2-137">Özel istemci kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-137">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="e2fe2-138">İstemci kimlik bilgileri sınıfı istemci proxy için yapılandırılmış olan kimlik bilgilerini temsil etmek için kullanılır ve bir güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteci seri hale getirici elde etmek için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>  
  
    ```  
    public class SamlClientCredentials : ClientCredentials  
    {  
     ClaimSet claims;  
     SamlAssertion assertion;  
     SecurityToken proofToken;  
  
     public SamlClientCredentials() : base()  
     {  
      // Set SupportInteractive to false to suppress Cardspace UI  
      base.SupportInteractive = false;  
     }  
  
     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )  
     {  
      // Just do reference copy given sample nature  
      this.assertion = other.assertion;  
      this.claims = other.claims;  
      this.proofToken = other.proofToken;  
     }  
  
     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }  
  
     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }  
     public ClaimSet Claims { get { return claims; } set { claims = value; } }  
  
     protected override ClientCredentials CloneCore()  
     {  
      return new SamlClientCredentials(this);  
     }  
  
     public override SecurityTokenManager CreateSecurityTokenManager()  
     {  
      // return custom security token manager  
      return new SamlSecurityTokenManager(this);  
     }  
    }  
    ```  
  
4.  <span data-ttu-id="e2fe2-139">Özel istemci kimlik bilgisi kullanmak için istemciyi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-139">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="e2fe2-140">Örnek, varsayılan istemci kimlik bilgisi sınıfını siler ve istemci özel istemci kimlik bilgisi kullanabilmek için yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>  
  
    ```  
    // Create new credentials class  
    SamlClientCredentials samlCC = new SamlClientCredentials();  
  
    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case  
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");  
  
    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case  
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");  
  
    // Create some claims to put in the SAML assertion  
    IList<Claim> claims = new List<Claim>();  
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));  
    ClaimSet claimset = new DefaultClaimSet(claims);  
    samlCC.Claims = claimset;  
  
    // set new credentials  
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);  
    ```  
  
 <span data-ttu-id="e2fe2-141">Hizmette arayanla ilişkili talep görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="e2fe2-142">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e2fe2-143">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-143">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="e2fe2-144">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="e2fe2-144">Setup Batch File</span></span>  
 <span data-ttu-id="e2fe2-145">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e2fe2-146">Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="e2fe2-147">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="e2fe2-148">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="e2fe2-148">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="e2fe2-149">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="e2fe2-150">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="e2fe2-151">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e2fe2-152">Localhost bu toplu iş dosyasında varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-152">The default value in this batch file is localhost.</span></span>  
  
     <span data-ttu-id="e2fe2-153">Sertifika, LocalMachine depolama konumu altında (Kişisel) My deposunda saklanır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="e2fe2-154">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="e2fe2-154">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="e2fe2-155">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e2fe2-156">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e2fe2-157">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="e2fe2-158">Sertifikayı veren sertifika oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-158">Creating the issuer certificate.</span></span>  
  
     <span data-ttu-id="e2fe2-159">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak yayıncı sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="e2fe2-160">`%USER_NAME%` Değişkeni, sertifika veren adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="e2fe2-161">Kendi verenin adı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="e2fe2-162">Alice bu toplu iş dosyasında varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-162">The default value in this batch file is Alice.</span></span>  
  
     <span data-ttu-id="e2fe2-163">Sertifika Currentuser'a depolama konumu altında My deposunda saklanır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-163">The certificate is stored in My store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="e2fe2-164">Sertifikayı sunucunun güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="e2fe2-165">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e2fe2-166">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e2fe2-167">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifika depolama veren sertifika ile doldurma, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e2fe2-168">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e2fe2-168">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="e2fe2-169">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2fe2-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e2fe2-170">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2fe2-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2fe2-171">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e2fe2-172">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e2fe2-172">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="e2fe2-173">Örnek yükleme klasöründen içinde Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-173">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="e2fe2-174">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-174">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2fe2-175">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-175">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="e2fe2-176">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-176">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="e2fe2-177">Service.exe service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="e2fe2-178">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e2fe2-179">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="e2fe2-180">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="e2fe2-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e2fe2-181">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e2fe2-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="e2fe2-182">Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="e2fe2-183">Hizmet program dosyalarını hizmeti bilgisayarında hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="e2fe2-184">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="e2fe2-185">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="e2fe2-186">Service.exe.config dosyayı bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="e2fe2-187">Sunucu sertifikası Setup.bat toplu iş dosyasını değiştirerek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="e2fe2-188">Setup.bat dosyasını yönetici ayrıcalıklarıyla açılmış bir Visual Studio komut istemi penceresinde çalıştırmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="e2fe2-189">Ayarlamalısınız `%SERVER_NAME%` değişken hizmet barındırmak için kullanılan bilgisayarın ana bilgisayar tam adı.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="e2fe2-190">Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="e2fe2-191">Sunucu sertifikasının güvenilen istemci veren tarafından verildiğinde bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="e2fe2-192">Hizmeti bilgisayarında Service.exe.config dosyasında localhost yerine bir tam bilgisayar adını belirtmek için taban adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="e2fe2-193">Hizmet bilgisayarda Service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="e2fe2-194">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="e2fe2-195">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="e2fe2-196">İstemci bilgisayarda, başlatma `Client.exe` bir komut istemi penceresinden.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="e2fe2-197">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="e2fe2-197">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e2fe2-198">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="e2fe2-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="e2fe2-199">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fe2-200">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-200">See Also</span></span>
