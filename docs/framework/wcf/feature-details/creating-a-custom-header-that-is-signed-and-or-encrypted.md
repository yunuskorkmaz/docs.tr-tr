---
title: İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0adb4100bca1add2c23ff2c802ddb5e2cb1c368c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579664"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma
WCF istemcisi kullanarak WCF olmayan bir hizmet çağrılırken, bazı durumlarda özel SOAP üstbilgileri kullanılması gerekir. WCF 'de imzalanmış ve şifrelenmiş özel üst bilgilerin WCF olmayan bir hizmetle çalışmasını önleyen bir kurallı kurallı hata vardır. Sorun, varsayılan XML ad alanlarının yanlış kurallı kullanım nedeniyle oluşur. Bu yalnızca, imzalanmış ve/veya şifrelenmiş özel üstbilgileriyle WCF olmayan hizmetler çağrılırken sorunlu olur.  Hizmet, imzalanmış ve/veya şifrelenmiş özel üstbilgiyi içeren iletiyi aldığında imzayı doğrulayamamıştır. Bu geçici çözüm, kurallı olmayan hizmetlerle birlikte çalışabilirliği sağlar, ancak WCF hizmetleriyle birlikte çalışabilirliği engellemez.  
  
## <a name="defining-the-custom-header"></a>Özel üstbilgiyi tanımlama  
 Özel üstbilgiler bir ileti sözleşmesi tanımlayarak ve bir öznitelik olarak göndermek istediğiniz Üyeler bir özniteliğiyle işaretlenerek tanımlanır <xref:System.ServiceModel.MessageHeaderAttribute> . Kurallı hata gidermek için, XML seri hale getiricinin varsayılan ad alanı bildirimi yerine ön ek içeren özel üstbilgi için ad alanını bildirdiğinden emin olmanız gerekir. Aşağıdaki kod, doğru ad alanı bildirimiyle bir ileti üst bilgisi olarak kullanılacak veri türünün nasıl tanımlanacağını gösterir.  
  
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
  
 Bu kod `msgHeaderElement` , XML serileştiriciyle seri hale getirilecek adlı yeni bir tür bildirir. Bu türden bir örnek serileştirildiğinde, ' h ' ön ekine sahip bir ad alanı tanımlar ve bu sayede kurallı hata etrafında çalışır.  İleti sözleşmesi daha sonra bir örneği tanımlar `msgHeaderElement` ve <xref:System.ServiceModel.MessageHeaderAttribute> Aşağıdaki örnekte gösterildiği gibi özniteliği ile işaretler.  
  
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

- [Varsayılan İleti Sözleşmesi](../samples/default-message-contract.md)
- [İleti Sözleşmeleri](../samples/message-contracts.md)
- [İleti Sözleşmeleri Kullanılıyor](using-message-contracts.md)
