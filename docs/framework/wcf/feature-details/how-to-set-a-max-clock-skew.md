---
title: "Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e186043a6cb32eaf5ed6bac6be3eaf50cb1ea32b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="39aee-102">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="39aee-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="39aee-103">İki bilgisayardaki saat ayarları farklıysa zaman açısından kritik işlevler derailed.</span><span class="sxs-lookup"><span data-stu-id="39aee-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="39aee-104">Bu olasılığını azaltmak için ayarlayabileceğiniz `MaxClockSkew` özelliğine bir <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="39aee-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="39aee-105">Bu özellik üzerinde iki sınıf bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="39aee-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39aee-106">Önemli için güvenli bir konuşma değişiklikler `MaxClockSkew` özelliği, hizmet veya istemci önyükleme içinde olduğunda sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39aee-106">Important   For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="39aee-107">Bunu yapmak için özellik üzerinde ayarlamalısınız <xref:System.ServiceModel.Channels.SecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="39aee-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span></span>  
  
 <span data-ttu-id="39aee-108">Sistem tarafından sağlanan bağlamalar birinde özelliğini değiştirmek için güvenlik bağlama öğesi bağlamaları koleksiyonunda bulmak ve ayarlayın `MaxClockSkew` özelliği için yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="39aee-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="39aee-109">İki sınıf türetin <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="39aee-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="39aee-110">Güvenlik bağlama koleksiyondan alırken, bu türden biri için doğru şekilde ayarlanması için atamalısınız `MaxClockSkew` özelliği.</span><span class="sxs-lookup"><span data-stu-id="39aee-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="39aee-111">Aşağıdaki örnek kullanan bir <xref:System.ServiceModel.WSHttpBinding>, kullanan <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="39aee-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="39aee-112">Her sistem tarafından sağlanan bağlaması kullanmak için güvenlik bağlama hangi türünü belirten bir listesi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="39aee-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="39aee-113">Yeni bir saat ile özel bağlama oluşturmak için kod değerinde eğme</span><span class="sxs-lookup"><span data-stu-id="39aee-113">To create a custom binding with a new clock skew value in code</span></span>  
  
1.  > [!WARNING]
    >  <span data-ttu-id="39aee-114">Şu ad alanlarından kodunuzda Ekle başvurular dikkat edin: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, ve <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="39aee-114">Note   Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
     <span data-ttu-id="39aee-115">Bir örneğini oluşturmak bir <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="39aee-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
2.  <span data-ttu-id="39aee-116">Yeni bir örneğini oluşturmak <xref:System.ServiceModel.Channels.BindingElementCollection> çağırarak sınıfı <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39aee-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="39aee-117">Kullanım <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemi <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı güvenlik bağlama öğesi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="39aee-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4.  <span data-ttu-id="39aee-118">Kullanırken <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> gerçek türe yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39aee-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="39aee-119">Yayınları için aşağıdaki örnekte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türü.</span><span class="sxs-lookup"><span data-stu-id="39aee-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5.  <span data-ttu-id="39aee-120">Ayarlama <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> güvenlik bağlama öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="39aee-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6.  <span data-ttu-id="39aee-121">Oluşturma bir <xref:System.ServiceModel.ServiceHost> uygun hizmet türü ve temel adresi.</span><span class="sxs-lookup"><span data-stu-id="39aee-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7.  <span data-ttu-id="39aee-122">Kullanım <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> bir uç nokta ekleyin ve dahil etmek için yöntemi <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="39aee-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="39aee-123">MaxClockSkew yapılandırmasında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39aee-123">To set the MaxClockSkew in configuration</span></span>  
  
1.  <span data-ttu-id="39aee-124">Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) içinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümü.</span><span class="sxs-lookup"><span data-stu-id="39aee-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2.  <span data-ttu-id="39aee-125">Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="39aee-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="39aee-126">Aşağıdaki örnek, ayarlar `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="39aee-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3.  <span data-ttu-id="39aee-127">Bir kodlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39aee-127">Add an encoding element.</span></span> <span data-ttu-id="39aee-128">Aşağıdaki örnek, bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="39aee-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4.  <span data-ttu-id="39aee-129">Ekleme bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi ve kümesi `authenticationMode` öznitelik için uygun bir ayar.</span><span class="sxs-lookup"><span data-stu-id="39aee-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="39aee-130">Aşağıdaki örnek özniteliği olarak ayarlanmış `Kerberos` belirtmek için hizmet Windows kimlik doğrulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="39aee-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5.  <span data-ttu-id="39aee-131">Ekleme bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` biçiminde bir değer özniteliğini `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="39aee-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="39aee-132">Aşağıdaki örnek 7 dakika olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39aee-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="39aee-133">İsteğe bağlı olarak ekleyin bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` öznitelik için uygun bir ayar.</span><span class="sxs-lookup"><span data-stu-id="39aee-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6.  <span data-ttu-id="39aee-134">Bir taşıma öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39aee-134">Add a transport element.</span></span> <span data-ttu-id="39aee-135">Aşağıdaki örnek kullanan bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="39aee-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7.  <span data-ttu-id="39aee-136">Güvenli bir konuşma için güvenlik ayarlarını önyükleme sırasında gerçekleşmelidir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="39aee-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39aee-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39aee-137">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="39aee-138">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="39aee-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
