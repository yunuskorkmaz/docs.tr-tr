---
title: 'Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950973"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama
Uygun bir öznitelik uygulayıp özelliği ayarlayarak koruma düzeyini ayarlayabilirsiniz. Her iletinin tüm bölümlerini etkilemek için hizmet düzeyinde koruma ayarlayabilir veya yöntemlerle ileti bölümlerine kadar artan parçalı düzeylerde koruma ayarlayabilirsiniz. `ProtectionLevel` Özelliği hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
> Yapılandırma bölümünde değil, yalnızca kodda koruma düzeylerini ayarlayabilirsiniz.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Bir hizmetin tüm iletilerini imzalamak için  
  
1. Hizmet için bir arabirim oluşturun.  
  
2. Özniteliğini hizmetine uygulayın ve aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.Sign>olarak ayarlayın (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>). <xref:System.ServiceModel.ServiceContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Bir işlemin tüm ileti parçalarını imzalamak için  
  
1. Hizmet için bir arabirim oluşturun ve <xref:System.ServiceModel.ServiceContractAttribute> özniteliği arabirimine uygulayın.  
  
2. Arabirime bir yöntem bildirimi ekleyin.  
  
3. Özniteliğini yöntemine uygulayın ve aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini olarak <xref:System.Net.Security.ProtectionLevel.Sign>ayarlayın. <xref:System.ServiceModel.OperationContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Hata Iletilerini koruma  
 Bir hizmette oluşturulan özel durumlar, bir istemciye SOAP hatası olarak gönderilebilir. Türü kesin belirlenmiş hatalar oluşturma hakkında daha fazla bilgi için bkz. [sözleşmelerdeki ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: Hizmet sözleşmeleri](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)hatalarını bildirin.  
  
#### <a name="to-protect-a-fault-message"></a>Bir hata iletisini korumak için  
  
1. Hata iletisini temsil eden bir tür oluşturun. Aşağıdaki örnek, iki alanı olan adlı `MathFault` bir sınıf oluşturur.  
  
2. Aşağıdaki kodda gösterildiği gibi, <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğinitürüneveserileştirilmesigerekenheralanabirözniteliğeuygulayın.<xref:System.Runtime.Serialization.DataContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. Hatayı döndürecek arabirimde, <xref:System.ServiceModel.FaultContractAttribute> özniteliği hatayı döndürecek yönteme uygulayın ve `detailType` parametreyi hata sınıfının türü olarak ayarlayın.  
  
4. Ayrıca oluşturucuda, aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ileti parçalarını koruma  
 İleti parçalarını korumak için bir ileti sözleşmesi kullanın. İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>İleti gövdesini korumak için  
  
1. İletiyi temsil eden bir tür oluşturun. Aşağıdaki örnek, `CompanyName` iki alan `Company` ve `CompanyID`içeren bir sınıf oluşturur.  
  
2. Özniteliğini sınıfına uygulayın ve <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın. <xref:System.ServiceModel.MessageContractAttribute>  
  
3. Özniteliğini, <xref:System.ServiceModel.MessageHeaderAttribute> ileti üst bilgisi olarak ifade edilecek bir alana uygulayın ve `ProtectionLevel` özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın.  
  
4. İleti gövdesinin bir parçası olarak ifade edilecek herhangi bir alana uygulayın ve aşağıdaki örnekte gösterildiği gibi `ProtectionLevel` özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın. <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir hizmetin `ProtectionLevel` çeşitli yerlerinde birkaç öznitelik sınıfının özelliğini ayarlar.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki kod, örnek kodu derlemek için gereken ad alanlarını gösterir.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Koruma Düzeylerini Anlama](../../../docs/framework/wcf/understanding-protection-level.md)
