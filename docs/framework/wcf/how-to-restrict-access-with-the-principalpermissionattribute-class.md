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
ms.openlocfilehash: 1cf09b945a21ca51f73c3948ffdf86da4225ac22
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751220"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="a9306-102">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="a9306-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="a9306-103">Bir Windows etki alanı bilgisayardaki kaynaklara erişimi denetleme temel güvenlik bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="a9306-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="a9306-104">Örneğin, yalnızca belirli kullanıcılara bordro bilgilerini gibi hassas verilerin görüntülemeniz mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9306-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="a9306-105">Bu konu, zorlu bir yöntemi kullanıcının, önceden tanımlanmış bir gruba ait erişimini kısıtlamak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="a9306-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="a9306-106">Çalışma örnek için bkz: [hizmet işlemlerine erişimi yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a9306-106">For a working sample, see [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="a9306-107">Görev, iki ayrı yordamlardan oluşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9306-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="a9306-108">İlk grubu oluşturur ve kullanıcıları ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="a9306-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="a9306-109">İkinci uygular <xref:System.Security.Permissions.PrincipalPermissionAttribute> grubu belirtmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a9306-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="a9306-110">Bir Windows grubu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a9306-110">To create a Windows group</span></span>  
  
1. <span data-ttu-id="a9306-111">Açık **Bilgisayar Yönetimi** Konsolu.</span><span class="sxs-lookup"><span data-stu-id="a9306-111">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="a9306-112">Sol bölmede bulunan tıklayın **yerel kullanıcılar ve gruplar**.</span><span class="sxs-lookup"><span data-stu-id="a9306-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="a9306-113">Sağ **grupları**, tıklatıp **yeni grup**.</span><span class="sxs-lookup"><span data-stu-id="a9306-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="a9306-114">İçinde **grup adı** yeni grup için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="a9306-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="a9306-115">İçinde **açıklama** yeni grubun açıklamasını yazın.</span><span class="sxs-lookup"><span data-stu-id="a9306-115">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="a9306-116">Tıklayın **Ekle** grubuna yeni üyeler eklemek için düğme.</span><span class="sxs-lookup"><span data-stu-id="a9306-116">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="a9306-117">Kendinizi gruba eklediğiniz ve aşağıdaki kodu test etmek istediğiniz, oturumu kapattığında gerekir ve tekrar açmaları gruba dahil.</span><span class="sxs-lookup"><span data-stu-id="a9306-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="a9306-118">İsteğe bağlı kullanıcı üyeliği</span><span class="sxs-lookup"><span data-stu-id="a9306-118">To demand user membership</span></span>  
  
1. <span data-ttu-id="a9306-119">Uygulanan hizmet sözleşme kodu içeren Windows Communication Foundation (WCF) kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a9306-119">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="a9306-120">Bir sözleşme uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a9306-120">For more information about implementing a contract, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="a9306-121">Uygulama <xref:System.Security.Permissions.PrincipalPermissionAttribute> öznitelik her yönteme belirli bir gruba sınırlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9306-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="a9306-122">Ayarlama <xref:System.Security.Permissions.SecurityAttribute.Action%2A> özelliğini <xref:System.Security.Permissions.SecurityAction.Demand> ve <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> özelliğini grubunun adı.</span><span class="sxs-lookup"><span data-stu-id="a9306-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="a9306-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a9306-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a9306-124">Uygularsanız, <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliği bir sözleşmeyi bir <xref:System.Security.SecurityException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a9306-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="a9306-125">Özniteliğin yöntem düzeyinde yalnızca uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9306-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="a9306-126">Bir yönteme erişimi denetlemek için bir sertifika kullanıyor</span><span class="sxs-lookup"><span data-stu-id="a9306-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="a9306-127">Ayrıca `PrincipalPermissionAttribute` bir sertifika istemci kimlik bilgisi türü ise bir yönteme erişimi denetlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a9306-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="a9306-128">Bunu yapmak için sertifikanın konu ve parmak izi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9306-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="a9306-129">Sertifika özelliklerini incelemek için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="a9306-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="a9306-130">Parmak izi değerini bulmak için bkz: [nasıl yapılır: Bir sertifikanın parmak izini alma](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a9306-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="a9306-131">Bir sertifika kullanarak erişimi denetleme</span><span class="sxs-lookup"><span data-stu-id="a9306-131">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="a9306-132">Uygulama <xref:System.Security.Permissions.PrincipalPermissionAttribute> erişimi kısıtlamak istediğiniz yönteme sınıf.</span><span class="sxs-lookup"><span data-stu-id="a9306-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="a9306-133">Özniteliğin eylem <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9306-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="a9306-134">Ayarlama `Name` konu adı ve sertifikanın parmak izi oluşan bir dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="a9306-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="a9306-135">İki değer, aşağıdaki örnekte gösterildiği gibi noktalı virgül ve boşluk ile ayırın:</span><span class="sxs-lookup"><span data-stu-id="a9306-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="a9306-136">Ayarlama <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> yapılandırmasını aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="a9306-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="a9306-137">Bu değeri ayarlamak `UseAspNetRoles` belirten `Name` özelliği `PrincipalPermissionAttribute` dize karşılaştırma yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9306-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="a9306-138">Bir sertifika bir istemci kimlik bilgileri olarak kullanıldığında, varsayılan olarak sertifika ortak adını ve parmak izini istemcinin birincil kimlik için benzersiz bir değer oluşturmak için noktalı virgül ile WCF birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a9306-138">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="a9306-139">İle `UseAspNetRoles` yap `PrincipalPermissionMode` hizmette bu birincil kimlik değeri ile karşılaştırılır `Name` kullanıcı erişim haklarını belirlemek için özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="a9306-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="a9306-140">Alternatif olarak, şirket içinde barındırılan hizmet oluşturulurken ayarlamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> aşağıdaki kodda gösterildiği gibi kodda özelliği:</span><span class="sxs-lookup"><span data-stu-id="a9306-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a9306-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9306-141">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="a9306-142">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="a9306-142">Authorizing Access to Service Operations</span></span>](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="a9306-143">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9306-143">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="a9306-144">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="a9306-144">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
