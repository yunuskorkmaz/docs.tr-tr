---
title: Sözleşme ilk iş akışı hizmet geliştirme
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: c326f91bc8673180db755a91ab080bcf0ba72052
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721794"
---
# <a name="contract-first-workflow-service-development"></a>Sözleşme ilk iş akışı hizmet geliştirme
İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Workflow Foundation (WF) özelliklerini daha iyi bir web hizmetleri ve iş akışları sözleşme öncelikli iş akışı geliştirme biçiminde arasında tümleştirme. Sözleşme öncelikli iş akışı geliştirme aracı, kod sözleşmede ilk tasarlamak sağlar. Araç ardından otomatik olarak bir etkinlik şablonu sözleşme işlemleri için araç kutusunda oluşturur. Bu konu nasıl etkinlikleri ve bir iş akışı hizmeti özelliklerinde harita hizmet sözleşme öznitelikleri için genel bir bakış sağlar. Bir sözleşme öncelikli iş akışı hizmeti oluşturma adım adım örnek için bkz. [nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [Hizmet sözleşme öznitelikleri için iş akışı öznitelikleri eşleme](contract-first-workflow-service-development.md#MappingAttributes)  
  
    -   [Hizmet sözleşme öznitelikleri](contract-first-workflow-service-development.md#ServiceContract)  
  
    -   [İşlem sözleşme öznitelikleri](contract-first-workflow-service-development.md#OperationContract)  
  
    -   [İleti sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#MessageContract)  
  
    -   [Veri sözleşme öznitelikleri](contract-first-workflow-service-development.md#DataContract)  
  
    -   [Hata sözleşme öznitelikleri](contract-first-workflow-service-development.md#FaultContract)  
  
-   [Ek destek ve uygulama bilgileri](contract-first-workflow-service-development.md#AdditionalSupport)  
  
    -   [Desteklenmeyen hizmet sözleşme özellikleri](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    -   [Yapılandırılmış Mesajlaşma etkinlik oluşturma](contract-first-workflow-service-development.md#ActivityGeneration)  
  
## <a name="MappingAttributes"></a> Hizmet sözleşme öznitelikleri için iş akışı öznitelikleri eşleme  
 Aşağıdaki bölümlerde tablolarda farklı WCF belirtin öznitelikler ve özellikler ve mesajlaşma etkinlikleri ve sözleşme öncelikli iş akışı özellikleri için nasıl eşlendiğini.  
  
-   [Hizmet sözleşme öznitelikleri](contract-first-workflow-service-development.md#ServiceContract)  
  
-   [İşlem sözleşme öznitelikleri](contract-first-workflow-service-development.md#OperationContract)  
  
-   [İleti sözleşmesi öznitelikleri](contract-first-workflow-service-development.md#MessageContract)  
  
-   [Veri sözleşme öznitelikleri](contract-first-workflow-service-development.md#DataContract)  
  
-   [Hata sözleşme öznitelikleri](contract-first-workflow-service-development.md#FaultContract)  
  
### <a name="ServiceContract"></a> Hizmet sözleşme öznitelikleri  
  
|Özellik Adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|Hayır|Alır veya sözleşme çift yönlü sözleşme olduğunda geri çağırma anlaşması türünü ayarlar.|(YOK)|  
|ConfigurationName|Hayır|Alır veya bir uygulama yapılandırma dosyasında hizmetin bulmak için kullanılan adını ayarlar.|(YOK)|  
|HasProtectionLevel|Evet|Üye bir koruma düzeyi atanmış olup olmadığını belirten bir değer alır.|Receive.ProtectionLevel null olmamalıdır.|  
|Ad|Evet|İçin adını alır veya ayarlar \<portType > öğesi Web Hizmetleri Açıklama Dili (WSDL).|Receive.ServiceContractName.LocalName eşleşmesi gerekir.|  
|Ad Alanı|Evet|Alır veya ayarlar ad alanı \<portType > öğesi Web Hizmetleri Açıklama Dili (WSDL).|Receive.ServiceContractName.NameSpace eşleşmelidir|  
|protectionLevel|Evet|Anlaşma için bağlama ProtectionLevel özelliğini değerini desteklemelidir belirtir.|Receive.ProtectionLevel eşleşmesi gerekir.|  
|Sessionmode'u|Hayır|Alır veya ayarlar oturumları izin verilen, izin verilen gerekli veya yok.|(YOK)|  
|typeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Devralınmış. özniteliği.)|(YOK)|  
  
 Gövde alt bölümünü buraya ekleyin.  
  
### <a name="OperationContract"></a> İşlem sözleşme öznitelikleri  
  
|Özellik Adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|Eylem|Evet|Eylemi alır veya WS-Addressing istek iletisinin ayarlar.|Receive.Action eşleşmesi gerekir.|  
|AsyncPattern|Hayır|Bir işlem zaman uyumsuz olarak başlangıç kullanarak uygulandığını belirtir\<methodName > ve bitiş\<methodName > Hizmet sözleşmesinde yöntemi çifti.|(YOK)|  
|HasProtectionLevel|Evet|Bu işlem için iletileri, imzalı şifrelemenin gerekip gerekmediğini belirten bir değer veya her ikisini de alır.|Receive.ProtectionLevel null olmamalıdır.|  
|IsInitiating|Hayır|Alır veya yöntemini (böyle bir oturum varsa), sunucu üzerindeki bir oturum başlatabilirsiniz bir işlemi uygulayan olup olmadığını gösteren bir değer ayarlar.|(YOK)|  
|IsOneWay|Evet|Alır veya bir işlem bir yanıt iletisi döndürüp döndürmeyeceğini belirten bir değer ayarlar.|(Bunun için hiçbir SendReply almak veya hiçbir ReceiveReply bu göndermek için).|  
|IsTerminating|Hayır|Alır veya ayarlar, gönderilir, hizmet işlemi yanıt iletisi sonra oturumu kapatmak sunucunun neden olup olmayacağını belirten bir değer.|(YOK)|  
|Ad|Evet|Alır veya ayarlar olan işlemin adı.|Receive.OperationName eşleşmesi gerekir.|  
|protectionLevel|Evet|Alır veya bir işlem iletileri, imzalı şifrelemenin gerekip gerekmediğini belirten bir değer veya her ikisini de ayarlar.|Receive.ProtectionLevel eşleşmesi gerekir.|  
|ReplyAction|Evet|Alır veya SOAP eylemi için yanıt iletisi işlemin değerini ayarlar.|SendReply.Action eşleşmesi gerekir.|  
|typeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Devralınmış. özniteliği.)|(YOK)|  
  
### <a name="MessageContract"></a> İleti sözleşmesi öznitelikleri  
  
|Özellik Adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Evet|İleti bir koruma düzeyi olup olmadığını belirten bir değer alır.|Doğrulama (Receive.Content ve SendReply.Content ileti sözleşme türüyle eşleşmelidir).|  
|IsWrapped|Evet|Alır veya ileti gövdesi bir sarmalayıcı öğe olup olmadığını belirten bir değeri ayarlar.|Doğrulama (Receive.Content ve Sendreply.Content ileti sözleşme türüyle eşleşmelidir).|  
|protectionLevel|Hayır|Alır veya ileti, imzalı şifrelemenin gerekip gerekmediğini belirtilen bir değer veya her ikisini de ayarlar.|(YOK)|  
|typeId|Evet|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Devralınmış. özniteliği.)|Doğrulama (Receive.Content ve SendReply.Content ileti sözleşme türüyle eşleşmelidir).|  
|WrapperName|Evet|Alır veya ayarlar ileti gövdesinin sarmalayıcı öğe adı.|Doğrulama (Receive.Content ve SendReply.Content ileti sözleşme türüyle eşleşmelidir).|  
|WrapperNamespace|Hayır|Alır veya ayarlar ileti gövdesi sarmalayıcı öğe ad alanı.|(YOK)|  
  
### <a name="DataContract"></a> Veri sözleşme öznitelikleri  
  
|Özellik Adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|IsReference|Hayır|Alır veya nesne başvuru verilerini korumak etkinleştirilip etkinleştirilmeyeceğini gösteren bir değer ayarlar.|(YOK)|  
|Ad|Evet|Alır veya türü için veri anlaşması adını ayarlar.|Doğrulama (Receive.Content ve SendReply.Content ileti sözleşme türüyle eşleşmelidir).|  
|Ad Alanı|Evet|Türünü alır veya veri anlaşması ad alanı için ayarlar.|Doğrulama (Receive.Content ve SendReply.Content ileti sözleşme türüyle eşleşmelidir).|  
|typeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Devralınmış. özniteliği.)|(YOK)|  
  
### <a name="FaultContract"></a> Hata sözleşme öznitelikleri  
  
|Özellik Adı|Desteklenir|Açıklama|WF doğrulama|  
|-------------------|---------------|-----------------|-------------------|  
|Eylem|Evet|Alır veya ayarlar da işlem anlaşması bir parçası olarak belirtilen SOAP hata iletisinin eylem.|SendReply.Action eşleşmesi gerekir.|  
|DetailType|Evet|Hata bilgilerini içeren bir seri hale getirilebilir bir nesne türünü alır.|SendReply.Content eşleşmelidir|  
|HasProtectionLevel|Hayır|SOAP hata iletisi bir koruma düzeyi atanmış olup olmadığını belirten bir değer alır.|(YOK)|  
|Ad|Hayır|Alır veya Web Hizmetleri Açıklama Dili (WSDL) hata iletisi adını ayarlar.|(YOK)|  
|Ad Alanı|Hayır|Alır veya ayarlar bir SOAP hatası ad alanı.|(YOK)|  
|protectionLevel|Hayır|Bir SOAP hatası bağlamayı gerektirir koruma düzeyini belirtir.|(YOK)|  
|typeId|Hayır|Türetilen bir sınıfta uygulandığında, bu öznitelik için benzersiz bir tanımlayıcı alır. (Devralınmış. özniteliği.)|(YOK)|  
  
## <a name="AdditionalSupport"></a> Ek destek ve uygulama bilgileri  
  
-   [Desteklenmeyen hizmet sözleşme özellikleri](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
-   [Yapılandırılmış Mesajlaşma etkinlik oluşturma](contract-first-workflow-service-development.md#ActivityGeneration)  
  
### <a name="UnsupportedFeatures"></a> Desteklenmeyen hizmet sözleşme özellikleri  
  
-   Sözleşmelerinde TPL (görev paralel kitaplığı) görevlerin kullanımı desteklenmiyor.  
  
-   Hizmet sözleşmelerinde devralma desteklenmiyor.  
  
### <a name="ActivityGeneration"></a> Yapılandırılmış Mesajlaşma etkinlik oluşturma  
 İki ortak statik yöntemler eklenir <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> oluşturulmasını desteklemek için etkinlikleri sözleşme öncelikli iş akışı hizmetlerini kullanırken İleti etkinlikleri önceden yapılandırılmış.  
  
-   <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 Bu yöntemler tarafından oluşturulan bir etkinlik sözleşme doğrulamasını geçmesi ve bu nedenle bu yöntemler için doğrulama mantığını bir parçası olarak dahili olarak kullanılan <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>, Ve <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> içeri aktarılan Sözleşmesi ile eşleşmesi için tüm önceden yapılandırılmış. İş Akışı Tasarımcısı'nda etkinlikler için içerik özellikleri sayfasında **ileti** veya **parametreleri** bölümleri Sözleşmesi ile eşleşmesi için önceden yapılandırılmış de.  
  
 WCF hata sözleşmeleri, ayrı bir dizi döndüren ve ayrıca işlenir yapılandırılmış <xref:System.ServiceModel.Activities.SendReply> her gösterilmesi hatalarının etkinlikleri <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 Diğer bölümleri için <xref:System.ServiceModel.Description.OperationDescription> WF Hizmetleri tarafından bugün (örneğin WebGet/Webınvoke davranışları veya özel işlem davranışları) desteklenmeyen, API oluşturma ve yapılandırma bir parçası olarak bu değerleri yoksayılır. Hiçbir özel durum oluşturulur.
