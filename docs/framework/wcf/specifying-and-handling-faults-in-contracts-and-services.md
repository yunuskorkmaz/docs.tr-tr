---
title: Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: 7c64bdb0cf60fff2dad49c3ffc48629c53abecad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006412"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme
Windows Communication Foundation (WCF) uygulamaları, SOAP hatası nesneleri ve SOAP hatası nesneleri yönetilen özel durum nesnelere yönetilen özel durum nesneleri eşleyerek hata durumları işleyin. Bu bölümdeki konular, hata ortaya çıkarmak için sözleşmeler tasarlamak nasıl özel SOAP hataları olarak koşulları, bu tür hataları hizmeti uygulamasının bir parçası olarak döndürülecek nasıl ve istemciler bu tür hataları nasıl catch tartışın.  
  
## <a name="error-handling-overview"></a>Hata işleme genel bakış  
 Tüm yönetilen uygulamalar, işleme hataları tarafından temsil edilen <xref:System.Exception> nesneleri. SOAP tabanlı uygulamalarda WCF uygulamaları gibi hizmet yöntemleri işleme hata bilgilerini SOAP hata iletileri kullanarak iletişim kurar. SOAP hatalarının bir hizmet işlemi için meta veriler bulunur ve bu nedenle istemcilerin daha sağlam ve etkileşimli kendi işlemi yapmak için kullanabileceği bir hataya sözleşmesi oluşturma iletisi türleridir. XML formundaki istemcilere SOAP hataları gösterilir, ayrıca, istemciler herhangi bir SOAP platformda kullanabilir, WCF uygulamanızı ulaşabileceği artan bir oranda birlikte çalışabilir tür sistemi olmasıdır.  
  
 WCF uygulamaları her iki türde hata sistemleri altında çalıştığından, istemciye gönderilen herhangi bir yönetilen özel durum bilgi gerekir özel SOAP hataları hizmet uygulamasına dönüştürülür, gönderilen ve SOAP hata WCF istemcileri özel durumlar hataya dönüştürüldü. Çift yönlü istemciler söz konusu olduğunda, istemci sözleşmeleri de SOAP hatalarının bir hizmete gönderebilirsiniz. Her iki durumda da, varsayılan hizmet özel davranışları kullanabilirsiniz veya açıkça denetleyebilirsiniz olup olmadığını — ve nasıl — özel durumlar için hata iletileri eşlendi.  
  
 İki tür SOAP hataları gönderilebilir: *bildirilen* ve *bildirilmemiş*. SOAP hataları olan bir işlem olan bildirilmiş bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hatası türü belirten özniteliği. *Bildirilmemiş* SOAP hataları bir işlem için bir sözleşmede belirtilen değil.  
  
 Hizmet işlemleri kullanarak kendi hata bildirme önemle tavsiye edilir <xref:System.ServiceModel.FaultContractAttribute> resmi bir istemci bir işlemin normal seyrinde içinde almayı bekleyebilirsiniz tüm SOAP hataları belirtmek için özniteliği. Ayrıca, bir SOAP hatası yalnızca bir istemci, bilgilerin açıklanması en aza indirmek için bilmeniz gereken bilgileri döndürmek önerilir.  
  
 Genellikle, hizmetler (ve çift yönlü istemciler) başarıyla hata işleme uygulamalarıyla tümleştirmek için aşağıdaki adımları uygulayın:  
  
- Özel durum koşulları için özel SOAP hataları eşleyin.  
  
- İstemciler ve hizmetler gönderin ve SOAP hataları özel durumlar olarak alın.  
  
 Ayrıca, WCF istemcileri ve Hizmetleri bildirilmemiş soap hataları, hata ayıklama amacıyla kullanabileceğiniz ve varsayılan hata davranışına genişletebilirsiniz. Aşağıdaki bölümlerde, bu görevler ve kavramlar açıklanmaktadır.  
  
