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
ms.openlocfilehash: df057d64feb89d1e43b938b36cb48f2f103b17d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595394"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="37aa4-102">Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="37aa4-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="37aa4-103">Bazı hizmetler federe kimlik bilgileri gerektirebilir, ancak güvenli oturumları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="37aa4-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="37aa4-104">Bu durumda, güvenli oturum özelliğini devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37aa4-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="37aa4-105">' Den farklı olarak, <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı bir hizmetle iletişim kurarken güvenli oturumları devre dışı bırakmak için bir yol sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="37aa4-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="37aa4-106">Bunun yerine, güvenli oturum ayarlarını bir önyükleme ile değiştiren özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37aa4-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="37aa4-107">Bu konu başlığı altında, bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlama oluşturmak için içindeki bağlama öğelerinin nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="37aa4-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="37aa4-108">Sonuç, <xref:System.ServiceModel.WSFederationHttpBinding> Güvenli Oturumlar kullanmamasının dışında, ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="37aa4-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="37aa4-109">Güvenli oturum olmadan özel bir Federasyon bağlaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="37aa4-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="37aa4-110"><xref:System.ServiceModel.WSFederationHttpBinding>Kod içinde imperatively veya yapılandırma dosyasından bir tane yükleyerek sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37aa4-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="37aa4-111">' <xref:System.ServiceModel.WSFederationHttpBinding> A kopyalayın <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="37aa4-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="37aa4-112">İçinde öğesini bulun <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="37aa4-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="37aa4-113">İçinde öğesini bulun <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="37aa4-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="37aa4-114">Orijinali, <xref:System.ServiceModel.Channels.SecurityBindingElement> önyükleme güvenliği bağlama öğesiyle değiştirin <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> .</span><span class="sxs-lookup"><span data-stu-id="37aa4-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="37aa4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="37aa4-115">Example</span></span>

<span data-ttu-id="37aa4-116">Aşağıdaki örnek, güvenli oturum olmadan özel bir Federasyon bağlaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37aa4-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="37aa4-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="37aa4-117">Compiling the Code</span></span>

- <span data-ttu-id="37aa4-118">Kod örneğini derlemek için, System. ServiceModel. dll derlemesine başvuran bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37aa4-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="37aa4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37aa4-119">See also</span></span>

- [<span data-ttu-id="37aa4-120">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="37aa4-120">Bindings and Security</span></span>](bindings-and-security.md)
