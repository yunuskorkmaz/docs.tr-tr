---
title: Oturumları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: 898e5688ae08a59415c8b3116665eec6cb4cf904
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877381"
---
# <a name="using-sessions"></a>Oturumları Kullanma
Windows Communication Foundation (WCF) uygulamaları bir *oturumu* iletiler grubunu bir konuşma ile ilişkilendirir. WCF oturumları bulunan oturum nesnesi değerinden farklı [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulamaları, farklı davranışları desteklemek ve farklı yollarla denetlenir. Bu konuda WCF'de oturumları sağlayan özellikleri açıklar uygulamaları ve bunların nasıl kullanıldığı.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation uygulamalarında oturumları  
 Bir oturum gerektiren bir hizmet sözleşmesi belirler, bu sözleşme tüm çağrıları (çağrıları destekleyen diğer bir deyişle, temel alınan ileti alışverişlerinde) aynı konuşmada bir parçası olmalıdır belirtme. Bir sözleşme oturumları sağlar ancak bir gerektirmez, istemcilerin bağlanabileceği ya da bir oturumu belirtirse veya bir oturumu yok. Sona ererse ve ileti bir özel durum aynı kanalı gönderilir.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
-   Bunlar açıkça başlatılan ve çağıran uygulama (WCF istemcisi) tarafından sonlandırıldı.  
  
-   Mesajlar oturumu sırasında bunlar alındığı sırayla işlenir.  
  
-   Oturumlarının iletiler grubunu bir sohbete ilişkilendirin. Farklı türde bağıntı mümkündür. Örneğin, oturum tabanlı bir kanalı oturum tabanlı başka bir kanal iletileri ileti gövdesinde paylaşılan bir etiketi temel bağıntısını ancak bir paylaşılan ağ bağlantısının dayalı iletiler ilişkilendirilebilir. Oturumdan elde edilebilir özellikleri bağıntı niteliğine bağlı.  
  
-   Bir WCF oturum ile ilişkili hiçbir genel veri deposu bulunmaktadır.  
  
 Alışkın olduğunuz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfını [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulamalar ve işlevselliği sağlar, bu tür bir oturum ve WCF oturumları arasında aşağıdaki değişiklikler fark edebilirsiniz:  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] oturumlarının her zaman sunucu-başlatılır.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] oturumlarının örtük olarak sırasız.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] oturumları istekler genelinde bir genel veri depolama mekanizmasını sağlar.  
  
 Bu konuda açıklanmaktadır:  
  
-   Oturum tabanlı bağlamalar hizmet modeli katmanını kullanırken varsayılan yürütme davranışı.  
  
-   WCF oturum tabanlı, sistem tarafından sağlanan bağlamaları sağlayan tür.  
  
-   Bir oturum gereksinim bildiren bir sözleşme oluşturma  
  
-   Anlama ve oluşturma ve oturumun sonlandırılması ve hizmet örneği oturuma arasındaki ilişkiyi denetlemek üzere nasıl.  
  
## <a name="default-execution-behavior-using-sessions"></a>Varsayılan yürütme davranışını kullanarak oturumları  
 Oturum başlatma girişiminde bir bağlama adında bir *oturum tabanlı* bağlama. Hizmet sözleşmeleri, bunlar gerektirir, izin veya oturum tabanlı bağlamalar ayarlayarak Reddet belirtin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> birine hizmet sözleşme arabirimi (veya sınıfı) bir özellikte <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> sabit listesi değerleri. Varsayılan olarak, bu özellik değeri <xref:System.ServiceModel.SessionMode.Allowed>, oturum tabanlı bir bağlama kullanan bir WCF hizmeti uygulaması ile olması durumunda bir istemci anlamına gelir, hizmeti oluşturur ve sağlanan oturumu kullanır.  
  
 Bir WCF hizmeti bir istemci oturumundan kabul ettiğinde, aşağıdaki özellikler varsayılan olarak etkindir:  
  
