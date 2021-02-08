---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: ProtectionLevel özelliğini ayarlama'
title: 'Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 526ed923d254f0312c9a2c6d17b7306973d88902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779250"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama

Uygun bir öznitelik uygulayıp özelliği ayarlayarak koruma düzeyini ayarlayabilirsiniz. Her iletinin tüm bölümlerini etkilemek için hizmet düzeyinde koruma ayarlayabilir veya yöntemlerle ileti bölümlerine kadar artan parçalı düzeylerde koruma ayarlayabilirsiniz. Özelliği hakkında daha fazla bilgi için `ProtectionLevel` bkz. [koruma düzeyini anlama](understanding-protection-level.md).  
  
> [!NOTE]
> Yapılandırma bölümünde değil, yalnızca kodda koruma düzeylerini ayarlayabilirsiniz.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Bir hizmetin tüm iletilerini imzalamak için  
  
1. Hizmet için bir arabirim oluşturun.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute>Özniteliğini hizmetine uygulayın ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.Sign> aşağıdaki kodda gösterildiği gibi özelliğini olarak ayarlayın (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> ).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Bir işlemin tüm ileti parçalarını imzalamak için  
  
1. Hizmet için bir arabirim oluşturun ve <xref:System.ServiceModel.ServiceContractAttribute> özniteliği arabirimine uygulayın.  
  
2. Arabirime bir yöntem bildirimi ekleyin.  
  
3. <xref:System.ServiceModel.OperationContractAttribute>Özniteliğini yöntemine uygulayın ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.Sign> aşağıdaki kodda gösterildiği gibi özelliğini olarak ayarlayın.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Hata Iletilerini koruma  

 Bir hizmette oluşturulan özel durumlar, bir istemciye SOAP hatası olarak gönderilebilir. Türü kesin belirlenmiş hatalar oluşturma hakkında daha fazla bilgi için bkz. [sözleşmelerdeki ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: hizmet sözleşmelerinde hata bildirme](how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Bir hata iletisini korumak için  
  
1. Hata iletisini temsil eden bir tür oluşturun. Aşağıdaki örnek, iki alanı olan adlı bir sınıf oluşturur `MathFault` .  
  
2. <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> Aşağıdaki kodda gösterildiği gibi, özniteliğini türüne ve serileştirilmesi gereken her alana bir özniteliğe uygulayın.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. Hatayı döndürecek arabirimde, <xref:System.ServiceModel.FaultContractAttribute> özniteliği hatayı döndürecek yönteme uygulayın ve `detailType` parametreyi hata sınıfının türü olarak ayarlayın.  
  
4. Ayrıca oluşturucuda, <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> aşağıdaki kodda gösterildiği gibi özelliğini olarak ayarlayın.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ileti parçalarını koruma  

 İleti parçalarını korumak için bir ileti sözleşmesi kullanın. İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](./feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>İleti gövdesini korumak için  
  
1. İletiyi temsil eden bir tür oluşturun. Aşağıdaki örnek `Company` , iki alan ve içeren bir sınıf oluşturur `CompanyName` `CompanyID` .  
  
2. <xref:System.ServiceModel.MessageContractAttribute>Özniteliğini sınıfına uygulayın ve <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğini olarak ayarlayın <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> .  
  
3. Özniteliğini, <xref:System.ServiceModel.MessageHeaderAttribute> ileti üst bilgisi olarak ifade edilecek bir alana uygulayın ve `ProtectionLevel` özelliğini olarak ayarlayın <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> .  
  
4. <xref:System.ServiceModel.MessageBodyMemberAttribute>İleti gövdesinin bir parçası olarak ifade edilecek herhangi bir alana uygulayın ve `ProtectionLevel` <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `ProtectionLevel` bir hizmetin çeşitli yerlerinde birkaç öznitelik sınıfının özelliğini ayarlar.  
  
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
- [Koruma Düzeylerini Anlama](understanding-protection-level.md)
