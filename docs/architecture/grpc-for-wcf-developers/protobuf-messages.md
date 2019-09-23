---
title: Prototipsiz iletiler-WCF geliştiricileri için gRPC
description: Daha fazla bilgi için bkz. IDL ve içinde C#oluşturulan prototip.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6bb67fe3bc37fcb49c0e69b7960a00d584307b8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184206"
---
# <a name="protobuf-messages"></a>Prototip iletileri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, `.proto` dosyalardaki prototip iletilerin nasıl bildirildiği, alan numaralarının ve türlerin temel kavramları açıklanmakta ve C# `protoc` derleyici tarafından oluşturulan koda bakar. Bölümün geri kalanı, farklı veri türlerinin prototipte nasıl temsil edildiği konusunda daha ayrıntılı bilgi sağlayacaktır.

## <a name="declaring-a-message"></a>İleti bildirme

WCF 'de, hisse `Stock` senedi Market Ticari uygulaması için bir sınıf aşağıdaki örnekte olduğu gibi tanımlanabilir:

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

Protoarabelleğe denk sınıfı uygulamak için, `.proto` dosyada bildirilmelidir. `protoc` Derleyici daha sonra yapı sürecinin bir parçası olarak .NET sınıfını oluşturur.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string displayName = 3;
    int32 marketId = 4;

}  
```

İlk satır, kullanılmakta olan sözdizimi sürümünü bildirir. Dilin sürüm 3 2016 ' de yayımlanmıştır ve gRPC Hizmetleri için önerilen sürümdür.

Satır, oluşturulan C# türler için kullanılacak ad alanını belirtir. `option csharp_namespace` Bu seçenek, `.proto` dosya diğer diller için derlendiğinde yok sayılır. Prototip dosyalarının birkaç dilde dile özgü seçenekleri içermesi yaygındır.

`Stock` İleti tanımı, her biri türü, adı ve alan numarası olan dört alanı belirtir.

## <a name="field-numbers"></a>Alan numaraları

Alan numaraları, prototipin önemli bir parçasıdır. Bunlar, ikili kodlu verilerdeki alanları tanımlamak için kullanılır. Bu, sürümden hizmetinizin sürümüne değiştiremeyeceği anlamına gelir. Bunun avantajı, geriye doğru ve ileri uyumluluğun mümkün olmadır. Eksik değer olasılığı işlendiği sürece, istemciler ve hizmetler, hakkında bilgi sahibi olmadıkları alan numaralarını yok sayacaktır.

İkili biçimde, alan numarası bir tür tanımlayıcısıyla birleştirilir. 1 ile 15 arasında alan numaraları, tek bir bayt olarak türlerine göre kodlanabilir; 16 ile 2047 arasında sayılar 2 bayt sürer. Herhangi bir nedenden dolayı bir ileti üzerinde 2047 ' den fazla alana ihtiyacınız varsa daha yüksek bir değere geçebilirsiniz. 1 ile 15 arasındaki alan numaralarının tek baytlık tanımlayıcıları daha iyi performans sağlar, bu nedenle bunları en temel, sık kullanılan alanlar için kullanmanız gerekir.

## <a name="types"></a>Türler

Tür bildirimleri, [sonraki bölümde](protobuf-data-types.md)daha ayrıntılı bir şekilde ele alınan Prototiparabelleği yerel skaler veri türlerini kullanıyor. Bu bölümün geri kalanı, prototipin yerleşik türlerini kapsayacak ve bunların ortak .NET türleriyle ilişkisini göstermeyecektir.

> [!NOTE]
> Prototip yerel olarak bir `decimal` tür desteklemez, bu nedenle bunun yerine Double kullanılır. Tam ondalık duyarlık gerektiren uygulamalar için, bu bölümün sonraki bölümünde yer [alan Ondalıklar bölümüne](protobuf-data-types.md#decimals) bakın.

## <a name="the-generated-code"></a>Oluşturulan kod

Uygulamanızı yapılandırdığınızda, Prototipsiz iletilerinizin her biri için sınıflar oluşturur ve yerel türlerini C# türlerle eşleştireşlenir. Oluşturulan `Stock` tür aşağıdaki imzaya sahip olacaktır:

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

Prototip derleyicinin, `PascalCase` `.proto` dosyada olsa da `camelCase` özellik adlarına uygulandığını unutmayın. Diğer platformlar için kod oluşturmanın `camelCase` , kuralları için beklenen durumu üretmeleri için ileti tanımında kullanılması en iyisidir.

>[!div class="step-by-step"]
>[Önceki](protocol-buffers.md)
>[İleri](protobuf-data-types.md)
