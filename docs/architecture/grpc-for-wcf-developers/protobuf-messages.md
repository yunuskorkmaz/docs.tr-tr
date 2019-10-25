---
title: Prototipsiz iletiler-WCF geliştiricileri için gRPC
description: Daha fazla bilgi için bkz. IDL ve içinde C#oluşturulan prototip.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9943478698acfbb54b3e1dd0e6a856d11b9266c3
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846337"
---
# <a name="protobuf-messages"></a>Protobuf iletileri

Bu bölümde, `.proto` dosyalarında prototip iletilerinin nasıl bildirildiği, alan numaralarının ve türlerin temel kavramları açıklanmaktadır ve `protoc` derleyicisi tarafından oluşturulan C# koda bakar. Bölümün geri kalanı, farklı veri türlerinin prototipte nasıl temsil edildiği konusunda daha ayrıntılı bilgi sağlayacaktır.

## <a name="declaring-a-message"></a>İleti bildirme

WCF 'de, hisse senedi Pazar ticareti uygulaması için bir `Stock` sınıfı aşağıdaki örnekte olduğu gibi tanımlanabilir:

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Protoarabelleğe denk sınıfı uygulamak için, `.proto` dosyasında bildirilmelidir. `protoc` derleyici daha sonra yapı sürecinin bir parçası olarak .NET sınıfını oluşturur.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

İlk satır, kullanılmakta olan sözdizimi sürümünü bildirir. Dilin sürüm 3 2016 ' de yayımlanmıştır ve gRPC Hizmetleri için önerilen sürümdür.

`option csharp_namespace` satırı, oluşturulan C# türler için kullanılacak ad alanını belirtir. `.proto` dosyası diğer diller için derlendiğinde Bu seçenek yok sayılır. Prototip dosyalarının birkaç dilde dile özgü seçenekleri içermesi yaygındır.

`Stock` ileti tanımı, her biri türü, adı ve alan numarası olan dört alanı belirtir.

## <a name="field-numbers"></a>Alan numaraları

Alan numaraları, prototipin önemli bir parçasıdır. Bunlar, ikili kodlu verilerdeki alanları tanımlamak için kullanılır. Bu, sürümden hizmetinizin sürümüne değiştiremeyeceği anlamına gelir. Bunun avantajı, geriye doğru ve ileri uyumluluğun mümkün olmadır. Eksik değer olasılığı işlendiği sürece, istemciler ve hizmetler, hakkında bilgi sahibi olmadıkları alan numaralarını yok sayacaktır.

İkili biçimde, alan numarası bir tür tanımlayıcısıyla birleştirilir. 1 ile 15 arasında alan numaraları, tek bir bayt olarak türlerine göre kodlanabilir; 16 ile 2047 arasında sayılar 2 bayt sürer. Herhangi bir nedenden dolayı bir ileti üzerinde 2047 ' den fazla alana ihtiyacınız varsa daha yüksek bir değere geçebilirsiniz. 1 ile 15 arasındaki alan numaralarının tek baytlık tanımlayıcıları daha iyi performans sağlar, bu nedenle bunları en temel, sık kullanılan alanlar için kullanmanız gerekir.

## <a name="types"></a>Türler

Tür bildirimleri, [sonraki bölümde](protobuf-data-types.md)daha ayrıntılı bir şekilde ele alınan Prototiparabelleği yerel skaler veri türlerini kullanıyor. Bu bölümün geri kalanı, prototipin yerleşik türlerini kapsayacak ve bunların ortak .NET türleriyle ilişkisini göstermeyecektir.

> [!NOTE]
> Prototip `decimal` bir türü yerel olarak desteklemez, bu nedenle bunun yerine Double kullanılır. Tam ondalık duyarlık gerektiren uygulamalar için, bu bölümün sonraki bölümünde yer [alan Ondalıklar bölümüne](protobuf-data-types.md#decimals) bakın.

## <a name="the-generated-code"></a>Oluşturulan kod

Uygulamanızı yapılandırdığınızda, Prototipsiz iletilerinizin her biri için sınıflar oluşturur ve yerel türlerini C# türlerle eşleştireşlenir. Oluşturulan `Stock` türü aşağıdaki imzaya sahip olacaktır:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Oluşturulan gerçek kod bundan çok daha karmaşıktır, çünkü her bir sınıf kendisini seri hale getirmek için gereken tüm kodu ve ikili tel biçiminde seri durumdan çıkarmak için gereklidir.

### <a name="property-names"></a>Özellik adları

Prototip derleyicinin, `.proto` dosyasında `snake_case` olsa da özellik adlarına `PascalCase` uygulandığını unutmayın. [Prototipli Stil Kılavuzu](https://developers.google.com/protocol-buffers/docs/style) , diğer platformlar için kod oluşturmanın, kuralları için beklenen durumu üretmeleri için ileti tanımlarınızda `snake_case` kullanılmasını önerir.

>[!div class="step-by-step"]
>[Önceki](protocol-buffers.md)
>[İleri](protobuf-data-types.md)
