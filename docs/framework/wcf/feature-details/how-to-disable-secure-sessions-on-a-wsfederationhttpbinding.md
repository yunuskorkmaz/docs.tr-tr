---
title: 'Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: b61c8935b785a80f6e3163b3bafd83d3dd84f52f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202087"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="61bfb-102">Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="61bfb-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="61bfb-103">Bazı hizmetler, Federasyon kimlik bilgisi iste ancak güvenli oturumlar desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="61bfb-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="61bfb-104">Bu durumda, güvenli oturum özelliği devre dışı bırakmalısınız.</span><span class="sxs-lookup"><span data-stu-id="61bfb-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="61bfb-105">Farklı <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı güvenli oturumlarını devre dışı bırakmak için bir yol sağlamaz hizmeti ile iletişim kurarken.</span><span class="sxs-lookup"><span data-stu-id="61bfb-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="61bfb-106">Bunun yerine, özel bağlama güvenli oturum ayarları ile bir önyükleme yerini alan oluşturmalısınız.</span><span class="sxs-lookup"><span data-stu-id="61bfb-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="61bfb-107">Bu konuda bulunan bağlama öğeleri değiştirmek gösterilmiştir bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlamayı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="61bfb-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="61bfb-108">Sonuç aynıdır <xref:System.ServiceModel.WSFederationHttpBinding> dışında güvenli oturumlar kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="61bfb-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="61bfb-109">Özel bir oluşturmak için bağlama güvenli oturum olmadan Federasyon</span><span class="sxs-lookup"><span data-stu-id="61bfb-109">To create a custom federated binding without secure session</span></span>  
  
1.  <span data-ttu-id="61bfb-110">Bir örneğini oluşturmak <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı kod içinde kesin ya da bir yapılandırma dosyasından yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="61bfb-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2.  <span data-ttu-id="61bfb-111">Kopya <xref:System.ServiceModel.WSFederationHttpBinding> içine bir <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="61bfb-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3.  <span data-ttu-id="61bfb-112">Bulma <xref:System.ServiceModel.Channels.SecurityBindingElement> içinde <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="61bfb-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4.  <span data-ttu-id="61bfb-113">Bulma <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> içinde <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="61bfb-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5.  <span data-ttu-id="61bfb-114">Orijinalin yerine geçecek <xref:System.ServiceModel.Channels.SecurityBindingElement> önyükleme güvenliği bağlama öğeyi <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="61bfb-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61bfb-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="61bfb-115">Example</span></span>  
 <span data-ttu-id="61bfb-116">Aşağıdaki örnek bir özel federe bağlama güvenli oturum olmadan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61bfb-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61bfb-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="61bfb-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="61bfb-118">Kod örneği derlemek için System.ServiceModel.dll derlemesine başvuran bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61bfb-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61bfb-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61bfb-119">See Also</span></span>  
 [<span data-ttu-id="61bfb-120">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="61bfb-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
