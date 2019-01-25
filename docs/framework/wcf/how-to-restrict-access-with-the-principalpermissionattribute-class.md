---
title: 'Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 4704a310e49246bdc8fff54abe6841f2e8482ed5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590580"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama
Bir Windows etki alanı bilgisayardaki kaynaklara erişimi denetleme temel güvenlik bir görevdir. Örneğin, yalnızca belirli kullanıcılara bordro bilgilerini gibi hassas verilerin görüntülemeniz mümkün olması gerekir. Bu konu, zorlu bir yöntemi kullanıcının, önceden tanımlanmış bir gruba ait erişimini kısıtlamak nasıl açıklar. Çalışma örnek için bkz: [hizmet işlemlerine erişimi yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Görev, iki ayrı yordamlardan oluşmaktadır. İlk grubu oluşturur ve kullanıcıları ile doldurur. İkinci uygular <xref:System.Security.Permissions.PrincipalPermissionAttribute> grubu belirtmek için sınıf.  
  
### <a name="to-create-a-windows-group"></a>Bir Windows grubu oluşturmak için  
  
1.  Açık **Bilgisayar Yönetimi** Konsolu.  
  
2.  Sol bölmede bulunan tıklayın **yerel kullanıcılar ve gruplar**.  
  
3.  Sağ **grupları**, tıklatıp **yeni grup**.  
  
4.  İçinde **grup adı** yeni grup için bir ad yazın.  
  
5.  İçinde **açıklama** yeni grubun açıklamasını yazın.  
  
6.  Tıklayın **Ekle** grubuna yeni üyeler eklemek için düğme.  
  
7.  Kendinizi gruba eklediğiniz ve aşağıdaki kodu test etmek istediğiniz, oturumu kapattığında gerekir ve tekrar açmaları gruba dahil.  
  
### <a name="to-demand-user-membership"></a>İsteğe bağlı kullanıcı üyeliği  
  
1.  Uygulanan hizmet sözleşme kodu içeren Windows Communication Foundation (WCF) kod dosyasını açın. Bir sözleşme uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Uygulama <xref:System.Security.Permissions.PrincipalPermissionAttribute> öznitelik her yönteme belirli bir gruba sınırlı olmalıdır. Ayarlama <xref:System.Security.Permissions.SecurityAttribute.Action%2A> özelliğini <xref:System.Security.Permissions.SecurityAction.Demand> ve <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> özelliğini grubunun adı. Örneğin:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Uygularsanız, <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliği bir sözleşmeyi bir <xref:System.Security.SecurityException> oluşturulur. Özniteliğin yöntem düzeyinde yalnızca uygulayabilirsiniz.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Bir yönteme erişimi denetlemek için bir sertifika kullanıyor  
 Ayrıca `PrincipalPermissionAttribute` bir sertifika istemci kimlik bilgisi türü ise bir yönteme erişimi denetlemek için sınıf. Bunu yapmak için sertifikanın konu ve parmak izi olmalıdır.  
  
 Sertifika özelliklerini incelemek için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Parmak izi değerini bulmak için bkz: [nasıl yapılır: Bir sertifikanın parmak izini alma](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Bir sertifika kullanarak erişimi denetleme  
  
1.  Uygulama <xref:System.Security.Permissions.PrincipalPermissionAttribute> erişimi kısıtlamak istediğiniz yönteme sınıf.  
  
2.  Özniteliğin eylem <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3.  Ayarlama `Name` konu adı ve sertifikanın parmak izi oluşan bir dize özelliği. İki değer, aşağıdaki örnekte gösterildiği gibi noktalı virgül ve boşluk ile ayırın:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Ayarlama <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> yapılandırmasını aşağıda gösterildiği gibi:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Bu değeri ayarlamak `UseAspNetRoles` belirten `Name` özelliği `PrincipalPermissionAttribute` dize karşılaştırma yapmak için kullanılır. Bir sertifika bir istemci kimlik bilgileri olarak kullanıldığında, varsayılan olarak sertifika ortak adını ve parmak izini istemcinin birincil kimlik için benzersiz bir değer oluşturmak için noktalı virgül ile WCF birleştirir. İle `UseAspNetRoles` yap `PrincipalPermissionMode` hizmette bu birincil kimlik değeri ile karşılaştırılır `Name` kullanıcı erişim haklarını belirlemek için özellik değeri.  
  
     Alternatif olarak, şirket içinde barındırılan hizmet oluşturulurken ayarlamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> aşağıdaki kodda gösterildiği gibi kodda özelliği:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
