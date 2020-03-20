---
title: Özel Bir Şifreleme Algoritması Belirtme
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186482"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Özel Bir Şifreleme Algoritması Belirtme
WCF, verileri şifrelerken veya dijital imzaları hesaplarken kullanmak üzere özel bir şifreleme algoritması belirtmenize olanak tanır. Bu, aşağıdaki adımlarla yapılır:  
  
1. Bir sınıf türetme<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Algoritmayı kaydedin  
  
3. Bağlayıcıyı <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türetilmiş sınıfla yapılandırın.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>SecurityAlgorithmSuite'ten bir sınıf türetin  
 Çeşitli <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> güvenlik le ilgili işlemleri gerçekleştirirken kullanılacak algoritmayı belirtmenize olanak tanıyan soyut bir taban sınıftır. Örneğin, dijital imza için karma hesaplama veya bir iletiyi şifreleme. Aşağıdaki kod, bir sınıfın nasıl <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türetileni gösterir:  
  
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
  
## <a name="register-the-custom-algorithm"></a>Özel Algoritmayı Kaydedin  
 Kayıt bir yapılandırma dosyasında veya zorunlu kodda yapılabilir. Özel bir algoritmayı kaydetme, bir kripto hizmet sağlayıcısı ve takma ad uygulayan bir sınıf arasında eşleme oluşturarak yapılır. Takma ad daha sonra WCF hizmetinin bağlama algoritması belirtilirken kullanılan bir URI eşlenir. Aşağıdaki yapılandırma snippet config özel bir algoritma nasıl kaydolunacağını göstermektedir:  
  
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
  
 <`cryptoClasses`> öğesi altındaki bölüm SHA256CryptoServiceProvider ve takma adı "SHA256CSP" arasında eşleme oluşturur. <`nameEntry`> öğesi "SHA256CSP" diğer adı ile belirtilen URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`arasındaki eşlemi oluşturur.  
  
 Özel algoritmayı koda kaydetmek <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> için yöntemi kullanın. Bu yöntem her iki eşleme oluşturur. Aşağıdaki örnek, bu yöntemin nasıl çağrıldığını gösterir:  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Bağlamayı Yapılandır  
 Aşağıdaki kod snippet gösterildiği <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>gibi bağlama ayarlarında özel türemiş sınıf belirterek bağlama yapılandırırsınız:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Tam bir kod örneği için [WCF Security örneğindeki Şifreleme Çevikliği'ne](../samples/cryptographic-agility-in-wcf-security.md) bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet ve İstemcileri Güvenli Hale Getirme](../feature-details/securing-services-and-clients.md)
- [Hizmetleri Güvenli Hale Getirme](../securing-services.md)
- [Güvenliğe Genel Bakış](../feature-details/security-overview.md)
- [Güvenlik Kavramları](../feature-details/security-concepts.md)
