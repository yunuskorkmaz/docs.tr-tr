---
description: 'Hakkında daha fazla bilgi edinin: özel bir şifre algoritması belirtme'
title: Özel Bir Şifreleme Algoritması Belirtme
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 4d4cb525b46b33a0d0df8dd6a3db9e9fafe84f8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643975"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="6dce3-103">Özel Bir Şifreleme Algoritması Belirtme</span><span class="sxs-lookup"><span data-stu-id="6dce3-103">Specifying a Custom Crypto Algorithm</span></span>

<span data-ttu-id="6dce3-104">WCF, verileri şifrelerken veya dijital imzaları hesaplarken kullanılacak özel bir şifre algoritması belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6dce3-104">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="6dce3-105">Bu işlem aşağıdaki adımlarla yapılır:</span><span class="sxs-lookup"><span data-stu-id="6dce3-105">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="6dce3-106">Öğesinden bir sınıf türet <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="6dce3-106">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="6dce3-107">Algoritmayı kaydetme</span><span class="sxs-lookup"><span data-stu-id="6dce3-107">Register the algorithm</span></span>  
  
3. <span data-ttu-id="6dce3-108">Bağlamayı <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> türetilmiş sınıfla yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="6dce3-108">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="6dce3-109">SecurityAlgorithmSuite 'ten bir sınıf türet</span><span class="sxs-lookup"><span data-stu-id="6dce3-109">Derive a class from SecurityAlgorithmSuite</span></span>  

 <span data-ttu-id="6dce3-110">, <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Güvenlikle ilgili çeşitli işlemler gerçekleştirirken kullanılacak algoritmayı belirtmenize olanak tanıyan soyut bir temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="6dce3-110">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="6dce3-111">Örneğin, dijital imza için bir karma hesaplama veya bir iletiyi şifreleme.</span><span class="sxs-lookup"><span data-stu-id="6dce3-111">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="6dce3-112">Aşağıdaki kod, öğesinden bir sınıfın nasıl türetileceğini göstermektedir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> :</span><span class="sxs-lookup"><span data-stu-id="6dce3-112">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="6dce3-113">Özel algoritmayı Kaydet</span><span class="sxs-lookup"><span data-stu-id="6dce3-113">Register the Custom Algorithm</span></span>  

 <span data-ttu-id="6dce3-114">Kayıt, bir yapılandırma dosyasında ya da kesinlik bir kod içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="6dce3-114">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="6dce3-115">Bir özel algoritmayı kaydetmek, bir şifreleme hizmeti sağlayıcısı ve diğer ad uygulayan bir sınıf arasında eşleme oluşturularak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6dce3-115">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="6dce3-116">Diğer ad daha sonra WCF hizmeti bağlamasındaki algoritmayı belirtirken kullanılan bir URI ile eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6dce3-116">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="6dce3-117">Aşağıdaki yapılandırma kod parçacığında özel bir algoritmanın config 'e nasıl kaydedileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6dce3-117">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://contoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="6dce3-118"><> öğesinin altındaki bölüm `cryptoClasses` , SHA256CryptoServiceProvider ve "SHA256CSP" diğer adı arasında eşlemeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dce3-118">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="6dce3-119"><`nameEntry`> öğesi, "SHA256CSP" diğer adı ve BELIRTILEN URL arasında eşleme oluşturur `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="6dce3-119">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="6dce3-120">Özel algoritmayı kodda kaydetmek için <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6dce3-120">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="6dce3-121">Bu yöntem her iki eşlemeyi de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dce3-121">This method creates both mappings.</span></span> <span data-ttu-id="6dce3-122">Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6dce3-122">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://contoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="6dce3-123">Bağlamayı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6dce3-123">Configure the Binding</span></span>  

 <span data-ttu-id="6dce3-124">Bağlama <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> ayarlarında, aşağıdaki kod parçacığında gösterildiği gibi özel türetilmiş sınıfı belirterek bağlamayı yapılandırırsınız:</span><span class="sxs-lookup"><span data-stu-id="6dce3-124">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="6dce3-125">Tüm kod örnekleri için bkz. [WCF güvenlik örneğindeki şifreleme çevikliği](../samples/cryptographic-agility-in-wcf-security.md) .</span><span class="sxs-lookup"><span data-stu-id="6dce3-125">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dce3-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dce3-126">See also</span></span>

- [<span data-ttu-id="6dce3-127">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6dce3-127">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6dce3-128">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6dce3-128">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="6dce3-129">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="6dce3-129">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="6dce3-130">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="6dce3-130">Security Concepts</span></span>](../feature-details/security-concepts.md)
