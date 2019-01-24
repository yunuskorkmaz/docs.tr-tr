---
title: Özel bir başlık oluşturma işaretli ve- veya şifreli
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0f8f86bcb5494cd502d14aff1cf3c4cdf4f8dd33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494827"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="3da8b-102">Özel bir başlık oluşturma işaretli ve- veya şifreli</span><span class="sxs-lookup"><span data-stu-id="3da8b-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="3da8b-103">Bir WCF istemcisi kullanarak olmayan WCF Hizmeti çağrılırken bazen özel SOAP üstbilgileri kullanmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="3da8b-104">Wcf'de imzalanacak ve şifrelenecek özel üst bilgileri olmayan bir WCF Hizmeti ile çalışmasını engelleyen Standartlaştırma hata yoktur.</span><span class="sxs-lookup"><span data-stu-id="3da8b-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="3da8b-105">Sorun, varsayılan XML ad alanları yanlış Standartlaştırma tarafından neden olur.</span><span class="sxs-lookup"><span data-stu-id="3da8b-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="3da8b-106">Yalnızca imzalı ve/veya şifrelenmiş özel üst bilgileri olmayan WCF hizmetlerinde çağrılırken sorunlu budur.</span><span class="sxs-lookup"><span data-stu-id="3da8b-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="3da8b-107">Hizmet imzalanmış ve/veya şifrelenmiş özel üst bilgi içeren ileti aldığında imzası doğrulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="3da8b-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="3da8b-108">Bu geçici çözüm Standartlaştırma hatayı önler, olmayan WCF hizmetleri ile birlikte çalışabilirlik sağlar, ancak WCF hizmetleri ile birlikte çalışabilirlik engellemez.</span><span class="sxs-lookup"><span data-stu-id="3da8b-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="3da8b-109">Özel üst bilgi tanımlama</span><span class="sxs-lookup"><span data-stu-id="3da8b-109">Defining the custom header</span></span>  
 <span data-ttu-id="3da8b-110">Özel üst bilgiler tanımlanmış bir ileti sözleşmesi tanımlayarak ve üyelerini işaretleme sahip üst bilgi olarak gönderilmesini istediğiniz bir <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3da8b-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="3da8b-111">Standartlaştırma hataya çalışmak üzere XML serileştiriciyi özel üst bilgi ile bir varsayılan ad alanı bildirimi yerine bir önek için ad alanı bildirir emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="3da8b-112">Aşağıdaki kod, doğru ad alanı bildirimi sahip bir ileti üst bilgisi olarak kullanılacak veri türü tanımlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="3da8b-113">Bu kod olarak adlandırılan yeni bir tür bildirir `msgHeaderElement` , seri hale getirilemiyor ile XML serileştirici.</span><span class="sxs-lookup"><span data-stu-id="3da8b-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="3da8b-114">Bu türün bir örneğini serileştirilmiş olduğunda, bu nedenle Standartlaştırma hataya çalışma 'h' ön eki, bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3da8b-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="3da8b-115">İleti anlaşması örneği tanımlarsınız `msgHeaderElement` ve kendisiyle işaretlemek <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3da8b-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3da8b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3da8b-116">See also</span></span>
- [<span data-ttu-id="3da8b-117">Varsayılan İleti Anlaşması</span><span class="sxs-lookup"><span data-stu-id="3da8b-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [<span data-ttu-id="3da8b-118">İleti Anlaşmaları</span><span class="sxs-lookup"><span data-stu-id="3da8b-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)
- [<span data-ttu-id="3da8b-119">İleti Anlaşmaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3da8b-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
