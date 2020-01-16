---
title: Keşif Bulma ve FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: da4c3c4a1d765e4f91b03f4f8fc1a73c3fea1535
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964844"
---
# <a name="discovery-find-and-findcriteria"></a>Keşif Bulma ve FindCriteria

Bir bulma bul işlemi, bir veya daha fazla hizmeti bulmak için istemci tarafından başlatılır ve bulma işlemindeki ana eylemlerden biridir. Find işlemi gerçekleştirmek, ağ üzerinden WS-Discovery araştırma iletisi gönderir. WS-Discovery ProbeMatch iletileriyle Yanıtla belirtilen ölçütlerle eşleşen hizmetler. Bulma iletileri hakkında daha fazla bilgi için bkz. [WS-Discovery belirtimi](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>DiscoveryClient

<xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfı, bulma işlemlerini gerçekleştirme mekanizmasını sağlar ve bulma istemci işlemlerini kolay hale getirir. Bir (engelleyici) zaman uyumlu bul gerçekleştiren bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi ve engelleyici olmayan bir zaman uyumsuz bulma Başlatan bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> yöntemi içerir. Her iki yöntem de <xref:System.ServiceModel.Discovery.FindCriteria> bir parametre alır ve kullanıcıya sonuçları bir <xref:System.ServiceModel.Discovery.FindResponse> nesnesi aracılığıyla sağlar.

## <a name="findcriteria"></a>FindCriteria

<xref:System.ServiceModel.Discovery.FindCriteria>, aradığınız Hizmetleri belirten arama ölçütlerine göre gruplanabilir ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilecekleri çeşitli özelliklere sahiptir. <xref:System.ServiceModel.Discovery.FindCriteria>, birden çok arama ölçütü içerebilir. Varsayılan olarak, hizmetin kendisini eşleşen bir hizmeti düşünmediği, varsayılan olarak tüm bileşenlerle eşleşmesi gerekir. Yalnızca bazı ölçütlere uyan hizmetleri bulmak istiyorsanız, hizmette özel bulma mantığı uygulayabilir veya birden çok sorgu kullanabilirsiniz.

Arama ölçütleri şunları içerir:

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>-Isteğe bağlı. Aranmakta olan hizmetin sözleşme adı ve genellikle bir hizmet aranırken kullanılan ölçütler. Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmeleri eşleştiren hizmet uç noktaları yanıtlayabilir. WCF 'de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement>-Isteğe bağlı. Kapsamlar, ayrı hizmet uç noktalarını sınıflandırmak için kullanılan mutlak URI 'Lerdir. Bu, birden çok uç noktanın aynı sözleşmeyi kullanıma sunduğundan ve uç noktaların bir alt kümesini aramak için bir yol olmasını istediğiniz senaryolarda kullanmak isteyebilirsiniz. Birden fazla kapsam belirtilmişse, yalnızca tüm kapsamlar ile eşleşen hizmet uç noktaları yanıt verebilir.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A>-bitiş noktası ile araştırma iletisindeki kapsamları eşleştirirken kullanılacak eşleşen algoritmayı belirtir. Desteklenen beş kapsam eşleştirme kuralı vardır:

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>, temel büyük/küçük harfe duyarlı bir dize karşılaştırması yapar.

  - "/" ile ayrılmış kesimlerle eşleşen <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>. `http://contoso/building1` araması, kapsam `http://contoso/building/floor1`bir hizmetle eşleşiyor. Son iki segment eşleşmediğinden `http://contoso/building100` eşleşmez.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>, bir LDAP URL 'SI kullanarak kapsamlarla eşler ile eşleşir.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>, kapsamlarla tam olarak bir UUID dizesi kullanarak eşleşir.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> yalnızca bir kapsam belirtmeyen hizmetlerle eşleşir.

  Kapsam eşleştirme kuralı belirtilmemişse, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> kullanılır.

Sonlandırma ölçütleri şunları içerir:

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>-ağdaki hizmetlerden gelen yanıtlar için beklenecek en uzun süre. Varsayılan süre 20 saniyedir.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>-beklenecek en fazla yanıt sayısı. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçmeden önce <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> yanıtları alınıyorsa, bulma işlemi sona erer.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse>, ağda eşleşen hizmetler tarafından gönderilen yanıtları içeren bir <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> Collection özelliğine sahiptir. Hiçbir hizmet yanıtlanmadan, koleksiyon boştur. Bir veya daha fazla hizmet yanıtladıysanız, her yanıt adresi, sözleşmeyi ve hizmetle ilgili bazı ek bilgileri içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> nesnesinde depolanır.

Aşağıdaki örnek, kodda bulma işleminin nasıl gerçekleştirileceğini gösterir.

```csharp
// Create DiscoveryClient
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());

// Create FindCriteria
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));
findCriteria.Duration = TimeSpan.FromSeconds(10);

// Find ICalculatorService endpoints
FindResponse findResponse = discoveryClient.Find(findCriteria);

Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)
```

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Keşif İstemcisi Kanalını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
- [Kapsamlarla Bulma](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Temel](../../../../docs/framework/wcf/samples/basic-sample.md)
