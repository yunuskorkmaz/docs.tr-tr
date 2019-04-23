---
title: İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 76bfb6040f6b78765ed42ce7fbf86cdbd62c1e48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075654"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma
Bir WCF istemcisi kullanarak olmayan WCF Hizmeti çağrılırken bazen özel SOAP üstbilgileri kullanmak gereklidir. Wcf'de imzalanacak ve şifrelenecek özel üst bilgileri olmayan bir WCF Hizmeti ile çalışmasını engelleyen Standartlaştırma hata yoktur. Sorun, varsayılan XML ad alanları yanlış Standartlaştırma tarafından neden olur. Yalnızca imzalı ve/veya şifrelenmiş özel üst bilgileri olmayan WCF hizmetlerinde çağrılırken sorunlu budur.  Hizmet imzalanmış ve/veya şifrelenmiş özel üst bilgi içeren ileti aldığında imzası doğrulanamıyor. Bu geçici çözüm Standartlaştırma hatayı önler, olmayan WCF hizmetleri ile birlikte çalışabilirlik sağlar, ancak WCF hizmetleri ile birlikte çalışabilirlik engellemez.  
  
## <a name="defining-the-custom-header"></a>Özel üst bilgi tanımlama  
 Özel üst bilgiler tanımlanmış bir ileti sözleşmesi tanımlayarak ve üyelerini işaretleme sahip üst bilgi olarak gönderilmesini istediğiniz bir <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği. Standartlaştırma hataya çalışmak üzere XML serileştiriciyi özel üst bilgi ile bir varsayılan ad alanı bildirimi yerine bir önek için ad alanı bildirir emin olmanız gerekir. Aşağıdaki kod, doğru ad alanı bildirimi sahip bir ileti üst bilgisi olarak kullanılacak veri türü tanımlamak gösterilmektedir.  
  
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
  
 Bu kod olarak adlandırılan yeni bir tür bildirir `msgHeaderElement` , seri hale getirilemiyor ile XML serileştirici. Bu türün bir örneğini serileştirilmiş olduğunda, bu nedenle Standartlaştırma hataya çalışma 'h' ön eki, bir ad alanı tanımlar.  İleti anlaşması örneği tanımlarsınız `msgHeaderElement` ve kendisiyle işaretlemek <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği aşağıdaki örnekte gösterildiği gibi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan İleti Anlaşması](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [İleti Anlaşmaları](../../../../docs/framework/wcf/samples/message-contracts.md)
- [İleti Anlaşmaları Kullanma](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
