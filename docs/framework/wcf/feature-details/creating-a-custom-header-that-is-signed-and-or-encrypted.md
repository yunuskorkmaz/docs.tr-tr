---
title: İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: d737647f8c0442a3d6fa0d077a1ffe2c251ea043
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856180"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma
WCF istemcisi kullanarak WCF olmayan bir hizmet çağrılırken, bazı durumlarda özel SOAP üstbilgileri kullanılması gerekir. WCF 'de imzalanmış ve şifrelenmiş özel üst bilgilerin WCF olmayan bir hizmetle çalışmasını önleyen bir kurallı kurallı hata vardır. Sorun, varsayılan XML ad alanlarının yanlış kurallı kullanım nedeniyle oluşur. Bu yalnızca, imzalanmış ve/veya şifrelenmiş özel üstbilgileriyle WCF olmayan hizmetler çağrılırken sorunlu olur.  Hizmet, imzalanmış ve/veya şifrelenmiş özel üstbilgiyi içeren iletiyi aldığında imzayı doğrulayamamıştır. Bu geçici çözüm, kurallı olmayan hizmetlerle birlikte çalışabilirliği sağlar, ancak WCF hizmetleriyle birlikte çalışabilirliği engellemez.  
  
## <a name="defining-the-custom-header"></a>Özel üstbilgiyi tanımlama  
 Özel üstbilgiler bir ileti sözleşmesi tanımlayarak ve bir öznitelik olarak göndermek istediğiniz Üyeler bir <xref:System.ServiceModel.MessageHeaderAttribute> özniteliğiyle işaretlenerek tanımlanır. Kurallı hata gidermek için, XML seri hale getiricinin varsayılan ad alanı bildirimi yerine ön ek içeren özel üstbilgi için ad alanını bildirdiğinden emin olmanız gerekir. Aşağıdaki kod, doğru ad alanı bildirimiyle bir ileti üst bilgisi olarak kullanılacak veri türünün nasıl tanımlanacağını gösterir.  
  
```csharp
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
  
 Bu kod, XML serileştiriciyle `msgHeaderElement` seri hale getirilecek adlı yeni bir tür bildirir. Bu türden bir örnek serileştirildiğinde, ' h ' ön ekine sahip bir ad alanı tanımlar ve bu sayede kurallı hata etrafında çalışır.  İleti sözleşmesi daha sonra bir örneği `msgHeaderElement` tanımlar ve aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği ile işaretler.  
  
```csharp
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
