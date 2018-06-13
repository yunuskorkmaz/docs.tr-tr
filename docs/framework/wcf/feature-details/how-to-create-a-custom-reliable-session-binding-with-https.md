---
title: 'Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: b3699593f783fff1227ec51194956e0cc8577dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492768"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma

Bu konu, Güvenli Yuva Katmanı (SSL) güvenilir oturumlar ile taşıma güvenliği kullanımını göstermektedir. HTTPS üzerinden güvenli bir oturum kullanmak için güvenilir bir oturum ve HTTPS taşıması kullanan özel bağlama oluşturmanız gerekir. Güvenilir oturum kodu kullanarak imperatively ya da bildirimli olarak yapılandırma dosyasında etkinleştirin. Güvenilir oturum etkinleştirmek için bu yordam istemci ve hizmet yapılandırma dosyalarını kullanır ve [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) öğesi.

Bu yordam önemli bir parçası olan  **\<uç noktası >** yapılandırma öğesi içeren bir `bindingConfiguration` adlı bir özel bağlama yapılandırma başvuran özniteliği `reliableSessionOverHttps`. [  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesine başvuruyor ekleyerek bir güvenilir oturum ve HTTPS taşıma kullanılan belirtmek için bu ad  **\< reliableSession >** ve  **\<httpsTransport >** öğeleri.

Bu örnekte kaynak kopyası için bkz: [özel bağlama güvenilir oturum HTTPS üzerinden](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Güvenilir bir oturum ile HTTPS kullanmak üzere bir CustomBinding ile hizmetini yapılandırma

1. Hizmet türü için bir hizmet sözleşmesini tanımlama.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Bir hizmet sınıfında Hizmet sözleşmesini uygulama. Adres veya bağlama bilgisi hizmet uygulaması içinde belirlenmezse unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgilerini almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Oluşturma bir *Web.config* için bir uç nokta yapılandırmak için bir dosya `CalculatorService` adlı özel bir bağlama ile `reliableSessionOverHttps` güvenilir bir oturum ve HTTPS aktarımı kullanır.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Oluşturma bir *Service.svc* bir çizgi içeren dosya:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Yer *Service.svc* , Internet Information Services (IIS) sanal dizinde dosya.

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>İstemci bir CustomBinding güvenilir bir oturum ile HTTPS kullanmak üzere yapılandırın

1. Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Oluşturulan istemci uygulaması da uyarlamasını içeren `ClientCalculator`. Adres ve bağlama bilgilerini hizmet uygulaması içinde belirlenmezse unutmayın. Yapılandırma dosyasından adres ve bağlama bilgilerini almak üzere kod yazmak için gerekli değildir.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Adlı özel bağlama yapılandırma `reliableSessionOverHttps` HTTPS taşıma ve güvenilir oturumlar kullanmak için.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemleri çağırın.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Derleme ve istemci çalıştırın.  

## <a name="net-framework-security"></a>.NET Framework güvenliği

Bu örnekte kullanılan sertifika ile oluşturulan bir test sertifikası olduğundan *Makecert.exe*, bir HTTPS adresi gibi erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc`, tarayıcınızdan.

## <a name="see-also"></a>Ayrıca bkz.

[Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
