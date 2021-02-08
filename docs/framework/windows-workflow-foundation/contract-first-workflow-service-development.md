---
description: 'Daha fazla bilgi: anlaşma Ilk Iş akışı hizmeti geliştirme'
title: İlk İş Akışı Hizmet Geliştirme Anlaşmasını Yapma
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 54f6c0c5de45187bd65e45d22978e6e9b105f3e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792719"
---
# <a name="contract-first-workflow-service-development"></a>İlk İş Akışı Hizmet Geliştirme Anlaşmasını Yapma

.NET Framework 4,5 ' den başlayarak, Windows Workflow Foundation (WF), sözleşme ilk iş akışı geliştirme biçiminde Web Hizmetleri ve iş akışları arasında daha iyi tümleştirme sunar. Sözleşme-ilk iş akışı geliştirme aracı, sözleşmeyi önce kod içinde tasarlamanızı sağlar. Araç daha sonra, sözleşmede bulunan işlemler için araç kutusunda bir etkinlik şablonu otomatik olarak oluşturur. Bu konuda, bir iş akışı hizmetindeki etkinliklerin ve özelliklerin bir hizmet sözleşmesinin öznitelikleriyle nasıl eşleneceğini gösteren bir genel bakış sunulmaktadır. Bir sözleşmenin ilk iş akışı hizmeti oluşturmaya yönelik adım adım bir örnek için bkz. [nasıl yapılır: mevcut bir hizmet sözleşmesini tüketen iş akışı hizmeti oluşturma](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).

## <a name="in-this-topic"></a>Bu konuda

