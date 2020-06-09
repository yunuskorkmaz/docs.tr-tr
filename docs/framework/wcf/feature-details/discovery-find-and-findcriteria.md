---
title: Keşif Bulma ve FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 1d6a0e3fcca45c3fe57aab84b0f2b6b86fabb404
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599184"
---
# <a name="discovery-find-and-findcriteria"></a>Keşif Bulma ve FindCriteria

Bir bulma bul işlemi, bir veya daha fazla hizmeti bulmak için istemci tarafından başlatılır ve bulma işlemindeki ana eylemlerden biridir. Find işlemi gerçekleştirmek, ağ üzerinden WS-Discovery araştırma iletisi gönderir. WS-Discovery ProbeMatch iletileriyle Yanıtla belirtilen ölçütlerle eşleşen hizmetler. Bulma iletileri hakkında daha fazla bilgi için bkz. [WS-Discovery belirtimi](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>DiscoveryClient

Sınıfı, bulma <xref:System.ServiceModel.Discovery.DiscoveryClient> işlemlerini gerçekleştirmek için mekanizma sağlar ve bulma istemci işlemlerini kolay hale getirir. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>Bir (engelleyici) zaman uyumlu bulma gerçekleştiren ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> engelleyici olmayan bir zaman uyumsuz bulma Başlatan bir yöntemi içerir. Her iki yöntem de bir <xref:System.ServiceModel.Discovery.FindCriteria> parametre alır ve bir nesne aracılığıyla kullanıcıya sonuçlar sağlar <xref:System.ServiceModel.Discovery.FindResponse> .

## <a name="findcriteria"></a>FindCriteria

<xref:System.ServiceModel.Discovery.FindCriteria>, aradığınız Hizmetleri belirten arama ölçütlerine göre gruplanabilir ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilecekleri çeşitli özelliklere sahiptir. <xref:System.ServiceModel.Discovery.FindCriteria>, Birden çok arama ölçütü içerebilir. Varsayılan olarak, hizmetin kendisini eşleşen bir hizmeti düşünmediği, varsayılan olarak tüm bileşenlerle eşleşmesi gerekir. Yalnızca bazı ölçütlere uyan hizmetleri bulmak istiyorsanız, hizmette özel bulma mantığı uygulayabilir veya birden çok sorgu kullanabilirsiniz.

Arama ölçütleri şunları içerir:

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>Seçim. Aranmakta olan hizmetin sözleşme adı ve genellikle bir hizmet aranırken kullanılan ölçütler. Birden fazla sözleşme adı belirtilmişse, yalnızca tüm sözleşmeleri eşleştiren hizmet uç noktaları yanıtlayabilir. WCF 'de bir uç noktanın yalnızca bir sözleşmeyi destekleyebileceğini unutmayın.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement>Seçim. Kapsamlar, ayrı hizmet uç noktalarını sınıflandırmak için kullanılan mutlak URI 'Lerdir. Bu, birden çok uç noktanın aynı sözleşmeyi kullanıma sunduğundan ve uç noktaların bir alt kümesini aramak için bir yol olmasını istediğiniz senaryolarda kullanmak isteyebilirsiniz. Birden fazla kapsam belirtilmişse, yalnızca tüm kapsamlar ile eşleşen hizmet uç noktaları yanıt verebilir.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A>-Araştırma iletisindeki kapsamları uç noktayla eşleştirirken kullanılacak eşleşen algoritmayı belirtir. Desteklenen beş kapsam eşleştirme kuralı vardır:

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>, temel büyük/küçük harfe duyarlı bir dize karşılaştırması yapar.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>"/" ile ayrılmış kesimlerle eşleşir. İçin arama `http://contoso/building1` , kapsama sahip bir hizmetle eşleşir `http://contoso/building/floor1` . Bu `http://contoso/building100` , son iki segment eşleşmediğinden eşleşmez.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>bir LDAP URL 'SI kullanarak kapsamları segmentlere göre eşler.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>kapsamları tam olarak bir UUID dizesi kullanarak eşleştirir.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>yalnızca bir kapsam belirtmeyen hizmetlerle eşleşir.

  Kapsam eşleştirme kuralı belirtilmemişse, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> kullanılır.

Sonlandırma ölçütleri şunları içerir:

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>-Ağdaki hizmetlerden gelen yanıtlar için beklenecek en uzun süre. Varsayılan süre 20 saniyedir.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>-Beklenecek en fazla yanıt sayısı. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>Yanıtların <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> süresi geçtiğinde alındıktan sonra bulma işlemi sonlanır.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse><xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A>, ağda eşleşen hizmetler tarafından gönderilen yanıtları içeren bir koleksiyon özelliğine sahiptir. Hiçbir hizmet yanıtlanmadan, koleksiyon boştur. Bir veya daha fazla hizmet yanıtladıysanız, her yanıt bir nesne içinde depolanır <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> ve bu hizmetle ilgili adres, sözleşme ve bazı ek bilgiler bulunur.

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

- [WCF Keşif Genel Bakış](wcf-discovery-overview.md)
- [Keşif İstemcisi Kanalını Kullanma](using-the-discovery-client-channel.md)
- [Kapsamlarla Bulma](../samples/discovery-with-scopes-sample.md)
- [Temel](../samples/basic-sample.md)
