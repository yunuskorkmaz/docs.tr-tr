---
title: SAML Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 509469404e2c3866c26b5e1817a819519203c175
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747853"
---
# <a name="saml-token-provider"></a><span data-ttu-id="60c89-102">SAML Belirteç Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="60c89-102">SAML Token Provider</span></span>
<span data-ttu-id="60c89-103">Bu örnek nasıl özel bir istemci SAML belirteç sağlayıcı uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="60c89-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="60c89-104">Windows Communication Foundation (WCF) bir belirteç sağlayıcısı güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60c89-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="60c89-105">Belirteç sağlayıcı genel hedef inceler ve böylece ileti güvenlik altyapısı güvenli hale getirebilirsiniz, kimlik bilgileri sorunları uygun.</span><span class="sxs-lookup"><span data-stu-id="60c89-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="60c89-106">WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="60c89-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="60c89-107">WCF ayrıca ile birlikte gelir bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="60c89-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="60c89-108">Özel belirteç sağlayıcıları, aşağıdaki durumlarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="60c89-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="60c89-109">Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="60c89-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="60c89-110">Kullanıcı için WCF istemci framework kimlik bilgileri kullandığında ayrıntıları sağladığında noktadan kimlik dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="60c89-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="60c89-111">Özel belirteç oluşturuluyorsa.</span><span class="sxs-lookup"><span data-stu-id="60c89-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="60c89-112">Bu örnek nasıl kullanılacak WCF istemci framework dışında alınan bir SAML belirtecine izin veren özel bir belirteç sağlayıcısını oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="60c89-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>  
  
 <span data-ttu-id="60c89-113">Özetlemek gerekirse, bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="60c89-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="60c89-114">Nasıl bir istemci özel bir belirteç sağlayıcısı ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="60c89-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="60c89-115">SAML belirteci için özel istemci kimlik bilgilerini nasıl geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="60c89-115">How a SAML token can be passed to the custom client credentials.</span></span>  
  
-   <span data-ttu-id="60c89-116">SAML belirteci WCF istemci framework nasıl sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60c89-116">How the SAML token is provided to the WCF client framework.</span></span>  
  
-   <span data-ttu-id="60c89-117">Sunucu, sunucunun X.509 sertifikası kullanarak istemci tarafından nasıl doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="60c89-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="60c89-118">Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için iki uç noktalarını kullanıma sunar. Her uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="60c89-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="60c89-119">Bir standart yapılandırılmış bağlama `wsFederationHttpBinding`, ileti güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="60c89-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="60c89-120">Bir uç nokta düzeltme simetrik anahtar diğer bir asimetrik sağlama anahtarı kullanan bir SAML belirteci kimlik doğrulaması için istemci beklediği sırada kullanan bir SAML belirteci ile kimlik doğrulaması için istemci bekliyor.</span><span class="sxs-lookup"><span data-stu-id="60c89-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="60c89-121">Hizmet Ayrıca hizmet kullanarak sertifikayı yapılandırır `serviceCredentials` davranışı.</span><span class="sxs-lookup"><span data-stu-id="60c89-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="60c89-122">`serviceCredentials` Davranışı bir hizmet sertifikası yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="60c89-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="60c89-123">Bir hizmet sertifikası, hizmet kimlik doğrulaması ve ileti koruma sağlamak için bir istemci tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60c89-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="60c89-124">Aşağıdaki yapılandırma, bu konunun sonunda Kurulum yönergelerinde açıklandığı gibi örnek Kurulum sırasında yüklenen "localhost" sertifikanın başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="60c89-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="60c89-125">`serviceCredentials` Davranışı da SAML belirteçlerini imzalamak için güvenilen sertifikalar yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="60c89-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="60c89-126">Aşağıdaki yapılandırma sırasında bir örnek yüklü 'Alice' sertifika başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="60c89-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>  
  
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
  
 <span data-ttu-id="60c89-127">Aşağıdaki adımlarda, bir özel SAML belirteç sağlayıcı geliştirin ve WCF ile tümleştirmek gösterilmektedir: güvenlik çerçevesi:</span><span class="sxs-lookup"><span data-stu-id="60c89-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>  
  
1.  <span data-ttu-id="60c89-128">Bir özel SAML belirteç sağlayıcı yazma.</span><span class="sxs-lookup"><span data-stu-id="60c89-128">Write a custom SAML token provider.</span></span>  
  
     <span data-ttu-id="60c89-129">Örnek oluşturma zamanında sağlanan bir SAML onaylama işlemi temel bir güvenlik belirteci döndüren bir özel SAML belirteç sağlayıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="60c89-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>  
  
     <span data-ttu-id="60c89-130">Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı türetilir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıf ve geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="60c89-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="60c89-131">Bu yöntem, oluşturur ve yeni bir `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="60c89-131">This method creates and returns a new `SecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="60c89-132">Özel güvenlik belirteci Yöneticisi'ni yazın.</span><span class="sxs-lookup"><span data-stu-id="60c89-132">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="60c89-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Sınıfı oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="60c89-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="60c89-134">Bir güvenlik belirteci Yöneticisi ayrıca belirteç Doğrulayıcı ve belirteç serializer özelliği oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="60c89-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="60c89-135">Bu örnek özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri belirttiğinizde, SAML belirteci özel SAML belirteç sağlayıcı döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="60c89-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="60c89-136">İstemci kimlik bilgileri sınıfı (3. adıma bakın) onaylama belirtilmemişse, güvenlik belirteci yöneticisi uygun bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60c89-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>  
  
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
  
