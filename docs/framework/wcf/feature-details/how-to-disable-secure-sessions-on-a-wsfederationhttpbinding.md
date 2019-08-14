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
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972044"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="faa61-102">Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="faa61-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="faa61-103">Bazı hizmetler federe kimlik bilgileri gerektirebilir, ancak güvenli oturumları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="faa61-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="faa61-104">Bu durumda, güvenli oturum özelliğini devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="faa61-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="faa61-105">'Denfarklıolarak,sınıfıbirhizmetleiletişimkurarkengüvenlioturumlarıdevredışıbırakmakiçinbiryolsağlamaz.<xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="faa61-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="faa61-106">Bunun yerine, güvenli oturum ayarlarını bir önyükleme ile değiştiren özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="faa61-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="faa61-107">Bu konu başlığı altında, bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlama oluşturmak için içindeki bağlama öğelerinin nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="faa61-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="faa61-108">Sonuç, güvenli oturumlar kullanmamasının <xref:System.ServiceModel.WSFederationHttpBinding> dışında, ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="faa61-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="faa61-109">Güvenli oturum olmadan özel bir Federasyon bağlaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="faa61-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="faa61-110">Kod içinde imperatively veya yapılandırma <xref:System.ServiceModel.WSFederationHttpBinding> dosyasından bir tane yükleyerek sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="faa61-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="faa61-111"><xref:System.ServiceModel.WSFederationHttpBinding> ' A<xref:System.ServiceModel.Channels.CustomBinding>kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="faa61-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="faa61-112"><xref:System.ServiceModel.Channels.SecurityBindingElement> İçinde<xref:System.ServiceModel.Channels.CustomBinding>öğesini bulun.</span><span class="sxs-lookup"><span data-stu-id="faa61-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="faa61-113"><xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> İçinde<xref:System.ServiceModel.Channels.SecurityBindingElement>öğesini bulun.</span><span class="sxs-lookup"><span data-stu-id="faa61-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="faa61-114">Orijinali <xref:System.ServiceModel.Channels.SecurityBindingElement> , önyükleme güvenliği bağlama öğesiyle <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>değiştirin.</span><span class="sxs-lookup"><span data-stu-id="faa61-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="faa61-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="faa61-115">Example</span></span>

<span data-ttu-id="faa61-116">Aşağıdaki örnek, güvenli oturum olmadan özel bir Federasyon bağlaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="faa61-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="faa61-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="faa61-117">Compiling the Code</span></span>

- <span data-ttu-id="faa61-118">Kod örneğini derlemek için, System. ServiceModel. dll derlemesine başvuran bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="faa61-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="faa61-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa61-119">See also</span></span>

- [<span data-ttu-id="faa61-120">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="faa61-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
