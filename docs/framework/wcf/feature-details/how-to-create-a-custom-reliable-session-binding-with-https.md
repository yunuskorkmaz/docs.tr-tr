---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma'
title: 'Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 97e0386c3694552099a623a319f566fa4db2a39b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756181"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma

Bu konu, güvenilir oturumlarla Güvenli Yuva Katmanı (SSL) aktarım güvenliği kullanımını gösterir. HTTPS üzerinden güvenilir bir oturum kullanmak için güvenilir bir oturum ve HTTPS taşıması kullanan özel bir bağlama oluşturmanız gerekir. Yapılandırma dosyasında kod kullanarak veya bildirimli olarak güvenilir oturumu imperatively etkinleştirirsiniz. Bu yordam, güvenilir oturumu ve öğesini etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) .

Bu yordamın anahtar bölümü, **\<endpoint>** yapılandırma öğesinin `bindingConfiguration` adlı bir özel bağlama yapılandırmasına başvuran bir özniteliği içermesi olur `reliableSessionOverHttps` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma öğesi, ve öğeleri dahil, güvenilir bir oturumun ve https taşımanın kullanıldığını belirtmek için bu ada başvurur **\<reliableSession>** **\<httpsTransport>** .

Bu örneğin kaynak kopyası için bkz. [https üzerinden özel bağlama güvenilir oturumu](../samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>HTTPS ile güvenilir bir oturum kullanmak için hizmeti bir CustomBinding ile yapılandırma

1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Hizmet sözleşmesini bir hizmet sınıfına uygulayın. Adresin veya bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın. Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Güvenilir bir  `CalculatorService` `reliableSessionOverHttps` oturum ve HTTPS taşıması kullanan adlı özel bir bağlama ile için bir uç nokta yapılandırmak üzere birWeb.configdosyası oluşturun.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Satırı içeren bir *Service. svc* dosyası oluşturun:

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. *Service. svc* dosyasını Internet INFORMATION SERVICES (IIS) sanal dizinine yerleştirin.

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>HTTPS ile güvenilir bir oturum kullanmak için istemciyi bir CustomBinding ile yapılandırma

1. Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Oluşturulan istemci uygulaması, uygulamasının uygulamasını da içerir `ClientCalculator` . Adres ve bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın. Yapılandırma dosyasından adres ve bağlama bilgilerini almak için kod yazmanız gerekmez.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. `reliableSessionOverHttps`Https aktarımını ve güvenilir oturumları kullanmak için adlı özel bir bağlama yapılandırın.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Uygulamasının bir örneğini oluşturun `ClientCalculator` ve ardından hizmet işlemlerini çağırın.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. İstemcisini derleyin ve çalıştırın.  

## <a name="net-framework-security"></a>.NET Framework güvenliği

Bu örnekte kullanılan sertifika *Makecert.exe* ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızla, gıbı bir https adresine erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc` .

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilir oturumlar](reliable-sessions.md)
