---
title: 'Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 93268be4b04ec6824ed7ecab070f28ddf40f8831
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320933"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="0d9dd-102">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="0d9dd-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="0d9dd-103">Bir Windows etki alanı bilgisayarındaki kaynaklara erişimi denetlemek, temel bir güvenlik görevidir.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="0d9dd-104">Örneğin, yalnızca belirli kullanıcılar, bordro bilgileri gibi hassas verileri görüntüleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="0d9dd-105">Bu konu, kullanıcının önceden tanımlanmış bir gruba ait olmasını sağlayarak bir yönteme erişimin nasıl kısıtlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="0d9dd-106">Çalışan bir örnek için bkz. [hizmet Işlemlerine erişimi yetkilendirme](./samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0d9dd-106">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="0d9dd-107">Görev iki ayrı yordamdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="0d9dd-108">İlki grubu oluşturur ve kullanıcılarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="0d9dd-109">İkincisi, grubu belirtmek için <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfını uygular.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="0d9dd-110">Bir Windows grubu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0d9dd-110">To create a Windows group</span></span>  
  
1. <span data-ttu-id="0d9dd-111">**Bilgisayar Yönetimi** konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-111">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="0d9dd-112">Sol bölmede, **yerel kullanıcılar ve gruplar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="0d9dd-113">**Gruplar**' a sağ tıklayın ve **Yeni Grup**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="0d9dd-114">**Grup adı** kutusuna yeni grup için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="0d9dd-115">**Açıklama** kutusuna yeni grubun açıklamasını yazın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-115">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="0d9dd-116">Gruba yeni üyeler eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-116">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="0d9dd-117">Kendinizi gruba eklediyseniz ve aşağıdaki kodu test etmek istiyorsanız, bilgisayarın oturumunu kapatmanız ve gruba dahil etmek için yeniden oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="0d9dd-118">İsteğe bağlı kullanıcı üyeliği</span><span class="sxs-lookup"><span data-stu-id="0d9dd-118">To demand user membership</span></span>  
  
1. <span data-ttu-id="0d9dd-119">Uygulanan hizmet sözleşmesi kodunu içeren Windows Communication Foundation (WCF) kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-119">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="0d9dd-120">Sözleşme uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="0d9dd-120">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="0d9dd-121">Belirli bir grup ile kısıtlanması gereken her bir yönteme <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="0d9dd-122">@No__t-0 özelliğini <xref:System.Security.Permissions.SecurityAction.Demand> ve <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> özelliği grubunun adına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="0d9dd-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0d9dd-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="0d9dd-124">@No__t-0 özniteliğini bir sözleşmeye uygularsanız, bir <xref:System.Security.SecurityException> atılır.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="0d9dd-125">Özniteliği yalnızca Yöntem düzeyinde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="0d9dd-126">Bir yönteme erişimi denetlemek için sertifika kullanma</span><span class="sxs-lookup"><span data-stu-id="0d9dd-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="0d9dd-127">İstemci kimlik bilgisi türü bir sertifika ise, bir yönteme erişimi denetlemek için `PrincipalPermissionAttribute` sınıfını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="0d9dd-128">Bunu yapmak için sertifikanın konusu ve parmak izinin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="0d9dd-129">Bir sertifikayı özelliklerine göre incelemek için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="0d9dd-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="0d9dd-130">Parmak izi değerini bulmak için bkz. [nasıl yapılır: bir sertifikanın parmak Izini alma](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="0d9dd-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="0d9dd-131">Bir sertifika kullanarak erişimi denetlemek için</span><span class="sxs-lookup"><span data-stu-id="0d9dd-131">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="0d9dd-132">@No__t-0 sınıfını erişimi kısıtlamak istediğiniz yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="0d9dd-133">Özniteliğin eylemini <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="0d9dd-134">@No__t-0 özelliğini, konu adı ve sertifikanın parmak iziyle oluşan bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="0d9dd-135">Aşağıdaki örnekte gösterildiği gibi iki değeri noktalı virgül ve boşluk ile ayırın:</span><span class="sxs-lookup"><span data-stu-id="0d9dd-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="0d9dd-136">@No__t-0 özelliğini aşağıdaki yapılandırma örneğinde gösterildiği gibi <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0d9dd-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="0d9dd-137">Bu değerin `UseAspNetRoles` olarak ayarlanması, bir dize karşılaştırması gerçekleştirmek için `PrincipalPermissionAttribute` ' nin `Name` özelliğinin kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="0d9dd-138">Bir sertifika istemci kimlik bilgileri olarak kullanıldığında, varsayılan olarak WCF, istemci birincil kimliği için benzersiz bir değer oluşturmak üzere sertifika ortak adını ve parmak izini noktalı virgülle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-138">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="0d9dd-139">@No__t-0, hizmette `PrincipalPermissionMode` olarak ayarlandığında, bu birincil kimlik değeri, kullanıcının erişim haklarını belirlemede `Name` Özellik değeri ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="0d9dd-140">Alternatif olarak, şirket içinde barındırılan bir hizmet oluştururken, koddaki <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini aşağıdaki kodda gösterildiği gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0d9dd-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0d9dd-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d9dd-141">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="0d9dd-142">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="0d9dd-142">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="0d9dd-143">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d9dd-143">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="0d9dd-144">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="0d9dd-144">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