1.  WCF istemci nesnesi arasındaki tüm çağrıların aynı hizmet örneği tarafından işlenir.  
  
2.  Farklı oturum tabanlı bağlamaları, ek özellikler sağlar.  
  
## <a name="system-provided-session-types"></a>Sistem tarafından sağlanan oturum türleri  
 Bir hizmet örneği, varsayılan ilişkisi belirli bir oturum ile oturum tabanlı bir bağlamayı destekler. Ancak, farklı oturum tabanlı bağlamalar daha önce açıklanan oturum tabanlı örneklemesini denetimini etkinleştirme yanı sıra farklı özellikleri destekler.  
  
 WCF oturum tabanlı uygulama davranışı aşağıdaki türlerini sağlar:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> İçinde her iki ucunda da iletişim anlaşılan belirli bir güvenli konuşma güvenlik tabanlı oturumları destekler. Daha fazla bilgi için [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md). Örneğin, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> bağlama, destek güvenlik oturumları ve güvenilir oturumlar için varsayılan olarak içeren şifreleyen ve iletileri dijital olarak imzalar yalnızca güvenli bir oturum kullanır.  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> Bağlama IP tabanlı oturumları tüm iletileri yuva düzeyinde bağlantısı tarafından bağıntılı olan emin olmak için destekler.  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> WS-ReliableMessaging belirtimini uygulayan öğesi içinde iletileri yapılandırılabilir ve tam olarak bile iletileri giderken iletilerin alındığı sağlama sonra teslim edilmek üzere güvenli oturumlar için destek sağlar Konuşma sırasında birden fazla düğümde. Daha fazla bilgi için [güvenilir oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> Bağlama için MSMQ veri birimi oturumları sağlar. Daha fazla bilgi için [wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Ayarı <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği olan bir gerektirir. yalnızca sözleşmesi gerektirir, oturumun türünü belirtmiyor.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Bir oturum gerektiren bir sözleşme oluşturma  
 Bir oturum grubun hizmet sözleşmesi bildirir işlemlerinin tümü aynı oturumunda yürütülmesi gerektiğini ve iletiler sırada teslim edilmesini durumları gerektiren bir sözleşme oluşturma. Hizmet sözleşmesi gerektirir oturumu destek düzeyini onaylanacak ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği hizmet sözleşme arabirimi veya sınıf değerine <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> belirtmek için sabit listesi olmadığını Sözleşme:  
  
-   Bir oturum gerektirir.  
  
-   Oturum oluşturmak bir istemci sağlar.  
  
-   Bir oturum açmasına izin vermez.  
  
 Ayarı <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği, ancak belirtmiyor türden bir oturum tabanlı davranış sözleşmesi gerektirir. Çalışma zamanında onaylamak için WCF bildirir, (Bu iletişim kanalını oluşturur) bağlama hizmeti yok, yok ya da oturum oluşturmak yapılandırılan hizmet uygularken. Bağlama seçer, bu gereksinimi herhangi bir türde oturum tabanlı olarak davranışı yeniden karşılayabilecek — güvenlik, taşıma, güvenilir veya bunların bir birleşimini. Tam davranış bağımlı <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> seçili değer. Yapılandırılmış bağlama hizmeti değeri olarak uyumlu değilse <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, bir özel durum oluşturulur. Bağlamalar ve kanalları destek oturumları oturum tabanlı olduğu söylenir oluşturma.  
  
 Aşağıdaki hizmet sözleşmesi belirten tüm işlemlerde `ICalculatorSession` oturum içindeki değiştirilen gerekir. Çağırana dışında bir değer döndürür işlemlerden hiçbiri `Equals` yöntemi. Ancak, `Equals` yöntem parametre almayan ve bu nedenle, yalnızca içinde veri zaten geçirilmiş diğer işlemler için oturumu içinde bir sıfır olmayan değer döndürebilir. Bu sözleşme düzgün çalışması için bir oturum gerektirir. Belirli bir istemci ile ilişkili bir oturum olmadan, hizmet örneği bu istemcinin gönderdiği hangi önceki veri olduğunu bilmesinin bir yolu yoktur.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Bir hizmet bir oturuma izin veriyorsa, ardından oturumu oluşturulur ve istemci başlatırsa kullanılan; Aksi takdirde, hiçbir oturum kurulur.  
  
## <a name="sessions-and-service-instances"></a>Oturumlarının ve hizmet örnekleri  
 WCF davranışı depolamasına varsayılan kullanırsanız, WCF istemci nesnesi arasındaki tüm çağrıların aynı hizmet örneği tarafından işlenir. Bu nedenle, uygulama düzeyinde oturumunun etkinleştirme uygulama davranışını yerel çağrı davranışa benzer olarak düşünebilirsiniz. Örneğin, yerel bir nesne oluşturduğunuzda:  
  
-   Bir oluşturucu çağrılır.  
  
-   WCF istemci nesne başvurusu yapılan tüm sonraki çağrılar, aynı nesne örneği tarafından işlenir.  
  
-   Nesne başvurusu kaldırıldığında bir yok Edicisi çağrılır.  
  
 Varsayılan hizmet örneği davranışı kullanılan sürece istemciler ve hizmetler arasındaki benzer bir davranış oturumları etkinleştir. Başlatma veya ayarlayarak bir oturumu sonlandırma olarak hizmet sözleşmesi gerektirir ya da oturumları destekler, bir veya daha fazla sözleşme operations işaretlenebilir <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> ve <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> özellikleri.  
  
 *İşlemleri başlatma* ilk yeni bir oturum işlemi olarak çağrılmalıdır olanlardır. Olmayan başlatma işlemlerini en az bir başlatma işlemi yalnızca çağrıldıktan sonra çağrılabilir. Bu nedenle, hizmet örneği başına uygun istemcilerden giriş almak üzere tasarlanmış başlatma işlemleri bildirerek oturumu Oluşturucusu bir tür hizmetiniz için oluşturabilirsiniz. (Durum, oturum, ancak hizmet nesnesi ile ilişkili şeklindedir.)  
  
 *İşlemleri sonlandırma*, buna karşılık, son iletiyi varolan bir oturumda çağrılmalıdır olanla aynıdır. Hizmet ilişkili oturumu kapatıldıktan sonra varsayılan durumda, WCF Hizmeti nesnesi ve onun bağlamı geri dönüştürür. Bu nedenle, bir tür yok Edicisi sonuna bir hizmet örneği için uygun bir işlevi gerçekleştirmek için tasarlanmış sonlandırma işlemleri bildirerek oluşturabilirsiniz.  
  
> [!NOTE]
>  Varsayılan davranışı bir benzerlik yerel oluşturucular ve Yıkıcılar taşıyan olsa da, bu yalnızca bir benzeyen olur. Herhangi bir WCF hizmeti işlemi, bir başlatma veya sonlandırma işlemi ya da aynı anda hem de olabilir. Ayrıca, varsayılan durumda, işlemleri başlatma herhangi sayıda herhangi bir sırada çağrılabilir; sonra oturumu oluşturulur ve açıkça hizmet örneği ömrünü denetlemek sürece bir örnekle ilişkili ek bir oturum yok oluşturulur (düzenleme tarafından <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> nesne). Son olarak oturum ve hizmet nesnesi ile ilişkili durumudur.  
  
 Örneğin, `ICalculatorSession` önceki örnekte kullanılan sözleşme gerekiyor WCF istemcisini ilk çağrı nesne `Clear` işlemi başka bir işlem ve, önce bu WCF istemci nesnesi oturumla çağırdığındaçağrısıyla`Equals` işlemi. Aşağıdaki kod örneği, bu gereksinimleri zorlayan bir sözleşme gösterir. `Clear` bir oturum başlatmak için önce çağrılmalıdır ve oturumu ne zaman sona ereceğini `Equals` çağrılır.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Hizmetleri oturumları istemciler başlatılmaz. WCF istemci uygulamalarının içinde oturum ömrünü ve oturum tabanlı kanal ömrünü arasında doğrudan bir ilişki yok. Bu nedenle, istemciler oturum tabanlı yeni kanalları oluşturarak yeni oturumları oluşturmasına ve oturum tabanlı kanalları düzgün bir şekilde kapatarak oturumlarına ayırma. Bir istemci, aşağıdakilerden birini çağırarak bir hizmet uç noktası ile bir oturumu başlatır:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> bir çağrı tarafından döndürülen kanalda <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> tarafından oluşturulan WCF istemci nesnesi üzerinde [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
-   WCF istemci nesnesi iki tür başlatan bir işlem (varsayılan olarak, tüm işlemleri başlatma). İlk işlem çağrıldığında, WCF istemci nesnesi, otomatik olarak kanal açar ve bir oturumu başlatır.  
  
 Genellikle bir istemci, aşağıdakilerden birini çağırarak bir hizmet uç noktası ile bir oturumu biter:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> bir çağrı tarafından döndürülen kanalda <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> svcutil.exe'yi oluşturulan WCF istemci nesne.  
  
-   WCF istemci nesnesi iki tür bir sonlandırma işlemi (varsayılan olarak, hiçbir işlem sonlandırma; sözleşmeyi sonlandırma işlemi açıkça belirtmeniz gerekir). İlk işlem çağrıldığında, WCF istemci nesnesi, otomatik olarak kanal açar ve bir oturumu başlatır.  
  
 Örnekler için bkz [nasıl yapılır: bir hizmet, gerektirir oturumları oluşturmasına](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) yanı sıra [varsayılan hizmet davranışı](../../../docs/framework/wcf/samples/default-service-behavior.md) ve [Instancing](../../../docs/framework/wcf/samples/instancing.md) örnekleri.  
  
 İstemcileri ve oturumları hakkında daha fazla bilgi için bkz: [WCF istemci kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlarının InstanceContext ayarlarla etkileşim  
 Arasında bir etkileşim yoktur <xref:System.ServiceModel.SessionMode> sözleşme numaralandırmada ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> Kanallar ve belirli hizmet nesneleri arasındaki ilişki denetleyen özelliği. Daha fazla bilgi için [oturumları Instancing ve eşzamanlılık](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesneleri paylaşma  
 Hangi oturum tabanlı kanal de denetleyebilirsiniz veya çağrı ile ilişkili <xref:System.ServiceModel.InstanceContext> kendinizi bu ilişkiyi gerçekleştirerek nesne. Tam bir örnek için bkz. [InstanceContextSharing](https://msdn.microsoft.com/library/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230).  
  
## <a name="sessions-and-streaming"></a>Oturumlarının ve akış  
 Büyük miktarda veri aktarmak için akış aktarım WCF arabelleğe alma ve iletilerini tamamen belleğindeki işleme varsayılan davranışına uygun bir alternatif modundadır. Oturum tabanlı bir bağlamayla çağrıları akışı yapılırken beklenmeyen davranışı elde edebilirsiniz. Tüm akış çağrılar kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, oturumları desteklemiyor tek kanalı (veri birimi kanal) yapılır. Birden çok istemci aynı hizmet nesnesi akış çağrıları üzerinden oturum tabanlı bir bağlama yapın ve hizmet nesnenin eşzamanlılık modu, tek ve kendi örnek bağlamı modu için ayarlanmışsa ayarlanır `PerSession`, tüm çağrıları, veri birimi kanal ve bu nedenle gitmelidir. yalnızca bir çağrı teker teker işlenir. Bir veya daha fazla istemciler daha sonra zaman aşımına uğrayabilir. Bu sorunu geçici olarak ya da hizmet nesnenin ayarlayarak çalışabilir `InstanceContextMode` için `PerCall` veya birden fazla eşzamanlılık.  
  
> [!NOTE]
>  Kullanılabilir tek bir "oturum" olduğundan MaxConcurrentSessions bu durumda hiçbir etkisi yoktur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
