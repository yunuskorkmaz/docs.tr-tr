---
title: "Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama"
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
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9b90df85259dfe48f071ca2b4b8404cfe8e673e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-protectionlevel-property"></a>Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama
Uygun bir öznitelik uygulama ve özelliğini ayarlayarak koruma düzeyi ayarlayabilirsiniz. Her ileti tüm parçalarını etkilemek için hizmet düzeyinde koruma ayarlayabilirsiniz veya yöntemlerden ileti bölümleri için giderek daha çok parçalı düzeyde koruma ayarlayabilirsiniz. [!INCLUDE[crabout](../../../includes/crabout-md.md)]`ProtectionLevel` özelliği, bkz: [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Koruma düzeyleri yalnızca kodda, yapılandırmada yok ayarlayabilirsiniz.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Bir hizmet için tüm iletileri imzalamak için  
  
1.  Hizmet için bir arabirimi oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği hizmete ve ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.Sign>aşağıdaki kodda gösterildiği gibi (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Bir işlem için tüm ileti bölümleri imzalamak için  
  
1.  Hizmeti için bir arabirim oluşturma ve uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.  
  
2.  Bir yöntem bildirimi arabirimi ekleyin.  
  
3.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> özniteliğini yöntemine ve ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.Sign>aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Koruma hata iletileri  
 Bir hizmette oluşturulan özel durumlar SOAP hatalarının istemciye gönderilebilir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]kesinlikle oluşturma yazılan hataları, bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: hizmet sözleşmelerinde hata bildirme](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Bir hata iletisi koruma  
  
1.  Hata iletisini temsil eden bir tür oluşturun. Aşağıdaki örnek adlı bir sınıf oluşturur `MathFault` iki alanlara sahip.  
  
2.  Uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği türü ve <xref:System.Runtime.Serialization.DataMemberAttribute> aşağıdaki kodda gösterildiği gibi serileştirilmelidir, her bir alan özniteliği.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  Hata döndürecektir arabiriminde uygulamak <xref:System.ServiceModel.FaultContractAttribute> özniteliği hataya dönün ve ayarlama yöntemi `detailType` hata sınıfı tür parametresi.  
  
4.  Ayrıca oluşturucuda ayarlamak <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>İleti bölümleri koruma  
 Bir ileti kısımlarını korumak için bir ileti sözleşmesi kullanın. [!INCLUDE[crabout](../../../includes/crabout-md.md)]ileti sözleşmeleri için bkz: [kullanarak ileti sözleşmeleri](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>İleti gövdesi korumak için  
  
1.  İletiyi temsil eden bir tür oluşturun. Aşağıdaki örnekte bir `Company` iki alanlarla sınıfı `CompanyName` ve `CompanyID`.  
  
2.  Uygulama <xref:System.ServiceModel.MessageContractAttribute> öznitelik sınıfını ve ayarlayın <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Uygulama <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği, ileti başlığı ifade edilen ve ayarlanmış bir alana `ProtectionLevel` özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Uygulama <xref:System.ServiceModel.MessageBodyMemberAttribute> ileti gövdesi bir parçası olarak ifade edilen, ve ayarlanmış herhangi bir alan için `ProtectionLevel` özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri `ProtectionLevel` bir hizmet çeşitli yerlerde birkaç öznitelik sınıfları özelliği.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki kod örnek kodu derlemek için gereken ad alanlarını gösterir.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [Koruma Düzeylerini Anlama](../../../docs/framework/wcf/understanding-protection-level.md)
