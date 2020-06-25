---
title: Prototipsiz iletiler-WCF geliştiricileri için gRPC
description: Prototipme iletilerinin IDL 'de nasıl tanımlandığını ve C# dilinde oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 6fc7b9c34810abaa8d674af56d1517a5cf87521b
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325043"
---
# <a name="protobuf-messages"></a>Protobuf iletileri

Bu bölümde, dosyalardaki protokol arabelleği (Protoarabelleği) iletilerinin nasıl bildirildiği ele alınmaktadır `.proto` . Alan numaralarının ve türlerinin temel kavramlarını açıklar ve derleyicinin oluşturduğu C# koduna bakar `protoc` .

Bölümün geri kalanı, farklı veri türlerinin prototipte nasıl temsil edildiği konusunda daha ayrıntılı bilgi sağlayacaktır.

## <a name="declaring-a-message"></a>İleti bildirme

Windows Communication Foundation (WCF) ' de, `Stock` hisse senedi Market Ticari uygulaması için bir sınıf aşağıdaki örnekte olduğu gibi tanımlanabilir:

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

Protoarabelleğe denk sınıfı uygulamak için, `.proto` dosyayı dosyada bildirmeniz gerekir. `protoc`Derleyici daha sonra yapı sürecinin bir parçası olarak .NET sınıfını oluşturur.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

İlk satır, kullanılmakta olan sözdizimi sürümünü bildirir. Dilin sürüm 3 2016 ' de yayımlanmıştır. Bu, gRPC Hizmetleri için önerdiğimiz sürümdür.

`option csharp_namespace`Satır, oluşturulan C# türleri için kullanılacak ad alanını belirtir. Bu seçenek, `.proto` dosya diğer diller için derlendiğinde yok sayılır. Prototip dosyaları genellikle birkaç dil için dile özgü seçenekler içerir.

`Stock`İleti tanımı dört alanı belirtir. Her birinin bir türü, adı ve alan numarası vardır.

## <a name="field-numbers"></a>Alan numaraları

Alan numaraları, prototipin önemli bir parçasıdır. Bunlar, ikili kodlu verilerdeki alanları tanımlamak için kullanılır. Bu, sürümden hizmetinizin sürümüne değiştiremeyeceği anlamına gelir. Bunun avantajı, geriye dönük uyumluluk ve ileriye doğru uyumluluk olanaklarından yararlanabilmektir. Eksik değer olasılığı işlendiği sürece, istemciler ve hizmetler, hakkında bilgi sahibi olmadıkları alan numaralarını yok sayacaktır.

İkili biçimde, alan numarası bir tür tanımlayıcısıyla birleştirilir. 1 ile 15 arasında alan numaraları, tek bir bayt olarak türlerine göre kodlanabilir. 16 ile 2.047 arasında sayılar 2 bayt sürer. Herhangi bir nedenden dolayı bir ileti üzerinde 2.047 ' den fazla alana ihtiyacınız varsa daha yüksek bir değere geçebilirsiniz. 1 ile 15 arasındaki alan numaralarının tek baytlık tanımlayıcıları daha iyi performans sağlar, bu nedenle bunları en temel, sık kullanılan alanlar için kullanmanız gerekir.

## <a name="types"></a>Türler

Tür bildirimleri, [sonraki bölümde](protobuf-data-types.md)daha ayrıntılı bir şekilde ele alınan Prototiparabelleği yerel skaler veri türlerini kullanıyor. Bu bölümün geri kalanı, prototipin yerleşik türlerini kapsayacak ve bunların ortak .NET türleriyle ilişkisini göstermeyecektir.

> [!NOTE]
> Prototip `decimal` , bir türü yerel olarak desteklemez, `double` bunun yerine kullanılır. Tam ondalık duyarlık gerektiren uygulamalar için, bu bölümün sonraki bölümünde yer [alan Ondalıklar bölümüne](protobuf-data-types.md#decimals) bakın.

## <a name="the-generated-code"></a>Oluşturulan kod

Uygulamanızı yapılandırdığınızda, Prototipsiz iletilerinizin her biri için sınıflar oluşturur ve yerel türlerini C# türlerine eşleyerek. Oluşturulan `Stock` tür aşağıdaki imzaya sahip olacaktır:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Oluşturulan gerçek kod bundan çok daha karmaşıktır. Bunun nedeni, her bir sınıfın kendisini seri hale getirmek için gereken tüm kodu ve ikili tel biçiminde seri durumdan çıkarmak için gerekli olduğunu içerir.

### <a name="property-names"></a>Özellik adları

Prototip derleyicisinin, `PascalCase` dosyasında olmasına rağmen özellik adlarına uygulandığını unutmayın `snake_case` `.proto` . [Prototipli Stil Kılavuzu](https://developers.google.com/protocol-buffers/docs/style) , `snake_case` diğer platformlar için kod oluşturmanın, kuralları için beklenen durumu üretmeleri için ileti tanımlarınızda kullanılmasını önerir.

>[!div class="step-by-step"]
>[Önceki](protocol-buffers.md) 
> [Sonraki](protobuf-data-types.md)
