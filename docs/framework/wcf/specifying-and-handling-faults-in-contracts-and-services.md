---
title: "Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57fc01b77379389ca4d86d241ec8f3d672b519b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]uygulamaları, SOAP hataya ve SOAP hataya nesneleri yönetilen özel durum nesneleri için yönetilen özel durum nesneleri eşleme tarafından hata durumları işler. Bu bölümdeki konular, koşul olarak özel SOAP hataları, hizmet uygulaması'nın bir parçası olarak bu tür hataları döndürmek nasıl ve nasıl böyle hatası istemciler catch hata kullanıma sunmak için sözleşmeleri tasarlamak nasıl tartışın.  
  
## <a name="error-handling-overview"></a>Hata işleme genel bakış  
 Tüm yönetilen uygulamalarda işleme hataları tarafından temsil edilen <xref:System.Exception> nesneleri. SOAP tabanlı uygulamalarda olduğu gibi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar, hizmet yöntemleri iletişim SOAP hata iletileri kullanarak hata bilgilerini işleme. SOAP, bir hizmet işlemi için meta verileri içinde yer alan ve bu nedenle istemciler daha sağlam veya etkileşimli kendi işlemi yapmak için kullanabileceğiniz bir arıza sözleşmesi oluşturma ileti türlerini hatalarıdır. SOAP hataları XML formundaki istemcilere ifade edilir çünkü ek olarak, ulaşabileceği artırma herhangi bir SOAP platformda istemcilerin kullanabileceği bir yüksek oranda birlikte çalışabilir türü sistemdir, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulama.  
  
 Çünkü [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamaları çalıştırmak hata sistemleri her iki tür altında istemciye gönderilen herhangi bir yönetilen özel durum bilgi gerekir özel durumlardan SOAP hataları Service uygulamasına dönüştürülür, gönderilen ve hataya özel durumları SOAP hataları dönüştürülüp [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemciler. Çift yönlü istemciler söz konusu olduğunda, istemci sözleşmeleri bir hizmete geri SOAP hataları da gönderebilirsiniz. Her iki durumda da, varsayılan hizmet özel durum davranışları kullanabilir veya açıkça denetleyebilirsiniz olup olmadığını — ve nasıl — özel durumlar için hata iletileri eşlendi.  
  
 İki tür SOAP hataları gönderilebilir: *bildirilen* ve *bildirilmemiş*. SOAP hataları olan bir işlem olduğu bildirildiğinde bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hatası türü belirten özniteliği. *Bildirilmemiş* bir işlem için sözleşmede SOAP hataları belirtilmedi.  
  
 Hizmet işlemleri kullanarak bunların hatalarını bildirme kesinlikle önerilir <xref:System.ServiceModel.FaultContractAttribute> resmi olarak bir istemci bir işlemi normal seyri içinde almayı bekleyebileceğiniz tüm SOAP hataları belirtmek için özniteliği. Ayrıca, bir SOAP hatası istemci bilgilerin açığa çıkmasına en aza indirmek için bilmeniz gereken bilgileri döndürmek önerilir.  
  
 Genellikle, hizmetler (ve çift yönlü istemcileri) başarıyla hata uygulamalarına işleme tümleştirmek için aşağıdaki adımları uygulayın:  
  
-   Özel durumları için özel SOAP hataları eşleyin.  
  
-   İstemcileri ve Hizmetleri gönderebilir ve özel durumlar olarak SOAP hataları alabilirsiniz.  
  
 Ayrıca, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri ve Hizmetleri bildirilmemiş soap hataları hata ayıklama amacıyla kullanabilirsiniz ve varsayılan hata davranışı genişletebilirsiniz. Aşağıdaki bölümlerde, bu görevleri ve kavramları açıklanmaktadır.  
  
## <a name="map-exceptions-to-soap-faults"></a>SOAP hataları için özel durumları eşleme  
 Hata koşullarını işleme bir işlem oluşturmanın ilk adımı, hangi koşullar altında bir istemci uygulama hataları hakkında bilgi sahibi olmak karar vermektir. Hata koşulları işlevselliklerini belirli bazı işlemler vardır. Örneğin, bir `PurchaseOrder` işlemi artık bir satın alma siparişi başlatmak için izin verilen müşterileri için belirli bilgiler döndürebilir. Diğer durumlarda, aşağıdaki gibi bir `Calculator` hizmet, daha genel `MathFault` bir SOAP hatası tüm bir hizmetin tüm hata koşullarını tanımlamak kullanabilirsiniz. Hizmetinizin istemcileri hata koşullarını tanımlandıktan sonra özel bir SOAP hatası oluşturulabilir ve işlem, ilgili hata koşulu duyduğunuzda, bir SOAP hatası döndürerek olarak işaretlenebilir.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Bu adım olarak hizmet veya istemci, geliştirme bkz [tanımlama ve belirtme hataları](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>İstemcileri ve Hizmetleri SOAP hataları özel durumları işleme  
 İşlem hata koşullarını tanımlamak, özel SOAP hataları tanımlama ve bu işlemler bu hataları döndürüyor olarak işaretleme olan ilk adımlar başarılı hata içinde işleme [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar. Sonraki adım düzgün bir şekilde gönderme ve alma bu hatalarının uygulamaktır. Genellikle Hizmetleri istemci uygulamaları hata koşulları hakkında bilgilendirmek için hataları gönderme, ancak çift yönlü istemcileri de Hizmetleri SOAP hataları gönderebilirsiniz.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hataları gönderme ve alma](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Bildirilmemiş SOAP hataları ve hata ayıklama  
 Bildirilen SOAP hataları sağlam, birlikte çalışabilen, dağıtılmış uygulamaları oluşturmak için son derece yararlıdır. Ancak, bazı durumlarda bir bildirilmemiş bir SOAP hatası, bu işlem Web Hizmetleri Açıklama Dili (WSDL) belirtilmeyen bir göndermek hizmet (veya çift yönlü istemci) yararlı olur. Örneğin, bir hizmet geliştirirken, beklenmeyen durumları hata ayıklama bilgileri istemciye göndermek amacıyla faydalı olduğu ortaya çıkabilir. Ayrıca, ayarlayabileceğiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğine `true` izin vermek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] iç hizmet işlemi özel durumlar hakkında bilgi edinmek için istemcileri. Hem tek tek hataları gönderme ve hata ayıklama davranışı özelliklerini ayarlama bölümünde açıklanmıştır [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Yönetilen özel durumlar iç uygulama bilgileri kullanıma sunabileceğinden ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` izin verebilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kişisel dahil olmak üzere iç hizmet işlemi özel durumlar hakkında bilgi edinmek için istemciler Kişisel ya da diğer hassas bilgiler.  
>   
>  Bu nedenle, ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` geçici olarak bir hizmet uygulaması hata ayıklamak için yalnızca bir yolu olarak önerilir. İşlenmemiş döndüren bir yöntem yönetilen özel durumları bu şekilde ek olarak, WSDL sözleşmesi içermiyor <xref:System.ServiceModel.FaultException%601> türü <xref:System.ServiceModel.ExceptionDetail>. İstemciler, bilinmeyen bir SOAP hatası olasılığını beklediğiniz gerekir (döndürülen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri olarak <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesneler) hata ayıklama bilgilerini düzgün şekilde alınamadı.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Hata işleme ile IErrorHandler özelleştirme  
 Uygulama düzeyi özel durum gerçekleştiğinde istemciye yanıt iletisini özelleştirme veya yanıt iletisi döndürüldükten sonra bazı özel işlem yapmak, uygulamak için özel gereksinimleri varsa <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> arabirimi.  
  
## <a name="fault-serialization-issues"></a>Hataya seri hale getirme konuları  
 Hatalı sözleşme çıkarılırken WCF ilk hataya sözleşme adı SOAP iletisi hataya sözleşme türüyle eşleştirmeye çalışır. Ardından listesi arar tam bir eşleşme bulamazsa, uyumlu bir türü için alfabetik sırada kullanılabilir hata sözleşmeleri. İki arıza durumunda sözleşmeleri (biridir, başka bir alt sınıfı gibi) uyumlu türleridir yanlış türde seri durumundan hata için kullanılabilir. Bu yalnızca, hatalı sözleşme adı, ad alanı ve eylem belirtmiyor oluşur. Bu sorunun oluşmasını önlemek için her zaman tam adı, ad alanı ve eylem özniteliklerinin belirterek hataya sözleşmeleri nitelemek. Paylaşılan bir temel sınıfından türetilen ilgili hata sözleşmeleri sayısı tanımladıysanız, ayrıca tüm yeni üyeleriyle işaretlemek emin olun `[DataMember(IsRequired=true)]`. Bunun hakkında daha fazla bilgi için `IsRequired` özniteliği bakın, <xref:System.Runtime.Serialization.DataMemberAttribute>. Bu, uyumlu bir türde bir taban sınıf engelleyen ve doğru türetilmiş türe seri durumdan çıkarılacak hataya zorlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.CommunicationException>  
 <xref:System.ServiceModel.FaultContractAttribute.Action%2A>  
 <xref:System.ServiceModel.FaultException.Code%2A>  
 <xref:System.ServiceModel.FaultException.Reason%2A>  
 <xref:System.ServiceModel.FaultCode.SubCode%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 [Hataları Tanımlama ve Belirtme](../../../docs/framework/wcf/defining-and-specifying-faults.md)