## <a name="map-exceptions-to-soap-faults"></a>SOAP hataları için özel durumları eşleme  
 Hata koşullarını işleme bir işlem oluşturmanın ilk adımı, hangi koşullar altında bir istemci uygulama hataları hakkında bilgilendirilmesi karar sağlamaktır. Bazı işlemler işlevselliklerini belirli hata koşulları vardır. Örneğin, bir `PurchaseOrder` işlemi, artık satın alma siparişi başlatmasına izin müşteriler belirli bilgiler döndürebilir. Diğer durumlarda, aşağıdaki gibi bir `Calculator` daha genel hizmet `MathFault` SOAP hatası hizmetin tamamı tüm hata koşulları tanımlamak kullanabilirsiniz. İstemcilerin hizmetinizin hata koşulları tanımlandıktan sonra özel bir SOAP hatası oluşturulabilir ve işlemi, karşılık gelen hata koşulu duyduğunuzda, bir SOAP hatası döndüren olarak işaretlenebilir.  
  
 Hizmet veya istemci geliştirme bu adımla ilgili daha fazla bilgi için bkz: [tanımlama ve belirtme hatası](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>İstemcileri ve Hizmetleri özel durumlar olarak SOAP hataları işleme  
 İşlem hata koşullarını tanımlayan özel SOAP hataları tanımlama ve bu işlemlerin söz konusu hataları döndürüyor olarak işaretleme ilk başarılı hata WCF uygulamaları işlemeyi adımlardır. Sonraki adım düzgün bir şekilde gönderme ve alma bu hataların uygulamaktır. Genellikle istemci uygulamaları hakkında hata koşullarını bildirmek için hataları Hizmetleri gönderir, ancak çift yönlü istemci hizmetlerini SOAP hataları da gönderebilirsiniz.  
  
 Daha fazla bilgi için [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Bildirilmemiş SOAP hataları ve hata ayıklama  
 Bildirilen SOAP hataları son derece sağlam, birlikte çalışabilir, dağıtılmış uygulamalar oluşturmak için yararlıdır. Ancak, bazı durumlarda bir bildirilmemiş bir SOAP hatası, bu işlem Web Hizmetleri Açıklama Dili (WSDL) belirtilmeyen bir göndermek hizmet (veya çift yönlü istemci) yararlı olur. Örneğin, bir hizmet geliştirirken, beklenmeyen durumları hata ayıklama amacıyla istemciye bilgileri göndermek için faydalı olan ortaya çıkabilir. Ayrıca, ayarlayabileceğiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini `true` iç hizmet işlemi özel durumları hakkında daha fazla bilgi edinmek için WCF istemcileri izin vermek için. Hem tek hataları gönderme ve hata ayıklama davranışı özelliklerini ayarlamak bölümünde açıklanmıştır [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Yönetilen özel durumlar iç uygulama bilgileri kullanıma sunabileceğinden, ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` kişisel dahil olmak üzere iç hizmet işlemi özel durumları hakkında daha fazla bilgi edinmek için WCF istemcileri izin verebilirsiniz veya diğer hassas bilgilerin.  
>   
>  Bu nedenle, ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` geçici olarak bir hizmet uygulaması hata ayıklamak için yalnızca bir yolu olarak önerilir. Bu şekilde özel durum işlenmemiş döndüren bir yöntem yönetilen ek olarak, WSDL sözleşmesini içermiyor <xref:System.ServiceModel.FaultException%601> türü <xref:System.ServiceModel.ExceptionDetail>. İstemciler, bilinmeyen bir SOAP hatası olasılığını beklemeniz gerekir (WCF istemcileri olarak döndürülen <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesneleri) düzgün bir şekilde hata ayıklama bilgileri edinmek için.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Hata işleme ile Ierrorhandler özelleştirme  
 Uygulama düzeyinde özel bir durum gerçekleştiğinde, istemciye yanıt iletisini özelleştirme veya yanıt iletisi döndürüldükten sonra bazı özel işlem yapmak, uygulamak için özel gereksinimleriniz varsa, <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> arabirimi.  
  
## <a name="fault-serialization-issues"></a>Hata seri hale getirme konuları  
 Hatalı sözleşme işlenirken WCF ilk SOAP iletisi hata sözleşme adı hataya sözleşme türüyle eşleştirmeye çalışır. Ardından listesini arar tam bir eşleşme bulamazsa, uyumlu bir tür için alfabetik sırayla kullanılabilir hata daraltır. İki arıza durumunda sözleşmelerinin (biridir, başka bir alt örneğin) uyumlu türleridir yanlış türde hata seri için kullanılabilir. Hatalı sözleşme adı, ad alanı ve eylem belirtmezse yalnızca gerçekleşir. Bu sorunun oluşmasını önlemek için her zaman tam adı, ad alanı ve eylem öznitelikleri belirterek hata sözleşmelerine nitelendirin. İlgili hata sözleşmelerine paylaşılan bir temel sınıftan türetilmiş bir dizi tanımladıysanız, ayrıca tüm yeni üyeleri ile işaretlenecek emin olun `[DataMember(IsRequired=true)]`. Bunun hakkında daha fazla bilgi için `IsRequired` özniteliği bakın <xref:System.Runtime.Serialization.DataMemberAttribute>. Uyumlu bir türde bir temel sınıf engellemek ve doğru türetilmiş türe seri durumdan hata zorlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.FaultException>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.CommunicationException>
- <xref:System.ServiceModel.FaultContractAttribute.Action%2A>
- <xref:System.ServiceModel.FaultException.Code%2A>
- <xref:System.ServiceModel.FaultException.Reason%2A>
- <xref:System.ServiceModel.FaultCode.SubCode%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- [Hataları Tanımlama ve Belirtme](../../../docs/framework/wcf/defining-and-specifying-faults.md)
