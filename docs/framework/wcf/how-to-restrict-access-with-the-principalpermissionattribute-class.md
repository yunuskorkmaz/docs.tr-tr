---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama'
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
ms.openlocfilehash: 533bd3358d5e337071c6419264d1dac03b8987ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779354"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="6d4df-103">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="6d4df-103">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>

<span data-ttu-id="6d4df-104">Bir Windows etki alanı bilgisayarındaki kaynaklara erişimi denetlemek, temel bir güvenlik görevidir.</span><span class="sxs-lookup"><span data-stu-id="6d4df-104">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="6d4df-105">Örneğin, yalnızca belirli kullanıcılar, bordro bilgileri gibi hassas verileri görüntüleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6d4df-105">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="6d4df-106">Bu konu, kullanıcının önceden tanımlanmış bir gruba ait olmasını sağlayarak bir yönteme erişimin nasıl kısıtlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6d4df-106">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="6d4df-107">Çalışan bir örnek için bkz. [hizmet Işlemlerine erişimi yetkilendirme](./samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6d4df-107">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="6d4df-108">Görev iki ayrı yordamdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="6d4df-108">The task consists of two separate procedures.</span></span> <span data-ttu-id="6d4df-109">İlki grubu oluşturur ve kullanıcılarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="6d4df-109">The first creates the group and populates it with users.</span></span> <span data-ttu-id="6d4df-110">İkincisi, <xref:System.Security.Permissions.PrincipalPermissionAttribute> grubu belirtmek için sınıfını uygular.</span><span class="sxs-lookup"><span data-stu-id="6d4df-110">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="6d4df-111">Bir Windows grubu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6d4df-111">To create a Windows group</span></span>  
  
1. <span data-ttu-id="6d4df-112">**Bilgisayar Yönetimi** konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-112">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="6d4df-113">Sol bölmede, **yerel kullanıcılar ve gruplar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-113">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="6d4df-114">**Gruplar**' a sağ tıklayın ve **Yeni Grup**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-114">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="6d4df-115">**Grup adı** kutusuna yeni grup için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-115">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="6d4df-116">**Açıklama** kutusuna yeni grubun açıklamasını yazın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-116">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="6d4df-117">Gruba yeni üyeler eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-117">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="6d4df-118">Kendinizi gruba eklediyseniz ve aşağıdaki kodu test etmek istiyorsanız, bilgisayarın oturumunu kapatmanız ve gruba dahil etmek için yeniden oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d4df-118">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="6d4df-119">İsteğe bağlı kullanıcı üyeliği</span><span class="sxs-lookup"><span data-stu-id="6d4df-119">To demand user membership</span></span>  
  
1. <span data-ttu-id="6d4df-120">Uygulanan hizmet sözleşmesi kodunu içeren Windows Communication Foundation (WCF) kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-120">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="6d4df-121">Sözleşme uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="6d4df-121">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="6d4df-122">Özniteliği, <xref:System.Security.Permissions.PrincipalPermissionAttribute> belirli bir grupla kısıtlanması gereken her bir yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-122">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="6d4df-123"><xref:System.Security.Permissions.SecurityAttribute.Action%2A>Özelliğini <xref:System.Security.Permissions.SecurityAction.Demand> ve <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> özelliğini grubun adına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-123">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="6d4df-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6d4df-124">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="6d4df-125"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Özniteliği bir sözleşmeye uygularsanız, bir <xref:System.Security.SecurityException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6d4df-125">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="6d4df-126">Özniteliği yalnızca Yöntem düzeyinde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d4df-126">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="6d4df-127">Bir yönteme erişimi denetlemek için sertifika kullanma</span><span class="sxs-lookup"><span data-stu-id="6d4df-127">Using a Certificate to Control Access to a Method</span></span>  

 <span data-ttu-id="6d4df-128">Ayrıca, `PrincipalPermissionAttribute` istemci kimlik bilgisi türü bir sertifika ise, bir yönteme erişimi denetlemek için sınıfını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d4df-128">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="6d4df-129">Bunu yapmak için sertifikanın konusu ve parmak izinin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d4df-129">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="6d4df-130">Bir sertifikayı özelliklerine göre incelemek için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="6d4df-130">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="6d4df-131">Parmak izi değerini bulmak için bkz. [nasıl yapılır: bir sertifikanın parmak Izini alma](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="6d4df-131">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="6d4df-132">Bir sertifika kullanarak erişimi denetlemek için</span><span class="sxs-lookup"><span data-stu-id="6d4df-132">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="6d4df-133"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Erişimi kısıtlamak istediğiniz yönteme sınıfı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-133">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="6d4df-134">Özniteliği için eylemini olarak ayarlayın <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6d4df-134">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="6d4df-135">Özelliği, `Name` Konu adı ve sertifikanın parmak iziyle oluşan bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d4df-135">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="6d4df-136">Aşağıdaki örnekte gösterildiği gibi iki değeri noktalı virgül ve boşluk ile ayırın:</span><span class="sxs-lookup"><span data-stu-id="6d4df-136">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="6d4df-137"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> Aşağıdaki yapılandırma örneğinde gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6d4df-137">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="6d4df-138">Bu değeri olarak ayarlamak `UseAspNetRoles` `Name` , öğesinin özelliğinin `PrincipalPermissionAttribute` bir dize karşılaştırması gerçekleştirmek için kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d4df-138">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="6d4df-139">Bir sertifika istemci kimlik bilgileri olarak kullanıldığında, varsayılan olarak WCF, istemci birincil kimliği için benzersiz bir değer oluşturmak üzere sertifika ortak adını ve parmak izini noktalı virgülle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="6d4df-139">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="6d4df-140">`UseAspNetRoles`Hizmet olarak ayarlandığı ile `PrincipalPermissionMode` , bu birincil kimlik değeri, `Name` kullanıcının erişim haklarını belirlemede özellik değeriyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="6d4df-140">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="6d4df-141">Alternatif olarak, şirket içinde barındırılan bir hizmet oluştururken <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> aşağıdaki kodda gösterildiği gibi koddaki özelliği ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6d4df-141">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6d4df-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d4df-142">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="6d4df-143">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="6d4df-143">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="6d4df-144">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="6d4df-144">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="6d4df-145">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="6d4df-145">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
