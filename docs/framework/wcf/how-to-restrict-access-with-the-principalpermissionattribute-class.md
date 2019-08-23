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
ms.openlocfilehash: 3b109e3e6817c300af1e79258d555562dcba067a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951018"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama
Bir Windows etki alanı bilgisayarındaki kaynaklara erişimi denetlemek, temel bir güvenlik görevidir. Örneğin, yalnızca belirli kullanıcılar, bordro bilgileri gibi hassas verileri görüntüleyebilmelidir. Bu konu, kullanıcının önceden tanımlanmış bir gruba ait olmasını sağlayarak bir yönteme erişimin nasıl kısıtlanacağını açıklar. Çalışan bir örnek için bkz. [hizmet Işlemlerine erişimi yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Görev iki ayrı yordamdan oluşur. İlki grubu oluşturur ve kullanıcılarla doldurur. İkincisi, grubu belirtmek <xref:System.Security.Permissions.PrincipalPermissionAttribute> için sınıfını uygular.  
  
### <a name="to-create-a-windows-group"></a>Bir Windows grubu oluşturmak için  
  
1. **Bilgisayar Yönetimi** konsolunu açın.  
  
2. Sol bölmede, **yerel kullanıcılar ve gruplar**' a tıklayın.  
  
3. **Gruplar**' a sağ tıklayın ve **Yeni Grup**' a tıklayın.  
  
4. **Grup adı** kutusuna yeni grup için bir ad yazın.  
  
5. **Açıklama** kutusuna yeni grubun açıklamasını yazın.  
  
6. Gruba yeni üyeler eklemek için **Ekle** düğmesine tıklayın.  
  
7. Kendinizi gruba eklediyseniz ve aşağıdaki kodu test etmek istiyorsanız, bilgisayarın oturumunu kapatmanız ve gruba dahil etmek için yeniden oturum açmanız gerekir.  
  
### <a name="to-demand-user-membership"></a>İsteğe bağlı kullanıcı üyeliği  
  
1. Uygulanan hizmet sözleşmesi kodunu içeren Windows Communication Foundation (WCF) kod dosyasını açın. Sözleşme uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2. Özniteliği, <xref:System.Security.Permissions.PrincipalPermissionAttribute> belirli bir grupla kısıtlanması gereken her bir yönteme uygulayın. <xref:System.Security.Permissions.SecurityAttribute.Action%2A> Özelliğini<xref:System.Security.Permissions.SecurityAction.Demand>veözelliğinigrubunadınaayarlayın. <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> Örneğin:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <xref:System.Security.Permissions.PrincipalPermissionAttribute> Özniteliği bir sözleşmeye uygularsanız, bir <xref:System.Security.SecurityException> oluşturulur. Özniteliği yalnızca Yöntem düzeyinde uygulayabilirsiniz.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Bir yönteme erişimi denetlemek için sertifika kullanma  
 Ayrıca, `PrincipalPermissionAttribute` istemci kimlik bilgisi türü bir sertifika ise, bir yönteme erişimi denetlemek için sınıfını da kullanabilirsiniz. Bunu yapmak için sertifikanın konusu ve parmak izinin olması gerekir.  
  
 Bir sertifikayı özelliklerine göre incelemek için bkz [. nasıl yapılır: MMC ek bileşeni](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)ile sertifikaları görüntüleyin. Parmak izi değerini bulmak için bkz [. nasıl yapılır: Bir sertifikanın](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)parmak izini alın.  
  
#### <a name="to-control-access-using-a-certificate"></a>Bir sertifika kullanarak erişimi denetlemek için  
  
1. Erişimi kısıtlamak istediğiniz yönteme sınıfıuygulayın.<xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. Özniteliği için eylemini olarak <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>ayarlayın.  
  
3. `Name` Özelliği, konu adı ve sertifikanın parmak iziyle oluşan bir dizeye ayarlayın. Aşağıdaki örnekte gösterildiği gibi iki değeri noktalı virgül ve boşluk ile ayırın:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. Aşağıdaki yapılandırma örneğinde gösterildiği <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> gibi özelliğiniolarakayarlayın:<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Bu değeri olarak `UseAspNetRoles` ayarlamak, `PrincipalPermissionAttribute` öğesinin `Name` özelliğinin bir dize karşılaştırması gerçekleştirmek için kullanılacağını gösterir. Bir sertifika istemci kimlik bilgileri olarak kullanıldığında, varsayılan olarak WCF, istemci birincil kimliği için benzersiz bir değer oluşturmak üzere sertifika ortak adını ve parmak izini noktalı virgülle birleştirir. Hizmet `UseAspNetRoles` `Name` olarak ayarlandığı ile, bu birincil kimlik değeri, kullanıcının erişim haklarını belirlemede özellik değeriyle karşılaştırılır. `PrincipalPermissionMode`  
  
     Alternatif olarak, şirket içinde barındırılan bir hizmet oluştururken aşağıdaki kodda gösterildiği <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> gibi koddaki özelliği ayarlayın:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
