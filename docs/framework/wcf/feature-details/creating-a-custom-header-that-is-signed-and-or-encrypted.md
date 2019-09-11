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
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="939f9-102">İmzalanmış ve/veya şifrelenmiş özel bir başlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="939f9-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="939f9-103">WCF istemcisi kullanarak WCF olmayan bir hizmet çağrılırken, bazı durumlarda özel SOAP üstbilgileri kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="939f9-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="939f9-104">WCF 'de imzalanmış ve şifrelenmiş özel üst bilgilerin WCF olmayan bir hizmetle çalışmasını önleyen bir kurallı kurallı hata vardır.</span><span class="sxs-lookup"><span data-stu-id="939f9-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="939f9-105">Sorun, varsayılan XML ad alanlarının yanlış kurallı kullanım nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="939f9-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="939f9-106">Bu yalnızca, imzalanmış ve/veya şifrelenmiş özel üstbilgileriyle WCF olmayan hizmetler çağrılırken sorunlu olur.</span><span class="sxs-lookup"><span data-stu-id="939f9-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="939f9-107">Hizmet, imzalanmış ve/veya şifrelenmiş özel üstbilgiyi içeren iletiyi aldığında imzayı doğrulayamamıştır.</span><span class="sxs-lookup"><span data-stu-id="939f9-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="939f9-108">Bu geçici çözüm, kurallı olmayan hizmetlerle birlikte çalışabilirliği sağlar, ancak WCF hizmetleriyle birlikte çalışabilirliği engellemez.</span><span class="sxs-lookup"><span data-stu-id="939f9-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="939f9-109">Özel üstbilgiyi tanımlama</span><span class="sxs-lookup"><span data-stu-id="939f9-109">Defining the custom header</span></span>  
 <span data-ttu-id="939f9-110">Özel üstbilgiler bir ileti sözleşmesi tanımlayarak ve bir öznitelik olarak göndermek istediğiniz Üyeler bir <xref:System.ServiceModel.MessageHeaderAttribute> özniteliğiyle işaretlenerek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="939f9-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="939f9-111">Kurallı hata gidermek için, XML seri hale getiricinin varsayılan ad alanı bildirimi yerine ön ek içeren özel üstbilgi için ad alanını bildirdiğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="939f9-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="939f9-112">Aşağıdaki kod, doğru ad alanı bildirimiyle bir ileti üst bilgisi olarak kullanılacak veri türünün nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="939f9-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="939f9-113">Bu kod, XML serileştiriciyle `msgHeaderElement` seri hale getirilecek adlı yeni bir tür bildirir.</span><span class="sxs-lookup"><span data-stu-id="939f9-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="939f9-114">Bu türden bir örnek serileştirildiğinde, ' h ' ön ekine sahip bir ad alanı tanımlar ve bu sayede kurallı hata etrafında çalışır.</span><span class="sxs-lookup"><span data-stu-id="939f9-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="939f9-115">İleti sözleşmesi daha sonra bir örneği `msgHeaderElement` tanımlar ve aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği ile işaretler.</span><span class="sxs-lookup"><span data-stu-id="939f9-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="939f9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="939f9-116">See also</span></span>

- [<span data-ttu-id="939f9-117">Varsayılan İleti Anlaşması</span><span class="sxs-lookup"><span data-stu-id="939f9-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [<span data-ttu-id="939f9-118">İleti Anlaşmaları</span><span class="sxs-lookup"><span data-stu-id="939f9-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)
- [<span data-ttu-id="939f9-119">İleti Anlaşmaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="939f9-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
