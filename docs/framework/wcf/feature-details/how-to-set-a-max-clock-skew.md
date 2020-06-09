---
title: 'Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: f8231acade6821c95a76a608633fe443f4add8ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586923"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="b059e-102">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b059e-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="b059e-103">İki bilgisayardaki saat ayarları farklıysa, zaman açısından kritik işlevler derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b059e-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="b059e-104">Bu olasılığa karşı azaltmak için `MaxClockSkew` özelliği bir olarak ayarlayabilirsiniz <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="b059e-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="b059e-105">Bu özellik iki sınıfta kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b059e-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="b059e-106">Güvenli bir konuşma için, `MaxClockSkew` hizmet veya istemci önyüklendi olduğunda özellikte değişiklikler yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b059e-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="b059e-107">Bunu yapmak için, özelliği tarafından döndürülen özelliğini ayarlamanız gerekir <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b059e-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b059e-108">Sistem tarafından belirtilen bağlamalardan birindeki özelliği değiştirmek için, bağlama koleksiyonunda güvenlik bağlama öğesini bulmanız ve `MaxClockSkew` özelliği yeni bir değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b059e-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="b059e-109">İki sınıf öğesinden türetilir <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="b059e-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="b059e-110">Koleksiyondan güvenlik bağlamasını alırken, özelliği doğru bir şekilde ayarlamak için bu türlerden birine atamalısınız `MaxClockSkew` .</span><span class="sxs-lookup"><span data-stu-id="b059e-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="b059e-111">Aşağıdaki örnek öğesini kullanan bir kullanır <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="b059e-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="b059e-112">Sistem tarafından belirtilen her bağlamada kullanılacak güvenlik bağlamasının türünü belirten bir liste için, bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="b059e-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="b059e-113">Kodda yeni saat eğriltme değeri ile özel bir bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b059e-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b059e-114">Kodunuzda aşağıdaki ad alanlarına başvurular ekleyin: <xref:System.ServiceModel.Channels> , <xref:System.ServiceModel.Description> , <xref:System.Security.Permissions> , ve <xref:System.ServiceModel.Security.Tokens> .</span><span class="sxs-lookup"><span data-stu-id="b059e-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="b059e-115">Bir sınıfın örneğini oluşturun <xref:System.ServiceModel.WSHttpBinding> ve güvenlik modunu olarak ayarlayın <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b059e-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="b059e-116">Yöntemini çağırarak sınıfının yeni bir örneğini oluşturun <xref:System.ServiceModel.Channels.BindingElementCollection> <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> .</span><span class="sxs-lookup"><span data-stu-id="b059e-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="b059e-117"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> <xref:System.ServiceModel.Channels.BindingElementCollection> Güvenlik bağlama öğesini bulmak için sınıfının yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b059e-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="b059e-118"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>Yöntemini kullanırken gerçek türe atayın.</span><span class="sxs-lookup"><span data-stu-id="b059e-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="b059e-119">Aşağıdaki örnek <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="b059e-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="b059e-120"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A>Güvenlik bağlama öğesinde özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b059e-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="b059e-121">Uygun bir <xref:System.ServiceModel.ServiceHost> hizmet türü ve temel adres ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b059e-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="b059e-122"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>Bir uç nokta eklemek ve dahil etmek için yöntemini kullanın <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="b059e-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="b059e-123">Yapılandırmada MaxClockSkew ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b059e-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="b059e-124">[\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)Öğe bölümünde bir oluşturun [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="b059e-124">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="b059e-125">Bir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b059e-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="b059e-126">Aşağıdaki örnek olarak ayarlanır `MaxClockSkewBinding` .</span><span class="sxs-lookup"><span data-stu-id="b059e-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="b059e-127">Bir Encoding öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b059e-127">Add an encoding element.</span></span> <span data-ttu-id="b059e-128">Aşağıdaki örnek bir ekler [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="b059e-128">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="b059e-129">Bir [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) öğe ekleyin ve `authenticationMode` özniteliği uygun bir ayara ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b059e-129">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="b059e-130">Aşağıdaki örnek, `Kerberos` hizmetinin Windows kimlik doğrulamasını kullanmasını belirtmek için özniteliğini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b059e-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="b059e-131">' A ekleyin [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` özniteliği biçimindeki bir değere ayarlayın `"##:##:##"` .</span><span class="sxs-lookup"><span data-stu-id="b059e-131">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="b059e-132">Aşağıdaki örnek, 7 dakika olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b059e-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="b059e-133">İsteğe bağlı olarak, bir ekleyin [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` özniteliği uygun bir ayara ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b059e-133">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="b059e-134">Bir Transport öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b059e-134">Add a transport element.</span></span> <span data-ttu-id="b059e-135">Aşağıdaki örnek bir kullanır [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="b059e-135">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="b059e-136">Güvenli bir konuşma için, güvenlik ayarları öğesindeki önplanda gerçekleşmelidir [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="b059e-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b059e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b059e-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b059e-138">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b059e-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
