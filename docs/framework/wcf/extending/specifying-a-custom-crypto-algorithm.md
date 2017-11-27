---
title: "Özel Bir Şifreleme Algoritması Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 630457e4d1b30fe2a9439c3a41af5da92606c55a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Özel Bir Şifreleme Algoritması Belirtme
WCF kullanmak üzere özel bir şifreleme algoritması belirtmenize olanak verir veri şifrelemek veya dijital imzalar bilgi işlem. Bu, aşağıdaki adımlarla gerçekleştirilir:  
  
1.  Öğesinden bir sınıf türetin<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  Algoritma kaydetme  
  
3.  Bağlama ile yapılandırma <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-türetilmiş sınıf.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>SecurityAlgorithmSuite bir sınıf türetin  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Çeşitli güvenlik gerçekleştirme işlemleri işlerken kullanılacak algoritmayı belirtmenize olanak sağlayan bir Özet temel sınıf. Örneğin, bir dijital imza veya iletiyi şifrelemek için bir karma hesaplama. Aşağıdaki kod öğesinden bir sınıf türetin gösterilmektedir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
 Kayıt bir yapılandırma dosyası veya kesinlik temelli kod yapılabilir. Özel bir algoritma kaydetme bir şifreleme hizmeti sağlayıcısı uygulayan bir sınıf ve bir diğer ad arasında bir eşleme oluşturarak yapılır. Diğer adı daha sonra algoritması WCF hizmet bağlama belirtme sırasında kullanılan bir URI eşleştirilir. Aşağıdaki yapılandırma parçacığını nasıl özel bir algoritma yapılandırma dosyasına kaydedileceği gösterilmektedir:  
  
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
  
 Bölümü altında <`cryptoClasses`> öğesi SHA256CryptoServiceProvider ve diğer adı "SHA256CSP" arasında eşleme oluşturur. <`nameEntry`> Öğesi "SHA256CSP" diğer adını ve belirtilen URL'yi (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm) arasındaki eşleştirmeyi oluşturur.  
  
 Özel algoritması kodu kullanımda kaydetmek için <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm%2A> System.String[])?qualifyHint=False & autoUpgrade = True yöntemi. Bu yöntem, her iki eşlemeleri oluşturur. Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını gösterir:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Bağlama yapılandırma  
 Özel belirterek bağını yapılandırmak <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-aşağıdaki kod parçacığında gösterildiği gibi türetilmiş sınıf bağlama ayarları'nda:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Tam kod örneği için bkz: [WCF güvenliğinde şifreleme çevikliği](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) örnek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Hizmetleri güvenli hale getirme](../../../../docs/framework/wcf/securing-services.md)  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Güvenlik kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)