- [Hizmet sözleşmesi özniteliklerini iş akışı öznitelikleriyle eşleme](contract-first-workflow-service-development.md#MappingAttributes)

  - [Hizmet sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#ServiceContract)

  - [İşlem sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#OperationContract)

  - [İleti sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#MessageContract)

  - [Veri sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#DataContract)

  - [Hata sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#FaultContract)

- [Ek destek ve uygulama bilgileri](contract-first-workflow-service-development.md#AdditionalSupport)

  - [Desteklenmeyen hizmet sözleşmesi özellikleri](contract-first-workflow-service-development.md#UnsupportedFeatures)

  - [Yapılandırılmış mesajlaşma etkinlikleri oluşturma](contract-first-workflow-service-development.md#ActivityGeneration)

## <a name="mapping-service-contract-attributes-to-workflow-attributes"></a><a name="MappingAttributes"></a> Hizmet sözleşmesi özniteliklerini iş akışı öznitelikleriyle eşleme

Aşağıdaki bölümlerde bulunan tablolar, farklı WCF özniteliklerini ve özelliklerini ve bunların bir sözleşmenin ilk iş akışındaki mesajlaşma etkinliklerine ve özelliklerine nasıl eşlenildiğini belirtir.

- [Hizmet sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#ServiceContract)

- [İşlem sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#OperationContract)

- [İleti sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#MessageContract)

- [Veri sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#DataContract)

- [Hata sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#FaultContract)

### <a name="service-contract-attributes"></a><a name="ServiceContract"></a> Hizmet sözleşmesi öznitelikleri

|Özellik Adı|Desteklenir|Description|WF doğrulaması|
|-------------------|---------------|-----------------|-------------------|
|CallbackContract|No|Anlaşma bir çift yönlü sözleşmeden geri arama sözleşmesinin türünü alır veya ayarlar.|(yok)|
|ConfigurationName|No|Hizmeti bir uygulama yapılandırma dosyasında bulmak için kullanılan adı alır veya ayarlar.|(yok)|
|HasProtectionLevel|Yes|Üyenin bir koruma düzeyi atanmış olup olmadığını gösteren bir değer alır.|Receive. ProtectionLevel null olmamalıdır.|
|Name|Yes|\<portType>Web Hizmetleri Açıklama Dili (wsdl) içindeki öğenin adını alır veya ayarlar.|Receive. ServiceContractName. LocalName eşleşmelidir.|
|Ad Alanı|Yes|\<portType>Web Hizmetleri Açıklama Dili (wsdl) içindeki öğenin ad alanını alır veya ayarlar.|Receive. ServiceContractName. NameSpace eşleşmelidir|
|ProtectionLevel|Yes|Sözleşme bağlamasının ProtectionLevel özelliğinin değerini desteklemesi gerekip gerekmediğini belirtir.|Receive. ProtectionLevel eşleşmelidir.|
|SessionMode|No|Oturumlara izin verildiğini, izin verilmediğini veya gerekli olup olmadığını alır veya ayarlar.|(yok)|
|Türü|No|Türetilmiş bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelikten devralındı.)|(yok)|

Gövde alt bölümünü buraya ekleyin.

### <a name="operation-contract-attributes"></a><a name="OperationContract"></a> İşlem sözleşmesi öznitelikleri

|Özellik Adı|Desteklenir|Description|WF doğrulaması|
|-------------------|---------------|-----------------|-------------------|
|Eylem|Yes|İstek iletisinin WS-Addressing eylemini alır veya ayarlar.|Receive. Action eşleşmelidir.|
|Metodundaki AsyncPattern|No|Bir işlemin, bir \<methodName> hizmet sözleşmesinde BEGIN ve End yöntem çiftinin kullanıldığı zaman uyumsuz olarak uygulandığını belirtir \<methodName> .|(yok)|
|HasProtectionLevel|Yes|Bu işlem için iletilerin şifrelenip şifrelenmeyeceğini, imzalanacağını veya her ikisini de gösteren bir değer alır.|Receive. ProtectionLevel null olmamalıdır.|
|IsInitiating|No|Yöntemin sunucuda oturum başlatabilen bir işlem uygulayıp uygulamadığını belirten bir değer alır veya ayarlar (böyle bir oturum varsa).|(yok)|
|IsOneWay|Yes|Bir işlemin yanıt iletisi döndürüp döndürmediğini gösteren bir değer alır veya ayarlar.|(Bu alma için SendReply yok veya bu gönderme için bir ReceiveReply yok).|
|IsTerminating|No|Varsa, yanıt iletisi gönderildiğinde, hizmet işleminin oturumu kapatmasına neden olup olmadığını gösteren bir değer alır veya ayarlar.|(yok)|
|Name|Yes|İşlemin adını alır veya ayarlar.|Receive. OperationName eşleşmelidir.|
|ProtectionLevel|Yes|Bir işlem iletilerinin şifrelenip şifrelenmeyeceğini, imzalanacağını veya her ikisini de belirler.|Receive. ProtectionLevel eşleşmelidir.|
|ReplyAction|Yes|İşlemin yanıt iletisi için SOAP eyleminin değerini alır veya ayarlar.|SendReply. Action eşleşmelidir.|
|Türü|No|Türetilmiş bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelikten devralındı.)|(yok)|

### <a name="message-contract-attributes"></a><a name="MessageContract"></a> İleti sözleşmesi öznitelikleri

|Özellik Adı|Desteklenir|Description|WF doğrulaması|
|-------------------|---------------|-----------------|-------------------|
|HasProtectionLevel|Yes|İletinin koruma düzeyine sahip olup olmadığını gösteren bir değer alır.|Doğrulama yok (Receive. Content ve SendReply. Content, ileti sözleşmesi türüyle eşleşmelidir).|
|IsWrapped|Yes|İleti gövdesinin sarmalayıcı öğesine sahip olup olmadığını belirten bir değer alır veya ayarlar.|Doğrulama yok (Receive. Content ve SendReply. Content, ileti sözleşmesi türüyle eşleşmelidir).|
|ProtectionLevel|No|İletinin şifrelenmesi, imzalanması veya her ikisinin de olması gerekip gerekmediğini belirten bir değer alır veya ayarlar.|(yok)|
|Türü|Yes|Türetilmiş bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelikten devralındı.)|Doğrulama yok (Receive. Content ve SendReply. Content, ileti sözleşmesi türüyle eşleşmelidir).|
|WrapperName|Yes|İleti gövdesinin sarmalayıcı öğesinin adını alır veya ayarlar.|Doğrulama yok (Receive. Content ve SendReply. Content, ileti sözleşmesi türüyle eşleşmelidir).|
|WrapperNamespace|No|İleti gövdesi sarmalayıcı öğesinin ad alanını alır veya ayarlar.|(yok)|

### <a name="data-contract-attributes"></a><a name="DataContract"></a> Veri sözleşmesi öznitelikleri

|Özellik Adı|Desteklenir|Description|WF doğrulaması|
|-------------------|---------------|-----------------|-------------------|
|IsReference|No|Nesne başvuru verilerinin korunup korunmayacağını gösteren bir değer alır veya ayarlar.|(yok)|
|Name|Yes|Tür için veri sözleşmesinin adını alır veya ayarlar.|Doğrulama yok (Receive. Content ve SendReply. Content, ileti sözleşmesi türüyle eşleşmelidir).|
|Ad Alanı|Yes|Tür için veri sözleşmesinin ad alanını alır veya ayarlar.|Doğrulama yok (Receive. Content ve SendReply. Content, ileti sözleşmesi türüyle eşleşmelidir).|
|Türü|No|Türetilmiş bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelikten devralındı.)|(yok)|

### <a name="fault-contract-attributes"></a><a name="FaultContract"></a> Hata sözleşmesi öznitelikleri

|Özellik Adı|Desteklenir|Description|WF doğrulaması|
|-------------------|---------------|-----------------|-------------------|
|Eylem|Yes|İşlem sözleşmesinin bir parçası olarak belirtilen SOAP hata iletisi eylemini alır veya ayarlar.|SendReply. Action eşleşmelidir.|
|Ayrıntı türü|Yes|Hata bilgilerini içeren bir serileştirilebilir nesnenin türünü alır.|SendReply. Content, türle eşleşmelidir|
|HasProtectionLevel|No|SOAP hata iletisinin atanmış bir koruma düzeyi olup olmadığını gösteren bir değer alır.|(yok)|
|Name|No|Web Hizmetleri Açıklama Dili (WSDL) içindeki hata iletisinin adını alır veya ayarlar.|(yok)|
|Ad Alanı|No|SOAP hatasının ad alanını alır veya ayarlar.|(yok)|
|ProtectionLevel|No|SOAP hatasının, bağlamadan gerektirdiği koruma düzeyini belirtir.|(yok)|
|Türü|No|Türetilmiş bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelikten devralındı.)|(yok)|

## <a name="additional-support-and-implementation-information"></a><a name="AdditionalSupport"></a> Ek destek ve uygulama bilgileri

- [Desteklenmeyen hizmet sözleşmesi özellikleri](contract-first-workflow-service-development.md#UnsupportedFeatures)

- [Yapılandırılmış mesajlaşma etkinlikleri oluşturma](contract-first-workflow-service-development.md#ActivityGeneration)

### <a name="unsupported-service-contract-features"></a><a name="UnsupportedFeatures"></a> Desteklenmeyen hizmet sözleşmesi özellikleri

- Sözleşmelerdeki TPL (görev paralel kitaplığı) görevlerinin kullanımı desteklenmiyor.

- Hizmet sözleşmelerinde devralma desteklenmez.

### <a name="generation-of-configured-messaging-activities"></a><a name="ActivityGeneration"></a> Yapılandırılmış mesajlaşma etkinlikleri oluşturma

<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Sözleşme ilk iş akışı Hizmetleri kullanılırken önceden yapılandırılmış ileti etkinliklerinin oluşturulmasını desteklemek için ve etkinliklerine iki ortak statik yöntem eklenir.

- <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>

- <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>

Bu yöntemler tarafından oluşturulan etkinliğin sözleşme doğrulamasını geçmesi gerekir ve bu nedenle bu yöntemler, ve için doğrulama mantığının bir parçası olarak dahili olarak kullanılır <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . ,,,, <xref:System.ServiceModel.Activities.Receive.OperationName%2A>  <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> Ve,  <xref:System.ServiceModel.Activities.Receive.Action%2A>  <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>  <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> içeri aktarılan sözleşmeyle eşleşecek şekilde önceden yapılandırılmıştır. Workflow Designer 'daki etkinliklerin içerik özellikleri sayfasında, **ileti** veya **Parametreler** bölümleri de sözleşmeyle eşleşecek şekilde önceden yapılandırılmıştır.

WCF hata sözleşmeleri <xref:System.ServiceModel.Activities.SendReply> , içinde görüntülenen hataların her biri için ayrı bir yapılandırılmış etkinlik kümesi döndürerek da işlenir <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection> .

<xref:System.ServiceModel.Description.OperationDescription>Günümüzde WF hizmetleri tarafından desteklenmeyen diğer bölümler için (ör. WebGet/Webvoke davranışları veya özel işlem davranışları), API, oluşturma ve yapılandırmanın bir parçası olarak bu değerleri yoksayar. Hiçbir özel durum oluşturulmaz.
