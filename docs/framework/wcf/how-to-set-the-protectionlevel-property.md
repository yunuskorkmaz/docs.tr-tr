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
ms.openlocfilehash: ce9fc8549218db5a1446026421f1a7ba1e5a23aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089854"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama
Uygun bir öznitelik uygulamak ve özelliğini ayarlayarak, koruma düzeyini ayarlayabilirsiniz. Her bir iletinin tüm bölümlerinde etkilemek için hizmet düzeyinde koruma ayarlayabilirsiniz veya yöntemlerinden message bölümleri için giderek daha ayrıntılı bir düzeyde koruma ayarlayabilirsiniz. Hakkında daha fazla bilgi için `ProtectionLevel` özelliğine bakın [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Koruma düzeyleri yalnızca kod, yapılandırmada yok ayarlayabilirsiniz.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Bir hizmet için tüm iletileri imzalamak için  
  
1.  Hizmet için bir arabirimi oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği hizmete ve ayarlama <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.Sign>aşağıdaki kodda gösterildiği gibi (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Bir işlem için tüm ileti bölümleri imzalamak için  
  
1.  Hizmet için bir arabirim oluşturma ve uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.  
  
2.  Yöntem bildiriminde arabirimi ekleyin.  
  
3.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> özniteliğini yöntemine ve ayarlama <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.Sign>aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Koruma hata iletileri  
 Bir hizmette oluşturulan özel durumlar SOAP hatalarının istemciye gönderilebilir. Hataları kesin oluşturma hakkında daha fazla bilgi yazılan için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: Hizmet sözleşmelerinde hata bildirme](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Bir hata iletisi koruma  
  
1.  Hata iletisini temsil eden bir tür oluşturun. Aşağıdaki örnekte adlı bir sınıf oluşturur `MathFault` ile iki alan.  
  
2.  Uygulama <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik türü için ve bir <xref:System.Runtime.Serialization.DataMemberAttribute> aşağıdaki kodda gösterildiği gibi seri hale getirilmesi, her alan için özniteliği.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  Hata döndüren arabiriminde uygulamak <xref:System.ServiceModel.FaultContractAttribute> özniteliğini hatasına dönün ve ayarlamanız yöntemine `detailType` hata sınıf türü parametresi.  
  
4.  Oluşturucu ayrıca ayarlamanız <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>İleti bölümlerini koruma  
 Bir ileti bölümlerini koruma için bir ileti anlaşması kullanın. İleti sözleşmeleri hakkında daha fazla bilgi için bkz: [kullanarak ileti sözleşmeleri](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>İleti gövdesi korumak için  
  
1.  İletiyi temsil eden bir tür oluşturun. Aşağıdaki örnek, oluşturur bir `Company` iki alan sınıfıyla `CompanyName` ve `CompanyID`.  
  
2.  Uygulama <xref:System.ServiceModel.MessageContractAttribute> ayarlayın ve öznitelik sınıfına <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Uygulama <xref:System.ServiceModel.MessageHeaderAttribute> öznitelik, bir ileti üst bilgisi ifade edilen ve ayarlanmış bir alana `ProtectionLevel` özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Uygulama <xref:System.ServiceModel.MessageBodyMemberAttribute> ileti gövdesi bir parçası olarak ifade edilen, ve ayarlanmış herhangi bir alan için `ProtectionLevel` özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri `ProtectionLevel` birkaç öznitelik sınıfları bir hizmet çeşitli yerlerde özelliği.  
  
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
