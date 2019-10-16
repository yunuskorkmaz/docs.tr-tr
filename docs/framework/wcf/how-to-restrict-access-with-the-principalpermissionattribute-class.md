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
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama
Bir Windows etki alanı bilgisayarındaki kaynaklara erişimi denetlemek, temel bir güvenlik görevidir. Örneğin, yalnızca belirli kullanıcılar, bordro bilgileri gibi hassas verileri görüntüleyebilmelidir. Bu konu, kullanıcının önceden tanımlanmış bir gruba ait olmasını sağlayarak bir yönteme erişimin nasıl kısıtlanacağını açıklar. Çalışan bir örnek için bkz. [hizmet Işlemlerine erişimi yetkilendirme](./samples/authorizing-access-to-service-operations.md).  
  
 Görev iki ayrı yordamdan oluşur. İlki grubu oluşturur ve kullanıcılarla doldurur. İkincisi, grubu belirtmek için <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfını uygular.  
  
### <a name="to-create-a-windows-group"></a>Bir Windows grubu oluşturmak için  
  
1. **Bilgisayar Yönetimi** konsolunu açın.  
  
2. Sol bölmede, **yerel kullanıcılar ve gruplar**' a tıklayın.  
  
3. **Gruplar**' a sağ tıklayın ve **Yeni Grup**' a tıklayın.  
  
4. **Grup adı** kutusuna yeni grup için bir ad yazın.  
  
5. **Açıklama** kutusuna yeni grubun açıklamasını yazın.  
  
6. Gruba yeni üyeler eklemek için **Ekle** düğmesine tıklayın.  
  
7. Kendinizi gruba eklediyseniz ve aşağıdaki kodu test etmek istiyorsanız, bilgisayarın oturumunu kapatmanız ve gruba dahil etmek için yeniden oturum açmanız gerekir.  
  
### <a name="to-demand-user-membership"></a>İsteğe bağlı kullanıcı üyeliği  
  
1. Uygulanan hizmet sözleşmesi kodunu içeren Windows Communication Foundation (WCF) kod dosyasını açın. Sözleşme uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).  
  
2. Belirli bir grup ile kısıtlanması gereken her bir yönteme <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliğini uygulayın. @No__t-0 özelliğini <xref:System.Security.Permissions.SecurityAction.Demand> ve <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> özelliği grubunun adına ayarlayın. Örneğin:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > @No__t-0 özniteliğini bir sözleşmeye uygularsanız, bir <xref:System.Security.SecurityException> atılır. Özniteliği yalnızca Yöntem düzeyinde uygulayabilirsiniz.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Bir yönteme erişimi denetlemek için sertifika kullanma  
 İstemci kimlik bilgisi türü bir sertifika ise, bir yönteme erişimi denetlemek için `PrincipalPermissionAttribute` sınıfını da kullanabilirsiniz. Bunu yapmak için sertifikanın konusu ve parmak izinin olması gerekir.  
  
 Bir sertifikayı özelliklerine göre incelemek için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Parmak izi değerini bulmak için bkz. [nasıl yapılır: bir sertifikanın parmak Izini alma](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Bir sertifika kullanarak erişimi denetlemek için  
  
1. @No__t-0 sınıfını erişimi kısıtlamak istediğiniz yönteme uygulayın.  
  
2. Özniteliğin eylemini <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType> olarak ayarlayın.  
  
3. @No__t-0 özelliğini, konu adı ve sertifikanın parmak iziyle oluşan bir dizeye ayarlayın. Aşağıdaki örnekte gösterildiği gibi iki değeri noktalı virgül ve boşluk ile ayırın:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. @No__t-0 özelliğini aşağıdaki yapılandırma örneğinde gösterildiği gibi <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> olarak ayarlayın:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Bu değerin `UseAspNetRoles` olarak ayarlanması, bir dize karşılaştırması gerçekleştirmek için `PrincipalPermissionAttribute` ' nin `Name` özelliğinin kullanılacağını gösterir. Bir sertifika istemci kimlik bilgileri olarak kullanıldığında, varsayılan olarak WCF, istemci birincil kimliği için benzersiz bir değer oluşturmak üzere sertifika ortak adını ve parmak izini noktalı virgülle birleştirir. @No__t-0, hizmette `PrincipalPermissionMode` olarak ayarlandığında, bu birincil kimlik değeri, kullanıcının erişim haklarını belirlemede `Name` Özellik değeri ile karşılaştırılır.  
  
     Alternatif olarak, şirket içinde barındırılan bir hizmet oluştururken, koddaki <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> özelliğini aşağıdaki kodda gösterildiği gibi ayarlayın:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Hizmet İşlemlerine Erişimi Yetkilendirme](./samples/authorizing-access-to-service-operations.md)
- [Güvenliğe Genel Bakış](./feature-details/security-overview.md)
- [Hizmet Anlaşmalarını Uygulama](implementing-service-contracts.md)
