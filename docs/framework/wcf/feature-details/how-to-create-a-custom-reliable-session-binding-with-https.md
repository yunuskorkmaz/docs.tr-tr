---
title: 'Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039539"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma

Bu konu, Güvenli Yuva Katmanı (SSL) aktarım güvenliği ile güvenilir oturumlar kullanımını gösterir. Güvenilir oturum HTTPS üzerinden kullanmak için özel bağlama güvenilir oturum ve HTTPS aktarımı kullanan oluşturmanız gerekir. Güvenilir oturum kesin kod kullanarak veya bildirimli olarak yapılandırma dosyasında etkinleştirin. Güvenilir oturum etkinleştirmek için bu yordam istemci ve hizmet yapılandırma dosyalarını kullanır ve [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) öğesi.

Bu yordam önemli bir parçası olan  **\<uç noktası >** yapılandırma öğesi içeren bir `bindingConfiguration` adlı bir özel bağlama yapılandırma başvuran öznitelik `reliableSessionOverHttps`. [  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi ekleyerek bir güvenilir oturum ve HTTPS aktarımı kullanılan belirtmek için bu ada başvuran  **\< reliableSession >** ve  **\<httpsTransport >** öğeleri.

Bu örnekte kaynak kopyası için bkz: [özel bağlama güvenilir oturum HTTPS üzerinden](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Güvenilir oturum ile HTTPS kullanmak için bir CustomBinding ile hizmetini yapılandırma

1. Hizmet türü için bir hizmet anlaşmasını tanımlar.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Hizmet sözleşmesi bir hizmet sınıfında uygulayın. Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgileri almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Oluşturma bir *Web.config* yapılandırmak için bir uç nokta için bir dosya `CalculatorService` adlı özel bir bağlama ile `reliableSessionOverHttps` güvenilir bir oturum ve HTTPS aktarımı kullanır.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Oluşturma bir *Service.svc* satırını içeren dosya:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Bir yerde *Service.svc* Internet Information Services (IIS) sanal dizininizin dosyasında.

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Güvenilir oturum ile HTTPS kullanmak için bir CustomBinding ile istemciyi Yapılandırma

1. Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Oluşturulan istemci uygulaması da uygulamasını içerir `ClientCalculator`. Adres ve bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın. Yapılandırma dosyasından adres ve bağlama bilgilerini almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Adlı özel bir bağlama yapılandırmak `reliableSessionOverHttps` HTTPS aktarımı ve güvenilir oturumlar kullanılacak.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırma.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Derleyin ve istemci çalıştırın.  

## <a name="net-framework-security"></a>.NET Framework güvenliği

Bu örnekte kullanılan sertifika ile oluşturulan bir test sertifikası olduğundan *Makecert.exe*, bir HTTPS adresi gibi erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc`, tarayıcınız üzerinden.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
