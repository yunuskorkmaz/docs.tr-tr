---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918672"
---
# <a name="transactedbatching"></a>\<Transactedtoplu işlem >

İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.

\<sistemin. ServiceModel > \
\<davranışlar > \
\<Endpointdavranışlar > \
\<davranış > \
\<Transactedtoplu işlem >

## <a name="syntax"></a>Sözdizimi

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`maxBatchSize`|Tek bir işlemde birlikte toplu olarak oluşturulabilecek en fazla alma işlemi sayısını belirten bir tamsayı. Varsayılan değer 0 ' dır.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|

## <a name="remarks"></a>Açıklamalar

İşlem toplu işlemi ile yapılandırılan bir aktarım, birkaç alma işlemini tek bir işlemde toplu olarak dener. Bu şekilde, bir işlem oluşturmanın ve her alma işleminde gerçekleştiren görece yüksek maliyetli bir işlemdir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma dosyasındaki bir hizmete işlenen toplu işlem davranışının nasıl ekleneceğini gösterir.

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
