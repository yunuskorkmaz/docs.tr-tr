---
title: "Oturumlar, Örnek Oluşturma ve Eşzamanlılık"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d4559f177b05f7d238c9f30649a5b01af7fb6f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sessions-instancing-and-concurrency"></a>Oturumlar, Örnek Oluşturma ve Eşzamanlılık
A *oturum* iki uç noktaları arasında gönderilen tüm iletiler bağıntı değil. *Örnek oluşturma* kullanıcı tanımlı bir hizmet nesneleri ve bunların ilgili ömrü denetlenmesi için başvuruyor <xref:System.ServiceModel.InstanceContext> nesneleri. *Eşzamanlılık* olan içinde çalışan iş parçacıklarının sayısını denetlemek için belirtilen terimin bir <xref:System.ServiceModel.InstanceContext> aynı anda.  
  
 Bu konuda, bu ayarları açıklanmaktadır bunları ve bunların arasındaki çeşitli etkileşimleri kullanma.  
  
## <a name="sessions"></a>Oturumlar  
 Ne zaman bir hizmet sözleşmesini ayarlar <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, bu sözleşme tüm çağrıları (çağrıları destekleyen başka bir deyişle, temel alınan ileti alışverişlerinde) aynı konuşmada bir parçası olması gerektiğini söyleyen. Bir sözleşme oturumları sağlar ancak bir gerektirmez, istemcilerin bağlanabileceği ya da bir veya oturumu belirtirse. Sona ererse ve bir ileti aynı oturum tabanlı kanal bir özel durum atılır gönderilir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
-   Bunlar açıkça başlatılan ve çağıran uygulama tarafından sonlandırıldı.  
  
-   Bir oturumda teslim edilen ileti bunlar alındığı sırada işlenir.  
  
-   Oturumları iletileri bir grup konuşma bağıntısını. Bu bağıntı anlamını bir soyutlamadır. Örneğin, bir oturum tabanlı kanalı başka bir oturum tabanlı kanal ileti gövdesinde paylaşılan bir etiket dayanan iletilerin ilişkilendirilebilir bir paylaşılan ağ bağlantısı üzerinde tabanlı iletileri ilişkilendirilebilir. Oturumdan elde edilebilir özelliklerine bağıntı yapısına bağlıdır.  
  
-   İle ilişkili bir genel veri depo bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumu.  
  
 Hakkında bilginiz varsa <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfını [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları ve işlevselliği sağlar, bu tür bir oturum arasındaki aşağıdaki farkları görebilirsiniz ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumları:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]oturumları her zaman sunucu-başlatılır.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]oturumları örtük olarak sıralanmamış.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]oturumları istekler genelinde bir genel veri depolama mekanizması sağlar.  
  
 İstemci uygulamaları ve hizmet uygulamaları oturumlarıyla farklı şekillerde etkileşim. İstemci uygulamaları oturumlarını başlatmak ve ardından almak ve oturum içinde gönderilen iletileri işleme. Hizmet uygulamaları oturumları ek davranış eklemek için bir genişletilebilirlik noktası olarak kullanın. Bu doğrudan ile çalışarak yapılır <xref:System.ServiceModel.InstanceContext> veya özel örnek bağlamı sağlayıcıyı uygulama.  
  
## <a name="instancing"></a>Örnek Oluşturma  
 Örneklemesini davranış (kullanarak ayarlamak <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği) denetimleri nasıl <xref:System.ServiceModel.InstanceContext> gelen iletilere yanıt olarak oluşturulur. Varsayılan olarak, her <xref:System.ServiceModel.InstanceContext> bir kullanıcı tanımlı bir hizmet nesnesiyle ilişkili bunu (varsayılan durumda) ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği de denetler depolamasına kullanıcı tanımlı hizmet nesneleri. <xref:System.ServiceModel.InstanceContextMode> Numaralandırma örneklemesini modlarını tanımlar.  
  
 Aşağıdaki örneklemesini modları kullanılabilir:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Yeni bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle nesne servis) her istemci isteği için oluşturulur.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Yeni bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle nesne servis) her yeni istemci oturumu için oluşturulur ve bu oturuma (Bu gerektirir oturumları destekleyen bir bağlama) ömrü boyunca saklanır.  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Bir tek <xref:System.ServiceModel.InstanceContext> (ve bu nedenle nesne servis) uygulama ömrü boyunca tüm istemci isteklerini işler.  
  
 Aşağıdaki kod örneğinde varsayılan gösterir <xref:System.ServiceModel.InstanceContextMode> değeri <xref:System.ServiceModel.InstanceContextMode.PerSession> açıkça bir hizmet sınıfında ayarlanan.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 Ve while <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği denetler ne sıklıkta <xref:System.ServiceModel.InstanceContext> yayımlandığı <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> denetim özelliklerini hizmet nesnesi serbest bırakıldığında.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen Singleton Hizmetleri  
 Tek örnek hizmet nesneler üzerinde bir değişim bazen faydalıdır: bir hizmet nesnesi kendiniz oluşturmanız ve bu nesneyi kullanarak hizmet ana bilgisayarını oluşturun. Bunu yapmak için de ayarlamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.InstanceContextMode.Single> ya da hizmet konağı açıldığında bir özel durum oluşur.  
  
 Kullanım <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> gibi bir hizmet oluşturmak için Oluşturucusu. Özel bir uygulama için bir alternatif sağlayan <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> belirli nesne örneği bir singleton hizmeti tarafından kullanım için sağlamak istediğiniz zaman. Hizmet uygulama türü (örneğin, onu varsayılan parametresiz ortak oluşturucu uygulamadığında) oluşturmak zor olduğu durumlarda, bu aşırı yüklemesini kullanabilirsiniz.  
  
 Bu oluşturucuya bir nesne sağlandığında, bazı özellikler için ilgili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] davranışı iş farklı depolamasına. Örneğin, arama <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> singleton nesne örneği sağlandığında hiçbir etkisi olmaz. Benzer şekilde, başka bir örneğinin yayın mekanizma göz ardı edilir. <xref:System.ServiceModel.ServiceHost> Her zaman davranır gibi <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> tüm işlemleri için.  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesneleri paylaşımı  
 Hangi süre sonuyla kanalı kontrol edebilirsiniz veya çağrı, kendisiyle ilişkilendirilmiş <xref:System.ServiceModel.InstanceContext> kendiniz bu ilişkiyi gerçekleştirerek nesnesi.  
  
