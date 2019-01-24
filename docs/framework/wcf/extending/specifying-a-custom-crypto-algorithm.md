---
title: Özel Bir Şifreleme Algoritması Belirtme
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 5c7bddb7e6e1696ea1cb4f8359e34a51a89fce40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537692"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="e827a-102">Özel Bir Şifreleme Algoritması Belirtme</span><span class="sxs-lookup"><span data-stu-id="e827a-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="e827a-103">WCF kullanmak üzere özel bir şifreleme algoritması belirtmenize olanak verir veri şifrelemek veya bilgi işlem dijital imzalar.</span><span class="sxs-lookup"><span data-stu-id="e827a-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="e827a-104">Bu, aşağıdaki adımlarla gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="e827a-104">This is done by the following steps:</span></span>  
  
1.  <span data-ttu-id="e827a-105">Öğesinden bir sınıf türetin <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="e827a-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2.  <span data-ttu-id="e827a-106">Algoritma kaydetme</span><span class="sxs-lookup"><span data-stu-id="e827a-106">Register the algorithm</span></span>  
  
3.  <span data-ttu-id="e827a-107">Bağlamasıyla yapılandırma <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="e827a-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="e827a-108">SecurityAlgorithmSuite bir sınıf türetin</span><span class="sxs-lookup"><span data-stu-id="e827a-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="e827a-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Algoritması, çeşitli güvenlikle ilgili işlemler yapılırken kullanılacak belirtmenizi sağlar bir soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="e827a-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="e827a-110">Örneğin, bir dijital imza veya iletiyi şifrelemek için karma hesaplaması.</span><span class="sxs-lookup"><span data-stu-id="e827a-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="e827a-111">Aşağıdaki kod, bir sınıf türetmek gösterilmektedir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span><span class="sxs-lookup"><span data-stu-id="e827a-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
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
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="e827a-112">Özel algoritması kaydetme</span><span class="sxs-lookup"><span data-stu-id="e827a-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="e827a-113">Kayıt, yapılandırma dosyasında veya kesinlik temelli kod içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="e827a-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="e827a-114">Özel bir algoritma kaydetme, şifreleme hizmeti sağlayıcısı uygulayan bir sınıf ve bir diğer ad arasında bir eşleme oluşturarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="e827a-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="e827a-115">Diğer ad daha sonra algoritması WCF hizmet bağlama belirtme sırasında kullanılan bir URI eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e827a-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="e827a-116">Aşağıdaki yapılandırma kod parçacığı bir özel algoritması yapılandırmada kaydetme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e827a-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="e827a-117">Bölümü altında <`cryptoClasses`> öğesi SHA256CryptoServiceProvider "SHA256CSP" diğer ad arasında eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e827a-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="e827a-118"><`nameEntry`> Öğesi "SHA256CSP" diğer ad ile belirtilen URL arasındaki eşlemeyi oluşturur (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span><span class="sxs-lookup"><span data-stu-id="e827a-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="e827a-119">Özel algoritması kodu kullanımda kaydedilecek <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e827a-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="e827a-120">Bu yöntem, her iki eşlemeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e827a-120">This method creates both mappings.</span></span> <span data-ttu-id="e827a-121">Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e827a-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="e827a-122">Bağlama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e827a-122">Configure the Binding</span></span>  
 <span data-ttu-id="e827a-123">Özel belirterek bağlama yapılandırma <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-aşağıdaki kod parçacığında gösterildiği gibi türetilmiş sınıf bağlama ayarları:</span><span class="sxs-lookup"><span data-stu-id="e827a-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="e827a-124">Tam kod örneği için bkz: [WCF güvenliğinde şifreleme çevikliği](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e827a-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e827a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e827a-125">See also</span></span>
- [<span data-ttu-id="e827a-126">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e827a-126">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e827a-127">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e827a-127">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="e827a-128">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e827a-128">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="e827a-129">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="e827a-129">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
