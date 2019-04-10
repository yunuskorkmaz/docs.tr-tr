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
ms.openlocfilehash: 1a8d99e5d2bd21a74318718f43b5d1c091ed073e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322153"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="a6416-102">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a6416-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="a6416-103">İki bilgisayar saat ayarları farklı ise, zaman açısından kritik işlevler derailed.</span><span class="sxs-lookup"><span data-stu-id="a6416-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="a6416-104">Bu olasılığını azaltmak için ayarlayabileceğiniz `MaxClockSkew` özelliğini bir <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="a6416-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="a6416-105">Bu özellik, iki sınıf üzerinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a6416-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6416-106">Önemli için bir güvenli konuşma değişiklikleri `MaxClockSkew` özelliği, hizmet veya istemcinin önyüklenemez olduğunda sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6416-106">Important   For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="a6416-107">Bunu yapmak için özelliğin üzerinde ayarlamalısınız <xref:System.ServiceModel.Channels.SecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6416-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span></span>  
  
 <span data-ttu-id="a6416-108">Sistem tarafından sağlanan bağlamalar birinde özelliğini değiştirmek için bağlamaları koleksiyonda güvenliği bağlama öğesini bulun ve ayarlamak `MaxClockSkew` özelliğini yeni bir değer.</span><span class="sxs-lookup"><span data-stu-id="a6416-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="a6416-109">İki sınıf türetilir <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a6416-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="a6416-110">Güvenlik bağlama koleksiyondan alınırken şu türlerden birine doğru şekilde ayarlanması için dönüştürmelisiniz `MaxClockSkew` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a6416-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="a6416-111">Aşağıdaki örnekte bir <xref:System.ServiceModel.WSHttpBinding>, kullanan <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a6416-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="a6416-112">Hangi güvenlik her sistem tarafından sağlanan bir bağlamayı içinde kullanılacak bağlama türünü belirten bir listesi için bkz [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a6416-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="a6416-113">Yeni bir saat ile özel bir bağlama oluşturmak için kod değerinde eğme</span><span class="sxs-lookup"><span data-stu-id="a6416-113">To create a custom binding with a new clock skew value in code</span></span>  
  
1. > [!WARNING]
    >  <span data-ttu-id="a6416-114">Kodunuzda aşağıdaki ad alanlarına Başvuru Ekle unutmayın: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, ve <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="a6416-114">Note   Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
     <span data-ttu-id="a6416-115">Bir örneğini oluşturmak bir <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="a6416-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
2. <span data-ttu-id="a6416-116">Yeni bir örneğini oluşturma <xref:System.ServiceModel.Channels.BindingElementCollection> çağırarak sınıfı <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6416-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="a6416-117">Kullanım <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemi <xref:System.ServiceModel.Channels.BindingElementCollection> güvenliği bağlama öğesini bulmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a6416-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="a6416-118">Kullanırken <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> gerçek türüne yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6416-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="a6416-119">Yayınları için aşağıdaki örnekte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türü.</span><span class="sxs-lookup"><span data-stu-id="a6416-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="a6416-120">Ayarlama <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> güvenlik bağlama öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="a6416-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="a6416-121">Oluşturma bir <xref:System.ServiceModel.ServiceHost> uygun hizmet türü ve temel adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="a6416-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="a6416-122">Kullanım <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> bir uç nokta ekleyin ve eklemek için yöntem <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="a6416-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="a6416-123">MaxClockSkew yapılandırmada ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a6416-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="a6416-124">Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) içinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümü.</span><span class="sxs-lookup"><span data-stu-id="a6416-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="a6416-125">Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="a6416-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="a6416-126">Aşağıdaki örnek ayarlar `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="a6416-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="a6416-127">Bir kodlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6416-127">Add an encoding element.</span></span> <span data-ttu-id="a6416-128">Aşağıdaki örnekte ekler bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="a6416-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="a6416-129">Ekleme bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi ve kümesi `authenticationMode` özniteliği için uygun bir ayar.</span><span class="sxs-lookup"><span data-stu-id="a6416-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="a6416-130">Aşağıdaki örnek özniteliği olarak ayarlanmış `Kerberos` hizmet Windows kimlik doğrulaması kullandığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a6416-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="a6416-131">Ekleme bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ayarlayıp `maxClockSkew` biçiminde bir değer özniteliği `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="a6416-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="a6416-132">Aşağıdaki örnek, 7 dakika olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6416-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="a6416-133">İsteğe bağlı olarak, ekleme bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ayarlayıp `maxClockSkew` özniteliği için uygun bir ayar.</span><span class="sxs-lookup"><span data-stu-id="a6416-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="a6416-134">Bir transport öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6416-134">Add a transport element.</span></span> <span data-ttu-id="a6416-135">Aşağıdaki örnekte bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="a6416-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="a6416-136">Güvenli bir konuşma için güvenlik ayarlarını önyükleme içinde gerçekleşmelidir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a6416-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6416-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6416-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a6416-138">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6416-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