## <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık denetimi etkin iş parçacığı sayısı olan bir <xref:System.ServiceModel.InstanceContext> herhangi bir zamanda. Bu kullanılarak denetlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> ile <xref:System.ServiceModel.ConcurrencyMode> numaralandırması.  
  
 Aşağıdaki üç eşzamanlılık modu kullanılabilir:  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>: Her örnek bağlamı en fazla bir iş parçacığı aynı anda örneği bağlamında iletileri işleme izin verilmez. Örnek bağlamı özgün iş parçacığı çıkar kadar aynı örnek bağlamı kullanmak isteyen başka bir iş parçacığı engellemelidir.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Her hizmet örneği birden çok iş parçacığı iletileri aynı anda işleme sahip olabilir. Hizmet uygulaması bu eşzamanlılık modunu kullanmak için iş parçacığı açısından güvenli olması gerekir.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Her hizmet örneği aynı anda tek bir ileti işler, ancak içe işlemi çağrılarını kabul eder. Bunu aracılığıyla çağrılırken hizmet yalnızca bu çağrıları kabul bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci nesnesi.  
  
> [!NOTE]
>  Anlama ve güvenli bir şekilde birden çok iş parçacığı kullanan kodu geliştirme başarıyla yazmak zor olabilir. Kullanmadan önce <xref:System.ServiceModel.ConcurrencyMode.Multiple> veya <xref:System.ServiceModel.ConcurrencyMode.Reentrant> değerleri emin olun, hizmeti bu modları için düzgün şekilde tasarlanmıştır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Eşzamanlılık kullanımını örnekleme modunu ilişkilidir. İçinde <xref:System.ServiceModel.InstanceContextMode.PerCall> her ileti yeni tarafından işlenir depolamasına, eşzamanlılık ilgili, olmadığından <xref:System.ServiceModel.InstanceContext> ve bu nedenle, hiçbir zaman birden fazla iş parçacığının etkin olduğu <xref:System.ServiceModel.InstanceContext>.  
  
 Aşağıdaki kod örneğinde ayarı gösterilmektedir <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> özelliğine <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumları InstanceContext ayarlarla etkileşim  
 Oturumlar ve <xref:System.ServiceModel.InstanceContext> değerini birleşimi bağlı olarak etkileşim <xref:System.ServiceModel.SessionMode> bir sözleşme numaralandırmada ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> kanalları özel arasındaki ilişkiyi denetimleri hizmet uygulaması özelliği Hizmet nesneleri.  
  
 Aşağıdaki tabloda oturumları destekleme ya da bir hizmetin değerlerini birleşimi verilen oturumları desteklemediğinden gelen kanal sonucunu gösterir <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği.  
  
|InstanceContextMode değeri|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Süre sonuyla kanal davranışa: bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />-Oturumsuz kanal davranışa: özel durum oluşur.|-Süre sonuyla kanal davranışa: bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />-Oturumsuz kanal davranışa: bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|-Süre sonuyla kanal davranışa: özel durum oluşur.<br />-Oturumsuz kanal davranışa: bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|  
|Değeri PerSession|-Süre sonuyla kanal davranışa: bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanalı.<br />-Oturumsuz kanal davranışa: özel durum oluşur.|-Süre sonuyla kanal davranışa: bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanalı.<br />-Oturumsuz kanal davranışa: bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|-Süre sonuyla kanal davranışa: özel durum oluşur.<br />-Oturumsuz kanal davranışa: bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|  
|Tek|-Süre sonuyla kanal davranışa: bir oturum ve bir <xref:System.ServiceModel.InstanceContext> tüm çağrıları için.<br />-Oturumsuz kanal davranışa: özel durum oluşur.|-Süre sonuyla kanal davranışa: bir oturum ve <xref:System.ServiceModel.InstanceContext> oluşturulan ya da kullanıcı tarafından belirtilen tekli için.<br />-Oturumsuz kanal davranışa: bir <xref:System.ServiceModel.InstanceContext> oluşturulan ya da kullanıcı tarafından belirtilen tekli için.|-Süre sonuyla kanal davranışa: özel durum oluşur.<br />-Oturumsuz kanal davranışa: bir <xref:System.ServiceModel.InstanceContext> oluşturulan her singleton veya kullanıcı tarafından belirtilen tekli için.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oturumları Kullanma](../../../../docs/framework/wcf/using-sessions.md)  
 [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)  
 [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)  
 [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)  
 [Örnek Oluşturma](../../../../docs/framework/wcf/samples/instancing.md)  
 [Oturum](../../../../docs/framework/wcf/samples/session.md)
