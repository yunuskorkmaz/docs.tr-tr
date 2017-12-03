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
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="02c4f-102">Özel bir başlık oluşturma imzalandığından ve- veya şifrelenmiş</span><span class="sxs-lookup"><span data-stu-id="02c4f-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="02c4f-103">WCF istemcisi kullanarak bir WCF olmayan hizmeti çağrılırken bazen özel SOAP üstbilgileri kullanmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="02c4f-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="02c4f-104">İmzalanabilir ve şifrelenebilir özel üstbilgileri olmayan WCF Hizmeti ile çalışmasını engelleyen WCF Standartlaştırma hata yoktur.</span><span class="sxs-lookup"><span data-stu-id="02c4f-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="02c4f-105">Sorun varsayılan XML ad alanları yanlış Standartlaştırma tarafından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="02c4f-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="02c4f-106">Bu yalnızca olmayan WCF hizmetleri ile imzalanmış ve/veya şifrelenmiş özel üstbilgileri çağrılırken sorunlu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02c4f-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="02c4f-107">Hizmeti imzalanmış ve/veya şifrelenmiş özel üstbilgi içeren ileti aldığında imzayı doğrulamak alamıyor.</span><span class="sxs-lookup"><span data-stu-id="02c4f-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="02c4f-108">Bu geçici çözüm Standartlaştırma hatayı ortadan kaldırır, WCF olmayan Hizmetleri ile birlikte çalışabilirlik sağlar, ancak WCF hizmetleri ile birlikte çalışabilirlik engellemez.</span><span class="sxs-lookup"><span data-stu-id="02c4f-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="02c4f-109">Özel Başlık tanımlama</span><span class="sxs-lookup"><span data-stu-id="02c4f-109">Defining the custom header</span></span>  
 <span data-ttu-id="02c4f-110">Özel üstbilgi tanımlanmış bir ileti sözleşmesi tanımlayarak ve ile başlığı olarak gönderilmesini istediğiniz üyeleri işaretleme bir <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="02c4f-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="02c4f-111">Standartlaştırma hata olarak çözmek için XML serileştiriciyi ad alanı için bir varsayılan ad alanı bildiriminin yerine bir önek ile özel üstbilgi bildirir emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="02c4f-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="02c4f-112">Aşağıdaki kodu, doğru ad alanı bildirimi sahip bir ileti üstbilgisi olarak kullanılan veri türünü tanımlayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="02c4f-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="02c4f-113">Bu kod adlı yeni bir tür bildirir `msgHeaderElement` , serileştirilen ile XML serileştirici.</span><span class="sxs-lookup"><span data-stu-id="02c4f-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="02c4f-114">Bu tür bir örneğini serileştirilmiş, böylece Standartlaştırma hata çalışma bir 'h' öneki içeren bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02c4f-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="02c4f-115">İleti sözleşmesi örneği tanımlarsınız `msgHeaderElement` ve ile işaretleyin <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="02c4f-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02c4f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02c4f-116">See Also</span></span>  
 [<span data-ttu-id="02c4f-117">Varsayılan ileti sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="02c4f-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [<span data-ttu-id="02c4f-118">İleti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="02c4f-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [<span data-ttu-id="02c4f-119">İleti sözleşmeleri kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="02c4f-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
