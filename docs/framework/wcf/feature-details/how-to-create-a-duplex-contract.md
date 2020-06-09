---
title: 'Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598989"
---
# <a name="how-to-create-a-duplex-contract"></a>Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma
Bu konuda, çift yönlü (çift yönlü) bir sözleşme kullanan Yöntemler oluşturmaya yönelik temel adımlar gösterilmektedir. Çift yönlü bir anlaşma, istemcilerin ve sunucuların birbirleriyle her ikisi ile iletişim kurmasına olanak tanır; böylece birbirlerine çağrı başlatabilir. Çift yönlü sözleşme Windows Communication Foundation (WCF) Hizmetleri için kullanılabilen üç ileti deseninden biridir. Diğer iki ileti deseni tek yönlü ve istek-yanıt ' dir. Çift yönlü sözleşme, istemci ve sunucu arasındaki 2 1 yönlü sözleşmelerden oluşur ve yöntemin bağıntılı olmasını gerektirmez. Hizmetiniz daha fazla bilgi için istemciyi sorgulayıp istemci üzerinde açık bir olay oluşturması gerektiğinde bu tür bir sözleşmeyi kullanın. Bir çift yönlü sözleşme için istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme Ile hizmetlere erişme](how-to-access-services-with-a-duplex-contract.md). Çalışan bir örnek için bkz. [çift yönlü](../samples/duplex.md) örnek.  
  
### <a name="to-create-a-duplex-contract"></a>Çift yönlü sözleşme oluşturmak için  
  
1. Çift yönlü sözleşmenin sunucu tarafını oluşturan arabirimi oluşturun.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute>Sınıfı arabirime uygulayın.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Arabirimde Yöntem imzalarını bildirin.  
  
4. Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> ortak sözleşmenin bir parçası olması gereken her yöntem imzasına uygulayın.  
  
5. Hizmetin istemcide çağırabileceği işlem kümesini tanımlayan geri arama arabirimini oluşturun.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Çağrı arabirimindeki Yöntem imzalarını bildirin.  
  
7. Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> ortak sözleşmenin bir parçası olması gereken her yöntem imzasına uygulayın.  
  
8. <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A>Birincil arabirimdeki özelliği geri çağırma arabiriminin türüne ayarlayarak iki arabirimi çift yönlü bir sözleşmeye bağlayın.  
  
### <a name="to-call-methods-on-the-client"></a>İstemcideki yöntemleri çağırmak için  
  
1. Hizmetin birincil sözleşme uygulamasında geri çağırma arabirimi için bir değişken bildirin.  
  
2. Değişkenini, sınıfının metodu tarafından döndürülen nesne başvurusu olarak ayarlayın <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> <xref:System.ServiceModel.OperationContext> .  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Geri çağırma arabirimi tarafından tanımlanan yöntemleri çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği çift yönlü iletişimi gösterir. Hizmetin sözleşmesi, ileri ve geri gitmek için hizmet işlemlerini içerir. İstemci sözleşmesi, konumunu raporlamak için bir hizmet işlemi içerir.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <xref:System.ServiceModel.ServiceContractAttribute>Ve özniteliklerinin uygulanması, <xref:System.ServiceModel.OperationContractAttribute> Web Hizmetleri Açıklama DILI (wsdl) içinde hizmet sözleşmesi tanımlarının otomatik olarak oluşturulmasını sağlar.  
  
- İstemci için WSDL belgesi ve (isteğe bağlı) kodu ve yapılandırmasını almak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
- Çift yönlü hizmetleri açığa çıkaran uç noktalar güvenli olmalıdır. Bir hizmet çift yönlü bir ileti aldığında, yanıtın nereye gönderileceğini belirlemede bu gelen iletideki ReplyTo 'ya bakar. Kanal güvenli değilse, güvenilir olmayan bir istemci hedef makinenin ReplyTo olan kötü amaçlı bir ileti gönderebilir ve hedef makinenin hizmet reddine neden olur. Normal istek-yanıt iletileriyle bu bir sorun değildir, çünkü ReplyTo yoksayıldı ve yanıt özgün iletinin tarihinde geldiği kanalda gönderilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](how-to-access-services-with-a-duplex-contract.md)
- [Çift Yönlü](../samples/duplex.md)
- [Hizmetleri Tasarlama ve Uygulama](../designing-and-implementing-services.md)
- [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../how-to-define-a-wcf-service-contract.md)
- [Oturum](../samples/session.md)
