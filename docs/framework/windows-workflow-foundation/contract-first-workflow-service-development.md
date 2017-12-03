---
title: "Sözleşme ilk iş akışı hizmeti geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c3d22c83f5fbc1144d139c9e7ba6a43137f6d144
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="contract-first-workflow-service-development"></a>Sözleşme ilk iş akışı hizmeti geliştirme
İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[wf](../../../includes/wf-md.md)] özellikleri daha iyi web hizmetleri ve iş akışları sözleşme ilk iş akışı geliştirme biçiminde arasında tümleştirme. Sözleşme ilk iş akışı geliştirme aracı kod sözleşmede ilk tasarlamanızı sağlar. Araç ardından otomatik olarak bir etkinlik şablonu sözleşmesindeki işlemleri için araç kutusu oluşturur. Bu konu nasıl etkinlikleri ve iş akışı hizmeti özelliklerinde harita hizmet sözleşmesini öznitelikleri için genel bir bakış sağlar. Bir sözleşme ilk iş akışı hizmeti oluşturma adım adım örnek için bkz: [nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [İş akışı özniteliklere hizmeti sözleşme öznitelikleri eşleme](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MappingAttributes)  
  
    -   [Hizmet sözleşmesi öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
    -   [İşlemi sözleşme öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
    -   [İleti sözleşmesi öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
    -   [Veri sözleşmesi öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
    -   [Hataya sözleşme öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
-   [Ek destek ve uygulama bilgileri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#AdditionalSupport)  
  
    -   [Desteklenmeyen hizmet sözleşmesi özellikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    -   [Yapılandırılmış Mesajlaşma etkinlikleri oluşturma](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
##  <a name="MappingAttributes"></a>İş akışı özniteliklere hizmeti sözleşme öznitelikleri eşleme  
 Aşağıdaki bölümlerde tablolarda farklı WCF belirtin öznitelikler ve özellikler ve mesajlaşma etkinlikleri ve sözleşme ilk iş akışı özelliklerinde nasıl eşlenmiş.  
  
-   [Hizmet sözleşmesi öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
-   [İşlemi sözleşme öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
-   [İleti sözleşmesi öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
-   [Veri sözleşmesi öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
-   [Hataya sözleşme öznitelikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
###  <a name="ServiceContract"></a>Hizmet sözleşmesi öznitelikleri  
  
|Özellik adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|Hayır|Alır veya sözleşme çift yönlü sözleşme olduğunda geri çağırma sözleşme türünü ayarlar.|(YOK)|  
|ConfigurationName|Hayır|Alır veya hizmet bir uygulama yapılandırma dosyasında bulmak için kullanılan adını ayarlar.|(YOK)|  
|HasProtectionLevel|Evet|Üye bir koruma düzeyi atanmış olup olmadığını belirten bir değer alır.|Receive.ProtectionLevel null olmamalıdır.|  
|Ad|Evet|İçin adını alır veya ayarlar \<bağlantı noktası türü > öğesi Web Hizmetleri Açıklama Dili (WSDL).|Receive.ServiceContractName.LocalName eşleşmesi gerekir.|  
|Ad Alanı|Evet|Alır veya ayarlar ad alanı \<bağlantı noktası türü > öğesi Web Hizmetleri Açıklama Dili (WSDL).|Receive.ServiceContractName.NameSpace eşleşmelidir|  
|ProtectionLevel|Evet|Sözleşme için bağlama ProtectionLevel özelliğinin değeri destekleyip desteklemediğini belirtir.|Receive.ProtectionLevel eşleşmesi gerekir.|  
|SessionMode|Hayır|Alır veya oturumları izin verilen, izin verilen veya gerekli değil olup olmadığını ayarlar.|(YOK)|  
|TypeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelik devralındı.)|(YOK)|  
  
 Gövde alt bölümünü buraya ekleyin.  
  
###  <a name="OperationContract"></a>İşlemi sözleşme öznitelikleri  
  
|Özellik adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|Eylem|Evet|Eylemi alır veya WS adresleme istek iletisinin ayarlar.|Receive.Action eşleşmesi gerekir.|  
|Başlatıcıda|Hayır|Begin zaman uyumsuz olarak kullanarak bir işlem uygulanır gösterir\<methodName > ve bitiş\<methodName > Hizmet sözleşmesinde yöntemi çifti.|(YOK)|  
|HasProtectionLevel|Evet|Bu işlem için iletileri, imzalı şifrelenmesi gerekip gerekmediğini belirten bir değer veya her ikisini de alır.|Receive.ProtectionLevel null olmamalıdır.|  
|IsInitiating|Hayır|Alır veya yöntemi (böyle bir oturum varsa), sunucu üzerindeki bir oturum başlatabilirsiniz bir işlem uygulayan olup olmadığını belirten bir değer ayarlar.|(YOK)|  
|IsOneWay|Evet|Alır veya bir işlem bir yanıt iletisi döndüren olup olmadığını belirten bir değer ayarlar.|(Bunun için hiçbir SendReply almak veya bu göndermek için hiçbir ReceiveReply).|  
|IsTerminating|Hayır|Alır veya herhangi biri, gönderilir, hizmet işlemi sunucunun yanıt iletisi sonra oturumu kapatmaya neden olup olmayacağını belirten bir değer ayarlar.|(YOK)|  
|Ad|Evet|Alır veya ayarlar işlemin adı.|Receive.OperationName eşleşmesi gerekir.|  
|ProtectionLevel|Evet|Alır veya bir işlem iletileri, imzalı şifrelenmesi gerekip gerekmediğini belirten bir değer veya her ikisini de ayarlar.|Receive.ProtectionLevel eşleşmesi gerekir.|  
|ReplyAction|Evet|Alır veya işlemi yanıt iletisi için SOAP eylemi değerini ayarlar.|SendReply.Action eşleşmesi gerekir.|  
|TypeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelik devralındı.)|(YOK)|  
  
###  <a name="MessageContract"></a>İleti sözleşmesi öznitelikleri  
  
|Özellik adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Evet|İleti bir koruma düzeyi olup olmadığını belirten bir değer alır.|Hiçbir doğrulama (Receive.Content ve SendReply.Content ileti sözleşmesi türüyle eşleşmelidir).|  
|IsWrapped|Evet|Alır veya ileti gövdesi bir kapsayıcı öğe sahip olup olmadığını belirten bir değer ayarlar.|Hiçbir doğrulama (Receive.Content ve Sendreply.Content ileti sözleşmesi türüyle eşleşmelidir).|  
|ProtectionLevel|Hayır|Alır veya ileti, imzalı şifrelenmesi gerekip gerekmediğini belirtilen bir değer veya her ikisini de ayarlar.|(YOK)|  
|TypeId|Evet|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelik devralındı.)|Hiçbir doğrulama (Receive.Content ve SendReply.Content ileti sözleşmesi türüyle eşleşmelidir).|  
|WrapperName|Evet|Alır veya ayarlar ileti gövdesinin sarmalayıcı öğesinin adı.|Hiçbir doğrulama (Receive.Content ve SendReply.Content ileti sözleşmesi türüyle eşleşmelidir).|  
|WrapperNamespace|Hayır|Alır veya ayarlar ileti gövdesi sarmalayıcı öğesinin ad alanı.|(YOK)|  
  
###  <a name="DataContract"></a>Veri sözleşmesi öznitelikleri  
  
|Özellik adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|IsReference|Hayır|Alır veya mi nesne başvuru verileri korumak belirten bir değer ayarlar.|(YOK)|  
|Ad|Evet|Alır veya türü için veri sözleşmesi adını ayarlar.|Hiçbir doğrulama (Receive.Content ve SendReply.Content ileti sözleşmesi türüyle eşleşmelidir).|  
|Ad Alanı|Evet|Türünü alır veya veri sözleşmesi için ad alanı için ayarlar.|Hiçbir doğrulama (Receive.Content ve SendReply.Content ileti sözleşmesi türüyle eşleşmelidir).|  
|TypeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelik devralındı.)|(YOK)|  
  
###  <a name="FaultContract"></a>Hataya sözleşme öznitelikleri  
  
|Özellik adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|Eylem|Evet|Eylemi alır veya işlemi sözleşmesinin bir parçası belirtilen SOAP hata iletisinin ayarlar.|SendReply.Action eşleşmesi gerekir.|  
|DetailType|Evet|Hata bilgilerini içeren serileştirilebilir bir nesne türünü alır.|SendReply.Content türü eşleşmelidir|  
|HasProtectionLevel|Hayır|SOAP hata iletisi bir koruma düzeyi atanmış olup olmadığını belirten bir değer alır.|(YOK)|  
|Ad|Hayır|Adını alır veya hata iletisinin Web Hizmetleri Açıklama Dili (WSDL) ayarlar.|(YOK)|  
|Ad Alanı|Hayır|Alır veya ayarlar bir SOAP hatası ad alanı.|(YOK)|  
|ProtectionLevel|Hayır|Bir SOAP hatası bağlamasını gerektirir koruma düzeyini belirtir.|(YOK)|  
|TypeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Öznitelik devralındı.)|(YOK)|  
  
##  <a name="AdditionalSupport"></a>Ek destek ve uygulama bilgileri  
  
-   [Desteklenmeyen hizmet sözleşmesi özellikleri](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
-   [Yapılandırılmış Mesajlaşma etkinlikleri oluşturma](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
###  <a name="UnsupportedFeatures"></a>Desteklenmeyen hizmet sözleşmesi özellikleri  
  
-   TPL (görev paralel kitaplığı) görevler sözleşmelerinde kullanımı desteklenmiyor.  
  
-   Hizmet sözleşmelerinde devralma desteklenmiyor.  
  
###  <a name="ActivityGeneration"></a>Yapılandırılmış Mesajlaşma etkinlikleri oluşturma  
 İki ortak statik yöntemler eklenir <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> oluşturulmasını desteklemek üzere etkinlikleri sözleşme ilk iş akışı hizmetlerini kullanırken İleti etkinlikleri önceden yapılandırılmış.  
  
-   <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 Bu yöntemler tarafından oluşturulan etkinliğini sözleşme doğrulamasını geçmesi ve bu nedenle bu yöntemleri için doğrulama mantığını bir parçası olarak dahili olarak kullanılan <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>, Ve <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> alınan sözleşme eşleşen tüm önceden yapılandırılmış olan. İş Akışı Tasarımcısı'nda etkinlikler için içerik özellikleri sayfasında **ileti** veya **parametreleri** bölümleri sözleşme eşleşen önceden yapılandırılmış de.  
  
 WCF hata sözleşmeleri, ayrı bir dizi döndürerek ayrıca işlenir yapılandırılmış <xref:System.ServiceModel.Activities.SendReply> etkinlikleri her görünmesini hatalarının <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 Diğer bölümleri için <xref:System.ServiceModel.Description.OperationDescription> WF Hizmetleri tarafından bugün (örneğin WebGet/Webınvoke davranışları veya özel işlemi davranışları) desteklenmeyen, API oluşturma ve yapılandırma bir parçası olarak bu değerleri göz ardı eder. Hiçbir özel durum oluşturulur.
