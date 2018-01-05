---
title: "Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma"
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
helpviewer_keywords: duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 003b07326612f3b51390d691c7bba0ef1c1b85dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-duplex-contract"></a>Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma
Bu konuda, çift yönlü (iki yönlü) sözleşme kullanan yöntemleri oluşturmak için temel adımlar gösterilmektedir. Çift yönlü sözleşme, istemciler ve sunucular ya da diğer çağrıları başlatmak için birbiriyle bağımsız olarak iletişim kurması sağlar. Çift yönlü sözleşme kullanılabilir üç ileti modelinden biridir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri. Diğer iki desenleri iletisi olan tek yönlü ve istek-yanıt. Çift yönlü sözleşme istemci ve sunucu arasında iki yönlü sözleşme oluşur ve yöntem çağrılarını ilintili olması gerekli değildir. Bu tür bir sözleşme hizmetiniz daha fazla bilgi için istemci sorgulamak veya açıkça istemci üzerindeki olaylara Yükselt kullanın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz. çift yönlü bir sözleşme için bir istemci uygulaması oluşturma [nasıl yapılır: çift yönlü sözleşme ile Erişim Hizmetleri](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Çalışma örnek için bkz: [çift yönlü](../../../../docs/framework/wcf/samples/duplex.md) örnek.  
  
### <a name="to-create-a-duplex-contract"></a>Çift yönlü sözleşme oluşturmak için  
  
1.  Çift yönlü sözleşme sunucu tarafı yapar arabirimi oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  Arabirimdeki yöntem imzaları bildirin.  
  
4.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel sözleşmesinin bir parçası olması her yöntem imzası sınıfı.  
  
5.  İstemcide hizmet çağırabileceği işlemler kümesini tanımlar geri çağırma arabirimi oluşturun.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  Geri çağırma arabirimi yöntemi imzalarında bildirin.  
  
7.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel sözleşmesinin bir parçası olması her yöntem imzası sınıfı.  
  
8.  Ayarlayarak çift yönlü bir sözleşme iki arabirim bağlantı <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> türde bir geri çağırma arabirimi birincil arabirim özelliği.  
  
### <a name="to-call-methods-on-the-client"></a>İstemcide yöntemleri çağırmak için  
  
1.  Birincil sözleşme hizmetin uygulamasında geri çağırma arabirimi için bir değişken bildirin.  
  
2.  Tarafından döndürülen nesne başvuru değişkenini <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> yöntemi <xref:System.ServiceModel.OperationContext> sınıfı.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  Geri çağırma arabirimi tarafından tanımlanan yöntemler çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, çift yönlü iletişimi gösterir. Hizmetin sözleşme taşıma için hizmet işlemleri ileriye ve geriye doğru içerir. İstemcinin sözleşme konumuna raporlama için bir hizmet işlemi içerir.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri Web Hizmetleri Açıklama Dili (WSDL) hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını sağlar.  
  
-   Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSDL belgesi (isteğe bağlı) kodu ve bir istemci için yapılandırma alınamadı.  
  
-   Çift yönlü hizmetler gösterme uç noktalarını güvenli hale getirilmelidir. Bir hizmet çift yönlü bir ileti aldığında, yanıt gönderileceği yeri belirlemek için bu gelen iletide ReplyTo bakar. Ardından kanal sağlanmazsa, güvenilmeyen bir istemci hedef makine hizmet reddine için önde gelen bir hedef makinenin ReplyTo içeren kötü amaçlı bir ileti gönderebilir. Normal istek-yanıt iletileri, bu bir sorun ReplyTo dikkate alınmaz ve orijinal iletinin geldiği üzerinde kanalda gönderilen yanıtı olmadığından.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Çift Yönlü](../../../../docs/framework/wcf/samples/duplex.md)  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Oturum](../../../../docs/framework/wcf/samples/session.md)
