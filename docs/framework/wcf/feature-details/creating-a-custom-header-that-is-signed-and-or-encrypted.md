---
title: "Özel bir başlık oluşturma imzalandığından ve- veya şifrelenmiş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d637dfaa4b3639d1e47280c423489735844a2a47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Özel bir başlık oluşturma imzalandığından ve- veya şifrelenmiş
WCF istemcisi kullanarak bir WCF olmayan hizmeti çağrılırken bazen özel SOAP üstbilgileri kullanmak gereklidir. İmzalanabilir ve şifrelenebilir özel üstbilgileri olmayan WCF Hizmeti ile çalışmasını engelleyen WCF Standartlaştırma hata yoktur. Sorun varsayılan XML ad alanları yanlış Standartlaştırma tarafından kaynaklanır. Bu yalnızca olmayan WCF hizmetleri ile imzalanmış ve/veya şifrelenmiş özel üstbilgileri çağrılırken sorunlu oluşturur.  Hizmeti imzalanmış ve/veya şifrelenmiş özel üstbilgi içeren ileti aldığında imzayı doğrulamak alamıyor. Bu geçici çözüm Standartlaştırma hatayı ortadan kaldırır, WCF olmayan Hizmetleri ile birlikte çalışabilirlik sağlar, ancak WCF hizmetleri ile birlikte çalışabilirlik engellemez.  
  
## <a name="defining-the-custom-header"></a>Özel Başlık tanımlama  
 Özel üstbilgi tanımlanmış bir ileti sözleşmesi tanımlayarak ve ile başlığı olarak gönderilmesini istediğiniz üyeleri işaretleme bir <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği. Standartlaştırma hata olarak çözmek için XML serileştiriciyi ad alanı için bir varsayılan ad alanı bildiriminin yerine bir önek ile özel üstbilgi bildirir emin olmalısınız. Aşağıdaki kodu, doğru ad alanı bildirimi sahip bir ileti üstbilgisi olarak kullanılan veri türünü tanımlayın gösterilmektedir.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 Bu kod adlı yeni bir tür bildirir `msgHeaderElement` , serileştirilen ile XML serileştirici. Bu tür bir örneğini serileştirilmiş, böylece Standartlaştırma hata çalışma bir 'h' öneki içeren bir ad tanımlar.  İleti sözleşmesi örneği tanımlarsınız `msgHeaderElement` ve ile işaretleyin <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği aşağıdaki örnekte gösterildiği gibi.  
  
```  
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varsayılan ileti sözleşmesi](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [İleti sözleşmeleri](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [İleti sözleşmeleri kullanılıyor](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
