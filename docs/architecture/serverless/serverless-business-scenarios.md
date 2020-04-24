---
title: Sunucusuz uygulamalar için örnek iş senaryoları ve kullanım örnekleri
description: Görüntü işlemeden mobil desteğe ve ETL işlem hattına kadar olan örneklere erişerek, uygulamalı bir yaklaşım ile sunucusuz öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 5c2ee70b86fbc9a54d2a532eaa3d7509f23825df
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135665"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Sunucusuz iş senaryoları ve kullanım örnekleri

Sunucusuz uygulamalar için birçok kullanım durumu ve senaryosu vardır. Bu bölümde, farklı senaryoları gösteren örnekler yer almaktadır. Senaryolar ilgili belgelerin ve genel kaynak kodu depolarının bağlantılarını içerir. Bu bölümdeki örnekler, kendi oluşturma ve sunucusuz çözümler uygulamanıza başlamanızı sağlar.

## <a name="big-data-processing"></a>Büyük veri işleme

![Şemayı eşleme/azaltma](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

Bu örnek, büyük bir veri kümesinde bir eşleme/azaltma işlemi yapmak için sunucusuz kullanır. 2017 ' de günde yeni York sarı vergilenme dönüşlerin ortalama hızını belirler.

[Büyük veri Işleme: Azure 'da sunucusuz MapReduce](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a>Sunucusuz uygulamalar oluşturma: Uygulamalı laboratuvar

Sunucu tarafı mantığı çalıştırmak ve sunucusuz mimariler oluşturmak için işlevleri kullanmayı öğrenin.

- İşletmeniz için en iyi Azure hizmetini seçme
- Azure Işlevleri oluşturma
- Tetikleyicileri kullanma
- Zincirleme işlevleri
- Uzun süre çalışan iş akışları
- İzleme
- Geliştirme, test ve dağıtım

[Sunucusuz uygulamalar oluşturma](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a>Müşteri İncelemeleri

Bu örnek, Visual Studio 'da C# sınıf kitaplıkları için yeni Azure Işlevleri araçları 'nı örnekler. Müşterilerin Azure depolama Blobları ve CosmosDB 'de depolanan ürün incelemelerini göndermesi için bir Web sitesi oluşturun. Azure bilişsel hizmetler 'i kullanarak müşteri incelemelerinin otomatik olarak yönetimini gerçekleştirmek için bir Azure Işlevi ekleyin. Web sitesini işlevden ayırmak için bir Azure depolama kuyruğu kullanın.

[Bilişsel hizmetler ile müşteri Incelemeleri uygulaması](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a>Docker Linux görüntü desteği

Bu örnek, bir Linux Docker `Dockerfile` kapsayıcısında Azure işlevleri oluşturmak ve çalıştırmak için nasıl oluşturulacağını gösterir.

[Linux 'ta Azure Işlevleri](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a>Dosya işleme ve doğrulama

Bu örnek, kuramsal müşterilerden bir CSV dosyası kümesini ayrıştırır. "Batch" müşterisi için gereken tüm dosyaların kullanılabilir olmasını sağlar ve sonra her bir dosyanın yapısını doğrular. Azure Işlevleri, Logic Apps ve Dayanıklı İşlevler kullanılarak farklı çözümler sunulmaktadır.

[Azure Işlevleri, Logic Apps ve Dayanıklı İşlevler kullanarak dosya işleme ve doğrulama](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a>Oyun verileri görselleştirme

![Oyun telemetrisi](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

Bir geliştiricinin oyunları için bir düzenleyici veri görselleştirme çözümünü nasıl uygulayamayacağı hakkında bir örnek. Aslında, bir Unreal Engine 4 eklentisi ve Unity eklentisi arka ucu olarak bu örnek kullanılarak geliştirilmiştir. Hizmet bileşeni, oyun altyapısı belirsiz.

[Düzenleyici içi oyun telemetri görselleştirmesi](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a>GraphQL

GraphQL API 'sini kullanıma sunan sunucusuz bir işlev oluşturun.

[GraphQL için sunucusuz işlevler](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a>Nesnelerin İnterneti (IoT) güvenilir Edge geçişi

![IoT mimarisi](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

Bu örnek, IoT cihazlarından güvenilir yukarı akış iletişimini etkinleştirmek için yeni bir iletişim protokolü uygular. Veri boşluğu algılamayı ve geri dolguyu otomatikleştirir.

[IoT güvenilir Edge geçişi](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a>Mikro hizmetler başvuru mimarisi

![Başvuru mimarisi](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

Reuna bulut uygulamasına (kurgusal bir şirket) göre grup tasarlama, geliştirme ve sunma konusunda karar veren işlem sürecinde size kılavuzluk eden bir başvuru mimarisi. Mimarinin tüm bileşenlerini yapılandırmaya ve dağıtmaya yönelik uygulamalı yönergeler içerir.

[Sunucusuz mikro hizmetler başvuru mimarisi](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a>Konsol uygulamalarını sunucusuz 'e geçirme

Bu örnek, herhangi bir konsol uygulamasını`.csx` Azure IŞLEVLERINDE bir http Web hizmetine dönüştürmek için kullanılabilen genel bir işlevdir (dosya). Tek yapmanız gereken, `.exe`bir yapılandırma dosyasını düzenleyeceğiniz ve öğesine bağımsız değişken olarak geçirilecek giriş parametrelerini belirtmelidir.

[Konsol uygulamalarını Azure Işlevleri üzerinde çalıştırma](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a>Mobil için sunucusuz

Azure Işlevlerinin kolayca uygulanması ve bakımını yapmak ve HTTP üzerinden erişilebilir olması kolay bir işlemdir. Bir mobil uygulama için API uygulamanın harika bir yoludur. Microsoft, Xamarin ile iOS, Android ve Windows için harika platformlar arası araçlar sunar. Bu nedenle, Xamarin ve Azure Işlevleri birlikte harika çalışmaktadır. Bu makalede, Azure Web portalında veya Visual Studio 'da ilk olarak Azure Işlevinin nasıl uygulanacağı ve Android, iOS ve Windows üzerinde çalışan Xamarin. Forms ile platformlar arası istemci oluşturma işlemlerinin nasıl yapılacağı gösterilir.

[Xamarin. Forms istemcisiyle basit bir Azure Işlevi uygulama](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a>Sunucusuz mesajlaşma

Bu örnek, her sayıdaki oturum/bölüm arasında rastgele sayıda ileti yüklemek için Dayanıklı İşlevler ' fan çıkış deseninin nasıl kullanılacağını gösterir. Service Bus, Event Hubs veya depolama kuyruklarını hedefler. Örnek ayrıca, başka bir Azure Işleviyle bu iletileri kullanma ve sonuç zamanlama verilerini başka bir olay hub 'ına yükleme özelliğini de ekler. Veriler daha sonra Azure Veri Gezgini gibi analiz hizmetlerine alınır.

[Azure Işlevleri ile Service Bus, Event Hubs ve depolama kuyrukları aracılığıyla ileti oluşturun ve kullanın](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a>Önerilen Kaynaklar

- [Linux 'ta Azure Işlevleri](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [Büyük veri Işleme: Azure 'da sunucusuz MapReduce](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [Sunucusuz uygulamalar oluşturma](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [Bilişsel hizmetler ile müşteri Incelemeleri uygulaması](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [Azure Işlevleri, Logic Apps ve Dayanıklı İşlevler kullanarak dosya işleme ve doğrulama](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [Xamarin. Forms istemcisiyle basit bir Azure Işlevi uygulama](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Düzenleyici içi oyun telemetri görselleştirmesi](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [IoT güvenilir Edge geçişi](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [Azure Işlevleri ile Service Bus, Event Hubs ve depolama kuyrukları aracılığıyla ileti oluşturun ve kullanın](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [Konsol uygulamalarını Azure Işlevleri üzerinde çalıştırma](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [GraphQL için sunucusuz işlevler](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [Sunucusuz mikro hizmetler başvuru mimarisi](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
>[Önceki](orchestration-patterns.md)
>[İleri](serverless-conclusion.md)