3.  <span data-ttu-id="60c89-137">Özel istemci kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="60c89-137">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="60c89-138">İstemci kimlik bilgileri sınıfı istemci proxy'si için yapılandırıldığında kimlik bilgilerini temsil etmek için kullanılır ve bir güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteç serializer özelliği almak için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60c89-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>  
  
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
  
4.  <span data-ttu-id="60c89-139">Özel istemci kimlik bilgilerini kullanacak biçimde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="60c89-139">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="60c89-140">Örnek, varsayılan istemci kimlik bilgisi sınıfını siler ve istemci özel bir istemci kimlik bilgileri kullanabilmeniz için yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c89-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>  
  
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
  
 <span data-ttu-id="60c89-141">Hizmet arayanla ilişkili talep görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="60c89-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="60c89-142">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="60c89-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="60c89-143">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="60c89-143">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="60c89-144">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="60c89-144">Setup Batch File</span></span>  
 <span data-ttu-id="60c89-145">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c89-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="60c89-146">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="60c89-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="60c89-147">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="60c89-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="60c89-148">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="60c89-148">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="60c89-149">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60c89-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="60c89-150">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c89-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="60c89-151">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="60c89-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="60c89-152">Localhost bu toplu iş dosyasında varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="60c89-152">The default value in this batch file is localhost.</span></span>  
  
     <span data-ttu-id="60c89-153">Sertifikayı LocalMachine depolama konumu altında (Kişisel) My deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="60c89-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="60c89-154">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:</span><span class="sxs-lookup"><span data-stu-id="60c89-154">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="60c89-155">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="60c89-156">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60c89-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="60c89-157">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="60c89-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="60c89-158">Verenin sertifika oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="60c89-158">Creating the issuer certificate.</span></span>  
  
     <span data-ttu-id="60c89-159">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sertifikayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60c89-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="60c89-160">`%USER_NAME%` Değişkeni sertifikayı verenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="60c89-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="60c89-161">Kendi verenin adı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="60c89-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="60c89-162">Alice bu toplu iş dosyasında varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="60c89-162">The default value in this batch file is Alice.</span></span>  
  
     <span data-ttu-id="60c89-163">Sertifika CurrentUser depolama konumu altında My deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="60c89-163">The certificate is stored in My store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="60c89-164">Sertifikayı sunucusunun güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="60c89-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="60c89-165">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="60c89-166">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60c89-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="60c89-167">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sertifikayı ile sunucu sertifika deposuna yerleştirmek, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="60c89-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="60c89-168">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="60c89-168">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="60c89-169">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60c89-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="60c89-170">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60c89-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60c89-171">Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.</span><span class="sxs-lookup"><span data-stu-id="60c89-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="60c89-172">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="60c89-172">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="60c89-173">Setup.bat içinde örnek yükleme klasöründen çalıştırın bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="60c89-173">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="60c89-174">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="60c89-174">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="60c89-175">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="60c89-175">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="60c89-176">İçinde PATH ortam değişkenini ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="60c89-176">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="60c89-177">Service.exe service\bin ' başlatın.</span><span class="sxs-lookup"><span data-stu-id="60c89-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="60c89-178">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="60c89-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="60c89-179">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="60c89-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="60c89-180">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="60c89-180">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="60c89-181">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="60c89-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="60c89-182">Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="60c89-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="60c89-183">Hizmet program dosyaları hizmeti bilgisayarında hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="60c89-184">Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="60c89-185">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60c89-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="60c89-186">Service.exe.config dosyayı bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="60c89-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="60c89-187">Setup.bat toplu iş dosyasını değiştirerek, sunucu sertifikası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60c89-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="60c89-188">Yönetici ayrıcalıklarıyla açılan bir Visual Studio komut istemi penceresinde setup.bat dosyasının çalıştırılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="60c89-189">Ayarlamalısınız `%SERVER_NAME%` değişken hizmeti barındırmak için kullanılan bilgisayarın tam ana bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="60c89-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="60c89-190">Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="60c89-191">Sunucu sertifikası güvenilir istemci veren tarafından verildiğinde, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="60c89-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="60c89-192">Hizmet bilgisayarı Service.exe.config dosyada localhost yerine tam bilgisayar adını belirtmek için temel adresini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="60c89-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="60c89-193">Hizmet bilgisayarda Service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="60c89-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="60c89-194">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="60c89-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="60c89-195">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="60c89-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="60c89-196">İstemci bilgisayarda Başlat `Client.exe` bir komut istemi penceresinden.</span><span class="sxs-lookup"><span data-stu-id="60c89-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="60c89-197">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="60c89-197">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="60c89-198">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="60c89-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="60c89-199">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="60c89-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c89-200">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60c89-200">See Also</span></span>
