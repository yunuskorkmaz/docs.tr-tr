---
title: 'Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: c00e5d8e50de89d3d4d346ccddc50282f24735b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332137"
---
# <a name="how-to-create-a-duplex-contract"></a>Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma
Bu konu, çift yönlü Sözleşme (iki yönlü) kullanan yöntemleri oluşturmak için temel adımları gösterir. Çift yönlü sözleşme, istemciler ve sunucular ya da diğer çağrıları başlatabilir, böylece birbiriyle bağımsız olarak iletişim kurmasına izin verir. Çift yönlü sözleşme Windows Communication Foundation (WCF) Hizmetleri için kullanılabilir üç ileti modelinden biridir. Diğer iki ileti desenleri olan tek yönlü ve istek-yanıt. Çift yönlü sözleşme, istemci ve sunucu arasında iki yönlü sözleşmeler oluşur ve yöntem çağrıları bağıntılı gerekli değildir. Bu tür bir sözleşme hizmetiniz daha fazla bilgi için istemci sorgu veya olay istemci üzerinde açıkça kullanın. Bir istemci uygulaması için çift yönlü sözleşme oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişme](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Çalışma örnek için bkz: [çift yönlü](../../../../docs/framework/wcf/samples/duplex.md) örnek.  
  
### <a name="to-create-a-duplex-contract"></a>Çift yönlü sözleşme oluşturma  
  
1. Çift yönlü sözleşme sunucu tarafı yapan arabirim oluşturun.  
  
2. Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Yöntem imzaları arabiriminde bildirin.  
  
4. Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel sözleşmesinin bir parçası olması gereken her yöntem imzası için sınıf.  
  
5. İstemcide hizmet çağırabilirsiniz işlemler kümesini tanımlayan bir geri arama arabirimini oluşturun.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Geri arama arabirimini yöntem imzaları bildirin.  
  
7. Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel sözleşmesinin bir parçası olması gereken her yöntem imzası için sınıf.  
  
8. İki arabirim çift yönlü sözleşme ayarlayarak bağlantı <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> geri arama arabirimini türü için birincil arabirim özelliği.  
  
### <a name="to-call-methods-on-the-client"></a>İstemci üzerinde yöntemleri çağırmak için  
  
1. Birincil sözleşme hizmetin uygulamasında geri çağırma arabirimi için bir değişken bildirir.  
  
2. Tarafından döndürülen nesne başvuru değişkenini <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> yöntemi <xref:System.ServiceModel.OperationContext> sınıfı.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Geri çağırma arabirim tarafından tanımlanan yöntemler çağırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, çift yönlü iletişimi gösterir. Taşıma için hizmet işlemleri ileriye ve geriye doğru hizmet sözleşmesi içeriyor. İstemcinin konumuna raporlama için bir hizmet işlemi içeriyor.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri, Web Hizmetleri Açıklama Dili (WSDL) hizmet sözleşme tanımları otomatik olarak oluşturulmasını sağlar.  
  
-   Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSDL belgesi (isteğe bağlı) kodu ve bir istemci yapılandırması alınamıyor.  
  
-   Çift yönlü hizmetler gösterme uç noktalarını güvenli hale getirilmelidir. Bir hizmeti çift yönlü bir ileti aldığında yanıt göndermesi yerini belirlemek için gelen bu iletide ReplyTo bakar. Ardından kanal güvenli değildir, güvenilmeyen bir istemci bir hedef makine, hizmet reddi için önde gelen bir hedef makinenin ReplyTo içeren kötü amaçlı bir ileti gönderebilir. Normal istek-yanıt iletileri, bu bir sorun ReplyTo göz ardı edilir ve yanıt üzerinde özgün iletinin geldiği kanal üzerinde gönderilen değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Çift Yönlü](../../../../docs/framework/wcf/samples/duplex.md)
- [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Oturum](../../../../docs/framework/wcf/samples/session.md)
