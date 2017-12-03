---
title: "Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama"
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
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ddfb7b343bf4eb551b5029c538d29f104698adf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama
Bir Windows etki alanına bilgisayar üzerindeki kaynaklara erişimi denetleme temel güvenlik bir görevdir. Örneğin, yalnızca belirli kullanıcılar bordro bilgileri gibi hassas verileri görüntüleyebilir olmalıdır. Bu konuda, yoğun tarafından bir yöntemi kullanıcının önceden tanımlanmış bir gruba ait erişimini kısıtlamak açıklanmaktadır. Çalışma örnek için bkz: [hizmet işlemlerine erişimi yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Görev iki ayrı yordamları içerir. İlk grubu oluşturur ve kullanıcılar ile doldurur. İkinci geçerlidir <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfı grubu belirtin.  
  
### <a name="to-create-a-windows-group"></a>Bir Windows grubu oluşturmak için  
  
1.  Açık **Bilgisayar Yönetimi** konsol.  
  
2.  Sol panelinde tıklatın **yerel kullanıcılar ve gruplar**.  
  
3.  Sağ **grupları**, tıklatıp **yeni grup**.  
  
4.  İçinde **grup adı** kutusuna, yeni grup için bir ad yazın.  
  
5.  İçinde **açıklama** kutusuna, yeni Grup açıklamasını yazın.  
  
6.  Tıklatın **Ekle** gruba yeni üye eklemek için düğmesini.  
  
7.  Kendiniz gruba eklediğiniz ve aşağıdaki kodu test etmek istediğiniz, oturumu kapattığında gerekir ve günlük yedekleme için gruba dahil.  
  
### <a name="to-demand-user-membership"></a>İsteğe bağlı kullanıcı üyeliği  
  
1.  Açık [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulanan hizmet sözleşme kodu içeren kod dosyası. [!INCLUDE[crabout](../../../includes/crabout-md.md)]bir sözleşme uygulama bkz [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Uygulama <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliği her yöntemine, belirli bir gruba kısıtlanmalıdır. Ayarlama <xref:System.Security.Permissions.SecurityAttribute.Action%2A> özelliğine <xref:System.Security.Permissions.SecurityAction.Demand> ve <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> özelliğini grubunun adı. Örneğin:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Uygularsanız <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliği bir sözleşmeyi bir <xref:System.Security.SecurityException> oluşturulur. Özniteliğin yöntem düzeyinde yalnızca uygulayabilirsiniz.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Bir sertifikayla erişimi denetlemek üzere bir yöntemi  
 Aynı zamanda `PrincipalPermissionAttribute` istemci kimlik bilgisi türü bir sertifika varsa bir yöntem erişimi denetlemek için sınıf. Bunu yapmak için sertifikanın konu ve parmak izi olması gerekir.  
  
 Bir sertifika özelliklerini incelemek için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Parmak izi değerini bulmak için bkz: [nasıl yapılır: bir sertifikanın parmak izini alma](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Bir sertifika kullanarak erişimi denetlemek için  
  
1.  Uygulama <xref:System.Security.Permissions.PrincipalPermissionAttribute> erişimini kısıtlamak istediğiniz yönteme sınıf.  
  
2.  Özniteliğe eylem <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3.  Ayarlama `Name` konu adı ve sertifikanın parmak izi oluşan bir dize özelliği. İki değer noktalı virgül ve boşluk ile aşağıdaki örnekte gösterildiği gibi ayırır:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Ayarlama <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğine <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> aşağıdaki yapılandırma örnekte gösterildiği gibi:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Bu değeri ayarlamak `UseAspNetRoles` belirten `Name` özelliği `PrincipalPermissionAttribute` dize karşılaştırmasının gerçekleştirmek için kullanılır. Bir sertifika kullanıldığında bir istemci kimlik bilgileri olarak varsayılan olarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sertifika ortak adı ve parmak izi istemcinin birincil kimlik için benzersiz bir değer oluşturmak için noktalı virgül ile art arda ekler. İle `UseAspNetRoles` olarak ayarla `PrincipalPermissionMode` hizmette bu birincil kimlik değer ile karşılaştırılır `Name` kullanıcının erişim haklarını belirlemek için özellik değeri.  
  
     Alternatif olarak, kendi kendini barındıran hizmet oluşturulurken kümesinin <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> aşağıdaki kodda gösterildiği gibi kodu özelliğinde:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [Hizmet işlemlerine erişimi yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Güvenlik genel bakış](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
