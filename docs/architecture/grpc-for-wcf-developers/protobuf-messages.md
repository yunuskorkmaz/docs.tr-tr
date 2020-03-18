---
title: Protobuf mesajları - WCF geliştiricileri için gRPC
description: Protobuf iletilerinin IDL'de nasıl tanımlandığını ve C#'da nasıl oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147990"
---
# <a name="protobuf-messages"></a>Protobuf iletileri

Bu bölümde, dosyalarda `.proto` Protokol Arabelleği (Protobuf) iletilerinin nasıl beyan edilebildiğini kapsar. Alan sayıları ve türlerinin temel kavramlarını açıklar ve `protoc` derleyicinin oluşturduğu C# koduna bakar.

Bölümün geri kalanı, Farklı veri türlerinin Protobuf'ta nasıl temsil edildiğine daha ayrıntılı olarak bakacaktır.

## <a name="declaring-a-message"></a>İleti bildirme

Windows Communication Foundation'da (WCF) bir borsa işlem uygulaması `Stock` sınıfı aşağıdaki örnek gibi tanımlanabilir:

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

Protobuf'ta eşdeğer sınıfı uygulamak için dosyada `.proto` beyan etmeniz gerekir. Derleyici `protoc` daha sonra yapı işleminin bir parçası olarak .NET sınıfını oluşturur.

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

İlk satır, kullanılan sözdizimi sürümünü bildirir. Dilin 3 sürümü 2016 yılında piyasaya sürüldü. GRPC hizmetleri için önerdiğimiz sürümdür.

Satır, `option csharp_namespace` oluşturulan C# türleri için kullanılacak ad alanını belirtir. `.proto` Dosya diğer diller için derlendiğinde bu seçenek yoksayılır. Protobuf dosyaları genellikle birkaç dil için dile özgü seçenekler içerir.

İleti `Stock` tanımı dört alan belirtir. Her birinin bir türü, adı ve bir alan numarası vardır.

## <a name="field-numbers"></a>Alan numaraları

Alan numaraları Protobuf önemli bir parçasıdır. İkili kodlanmış verilerdeki alanları tanımlamak için kullanılırlar, bu da hizmetin sürümünden sürümüne değiştirilemeyecekleri anlamına gelir. Avantajı geriye dönük uyumluluk ve ileri uyumluluk mümkün olmasıdır. İstemciler ve hizmetler, eksik değerler olasılığı işlendiği sürece, bilmedikleri alan numaralarını yok sayacaktır.

İkili biçimde, alan numarası bir tür tanımlayıcısı ile birleştirilir. 1'den 15'e kadar alan numaraları, tek bir bayt olarak kendi türüyle kodlanabilir. 16 ile 2,047 arası sayılar 2 bayt alır. Herhangi bir nedenle bir iletide 2.047'den fazla alana ihtiyacınız varsa daha yükseğe çıkabilirsiniz. 1 ile 15 arasında alan numaraları için tek bayt tanımlayıcıları daha iyi performans sunar, bu nedenle bunları en temel, en sık kullanılan alanlar için kullanmalısınız.

## <a name="types"></a>Türler

Tür bildirimleri, [bir sonraki bölümde](protobuf-data-types.md)daha ayrıntılı olarak tartışılan Protobuf'un yerel skaler veri türlerini kullanıyor. Bu bölümün geri kalanı Protobuf'un yerleşik türlerini kapsayacak ve bunların ortak .NET türleri ile nasıl ilişkili olduğunu gösterir.

> [!NOTE]
> Protobuf yerel olarak bir `decimal` türü desteklemez, bu nedenle `double` bunun yerine kullanılır. Tam ondalık kesinlik gerektiren uygulamalar için, bu bölümün bir sonraki bölümünde [ondalık sayılar bölümüne](protobuf-data-types.md#decimals) bakın.

## <a name="the-generated-code"></a>Oluşturulan kod

Uygulamanızı oluşturduğunuzda, Protobuf iletilerinizin her biri için sınıflar oluşturur ve yerel türlerini C# türleri ile eşler. Oluşturulan `Stock` tür aşağıdaki imzaya sahip olacaktır:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Oluşturulan gerçek kod bundan çok daha karmaşıktır. Bunun nedeni, her sınıfın kendisini ikili tel biçimine seri hale getirmek ve deserialize etmek için gereken tüm kodu içermesidir.

### <a name="property-names"></a>Özellik adları

Protobuf derleyicisinin dosyada olmalarına `PascalCase` `snake_case` rağmen özellik adlarına uygulandığını `.proto` unutmayın. [Protobuf stil kılavuzu,](https://developers.google.com/protocol-buffers/docs/style) `snake_case` diğer platformlar için kod oluşturmanın kendi kuralları için beklenen örneği üretecek şekilde ileti tanımlarınızda kullanılmasını önerir.

>[!div class="step-by-step"]
>[Önceki](protocol-buffers.md)
>[Sonraki](protobuf-data-types.md)
