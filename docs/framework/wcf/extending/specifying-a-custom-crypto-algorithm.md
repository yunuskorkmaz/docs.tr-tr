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
# <a name="specifying-a-custom-crypto-algorithm"></a>Özel Bir Şifreleme Algoritması Belirtme
WCF kullanmak üzere özel bir şifreleme algoritması belirtmenize olanak verir veri şifrelemek veya bilgi işlem dijital imzalar. Bu, aşağıdaki adımlarla gerçekleştirilir:  
  
1.  Öğesinden bir sınıf türetin <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  Algoritma kaydetme  
  
3.  Bağlamasıyla yapılandırma <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-türetilmiş sınıf.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>SecurityAlgorithmSuite bir sınıf türetin  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Algoritması, çeşitli güvenlikle ilgili işlemler yapılırken kullanılacak belirtmenizi sağlar bir soyut temel sınıf. Örneğin, bir dijital imza veya iletiyi şifrelemek için karma hesaplaması. Aşağıdaki kod, bir sınıf türetmek gösterilmektedir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
  
## <a name="register-the-custom-algorithm"></a>Özel algoritması kaydetme  
 Kayıt, yapılandırma dosyasında veya kesinlik temelli kod içinde yapılabilir. Özel bir algoritma kaydetme, şifreleme hizmeti sağlayıcısı uygulayan bir sınıf ve bir diğer ad arasında bir eşleme oluşturarak yapılır. Diğer ad daha sonra algoritması WCF hizmet bağlama belirtme sırasında kullanılan bir URI eşleştirilir. Aşağıdaki yapılandırma kod parçacığı bir özel algoritması yapılandırmada kaydetme gösterilmektedir:  
  
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
  
 Bölümü altında <`cryptoClasses`> öğesi SHA256CryptoServiceProvider "SHA256CSP" diğer ad arasında eşleme oluşturur. <`nameEntry`> Öğesi "SHA256CSP" diğer ad ile belirtilen URL arasındaki eşlemeyi oluşturur (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 Özel algoritması kodu kullanımda kaydedilecek <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> yöntemi. Bu yöntem, her iki eşlemeleri oluşturur. Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını gösterir:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Bağlama yapılandırma  
 Özel belirterek bağlama yapılandırma <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-aşağıdaki kod parçacığında gösterildiği gibi türetilmiş sınıf bağlama ayarları:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Tam kod örneği için bkz: [WCF güvenliğinde şifreleme çevikliği](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) örnek.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Hizmetleri Güvenli Hale Getirme](../../../../docs/framework/wcf/securing-services.md)
- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)
