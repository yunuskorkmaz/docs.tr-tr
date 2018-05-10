---
title: Oturumları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: da877568d5444ed9cfcf041adc378f7fc95cb774
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="using-sessions"></a>Oturumları Kullanma
Windows Communication Foundation (WCF) uygulamalarında bir *oturum* iletileri bir grup konuşma karşılık gelen. WCF oturumları bulunan oturum nesnesi farklı [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulamaları, farklı davranışlar desteklemek ve farklı şekillerde denetlenir. Bu konu içinde WCF oturumları etkinleştir özellikleri açıklar uygulamaları ve bunların nasıl kullanılacağını.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation uygulamaları oturumlarında  
 Bir oturum gerektiren bir hizmet sözleşmesini belirtir, bu sözleşme tüm çağrıları (çağrıları destekleyen başka bir deyişle, temel alınan ileti alışverişlerinde) aynı konuşmada parçası olmalıdır belirtme. Bir sözleşme oturumları sağlar ancak bir gerektirmez, istemcilerin bağlanabileceği ya da bir oturumu belirtirse veya bir oturumu değil. Sona ererse ve bir ileti bir özel durum aynı kanal gönderilir.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
-   Bunlar açıkça başlatılan ve çağıran uygulamada (WCF istemcisi) tarafından sonlandırıldı.  
  
-   Bir oturumda teslim edilen ileti bunlar alındığı sırada işlenir.  
  
-   Oturumları iletileri bir grup konuşma bağıntısını. Bağıntı farklı türlerde mümkündür. Örneğin, bir oturum tabanlı kanalı başka bir oturum tabanlı kanal ileti gövdesinde paylaşılan bir etiket dayanan iletilerin ilişkilendirilebilir bir paylaşılan ağ bağlantısı üzerinde tabanlı iletileri ilişkilendirilebilir. Oturumdan elde edilebilir özelliklerine bağıntı yapısına bağlıdır.  
  
-   Bir WCF oturum ile ilişkili bir genel veri depo yok.  
  
 Hakkında bilginiz varsa <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfını [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulamaları ve işlevselliği sağlar, bu tür bir oturum ve WCF oturumları arasında aşağıdaki değişiklikler fark edebilirsiniz:  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] oturumları her zaman sunucu-başlatılır.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] oturumları örtük olarak sıralanmamış.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] oturumları istekler genelinde bir genel veri depolama mekanizması sağlar.  
  
 Bu konuda açıklanmaktadır:  
  
-   Hizmet modeli katmanını oturum tabanlı bağlamalar kullanılarak varsayılan yürütme davranış.  
  
-   WCF oturum tabanlı, sistem tarafından sağlanan bağlamaları özellik türleri.  
  
-   Bir oturum gereksinim bildiren bir sözleşme oluşturma  
  
-   Nasıl anlamak ve oluşturma ve oturum sonlandırma ve hizmet örneği oturumuna ilişki denetler.  
  
## <a name="default-execution-behavior-using-sessions"></a>Varsayılan yürütme davranışı kullanarak oturumları  
 Oturum başlatma girişiminde bir bağlama adlı bir *oturum tabanlı* bağlama. Hizmet sözleşmeleri belirtin bunlar gerektiren, izin veya oturum tabanlı bağlamalar ayarlayarak Reddet <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> birine hizmet sözleşme arabirimi (veya sınıfı) özelliği <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> numaralandırma değerleri. Varsayılan olarak, bu özellik değeri <xref:System.ServiceModel.SessionMode.Allowed>olması durumunda bir istemci başka bir deyişle, oturum tabanlı bir bağlama bir WCF hizmeti uygulamasıyla kullanır, hizmet oluşturur ve sağlanan oturumu kullanır.  
  
 Bir WCF hizmeti bir istemci oturumundan kabul ettiğinde, aşağıdaki özellikler varsayılan olarak etkindir:  
  
1.  WCF istemci nesnesi arasındaki tüm çağrıları aynı hizmet örneği tarafından işlenir.  
  
2.  Farklı oturum tabanlı bağlamalar ek özellikler sağlar.  
  
## <a name="system-provided-session-types"></a>Sistem tarafından sağlanan oturum türleri  
 Bir hizmet örneği varsayılan ilişki belirli bir oturum ile oturum tabanlı bir bağlama destekler. Ancak, farklı oturum tabanlı bağlamalar daha önce açıklanan oturum tabanlı örneklemesini denetimini etkinleştirme yanı sıra farklı özellikleri destekler.  
  
 WCF oturum tabanlı uygulama davranışına aşağıdaki türlerini sağlar:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> , İletişimin her iki ucuna anlaşılan belirli güvenli bir konuşma güvenlik tabanlı oturumları destekler. Daha fazla bilgi için bkz: [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md). Örneğin, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> bağlama, destek güvenlik oturumları ve güvenilir oturumlar için varsayılan olarak içeren şifreleyen ve iletileri dijital imzalar bir güvenli oturum kullanır.  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> Bağlama tüm iletileri yuva düzeyinde bağlantısı tarafından bağıntılı olan emin olmak için oturumları TCP tabanlı destekler.  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> WS-ReliableMessaging belirtimini uygular, öğe iletileri yapılandırılabilecek sırayla ve tam olarak iletileri alınan iletileri bile giderken olduktan sonra teslim edilecek güvenli oturumlar için destek sağlar Konuşma sırasında birden çok düğüm arasında. Daha fazla bilgi için bkz: [güvenilir oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> Bağlama MSMQ veri birimi oturumları sağlar. Daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Ayar <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği olan gerektiren yalnızca sözleşme gerektirir, oturum türünü belirtmiyor.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Bir oturum gerektiren bir sözleşme oluşturma  
 Hizmet sözleşmesi bildirir işlemler grubunun tüm aynı oturum içinde yürütülmelidir olduğunu ve iletilerin sırayla teslim gerekir oturum durumları gerektiren bir sözleşme oluşturma. Bir hizmet sözleşmesini gerektiriyor oturum desteği düzeyini onaylanacak ayarlamak <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> hizmet sözleşme arabirimi veya değerini sınıfına özellik <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> belirtmek için numaralandırma olup olmadığını Sözleşme:  
  
-   Bir oturum gerektirir.  
  
-   Oturum oluşturmak bir istemcinin sağlar.  
  
-   Bir oturum açmasına izin vermez.  
  
 Ayar <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği, ancak belirtmiyor tür oturum tabanlı davranışı sözleşme gerektirir. Çalışma zamanında onaylamak için WCF bildirir, hizmet yapar, yok veya oturum oluşturmak için (hangi iletişim kanalı oluşturur) bağlama yapılandırılan hizmet uygularken. Yeniden bağlama oturum tabanlı davranış herhangi bir türde seçtiği bu gereksinimi karşılayan bir — güvenlik, Aktarım, güvenilir veya bileşimi. Tam davranışı bağlıdır <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> seçili değer. Hizmetinin yapılandırılan bağlama değerine uyuşmadığı <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, bir özel durum. Bağlamalar ve Destek oturumları oturum tabanlı olduğu söylenir oluşturdukları kanalları.  
  
 Aşağıdaki hizmet sözleşmesini belirleyen tüm işlemleri `ICalculatorSession` oturum içinde değiştirilen gerekir. İşlemlerin hiçbiri arayana dışında bir değer döndürür `Equals` yöntemi. Ancak, `Equals` yöntem parametre almayan ve bu nedenle, yalnızca sıfır olmayan bir değer, veri zaten geçirilmiş diğer işlemlerin bir oturumu içinde geri dönebilirsiniz. Bu sözleşme düzgün çalışması için bir oturum gerektirir. Belirli bir istemciyle ilişkili bir oturumu, bu istemcinin gönderdiği önceki hangi verilerin bilerek hiçbir şekilde hizmet örneği vardır.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Bir hizmet bir oturum izin veriyorsa, ardından oturumu oluşturulur ve istemci başlatıyorsa kullanılan; Aksi takdirde, hiçbir oturum oluşturulur.  
  
## <a name="sessions-and-service-instances"></a>Oturumlar ve hizmet örneği  
 WCF davranışını depolamasına varsayılan kullanırsanız, WCF istemci nesnesi arasındaki tüm çağrıları aynı hizmet örneği tarafından işlenir. Bu nedenle, uygulama düzeyinde bir oturumun uygulama davranışına benzer bir yerel arama davranıştır etkinleştirme olarak düşünebilirsiniz. Örneğin, yerel bir nesne oluştururken:  
  
-   Bir oluşturucu çağrılır.  
  
-   WCF istemcisi nesne başvurusu yapılan tüm sonraki çağrılar, aynı nesne örneği tarafından işlenir.  
  
-   Nesne başvurusu bozulduğunda bir yıkıcı adı verilir.  
  
 Varsayılan hizmet örneği davranışı kullanılan sürece oturumları istemcileri ve Hizmetleri arasındaki benzer bir davranış sağlar. Başlatma veya oturum ayarlayarak sonlandırma olarak bir hizmet sözleşmesini gerektirir ya da oturumları destekler, bir veya daha fazla sözleşme işlemleri işaretlenebilir <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> ve <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> özellikleri.  
  
 *İşlemleri başlatma* yeni bir oturum ilk işlem olarak çağrılmalıdır dosyalardır. Olmayan başlatma işlemlerini en az bir başlatma işlemi yalnızca çağrıldıktan sonra çağrılabilir. Bu nedenle oturum Oluşturucusu bir tür, hizmet örneği başına uygun istemcilerden giriş olabilmesi için tasarlanmış başlatma işlemlerini bildirerek hizmetiniz için oluşturabilirsiniz. (Oturum, ancak ve hizmet nesnesi ile ilişkili bir durumda.)  
  
 *İşlemleri sonlandırma*, buna karşılık, en son iletinin varolan bir oturumda çağrılmalıdır izinlerdir. Hizmet ilişkili oturum kapatıldıktan sonra varsayılan durumda, WCF Hizmeti nesnesi ve onun bağlamı geri dönüştürür. Bu nedenle, yıkıcı bir tür hizmet örneği sonuna uygun bir işlemi gerçekleştirmek için tasarlanmış sonlandırma işlemleri bildirerek oluşturabilirsiniz.  
  
> [!NOTE]
>  Varsayılan davranışı yerel oluşturucular ve yıkıcı bir benzerlik taşıyan rağmen bu yalnızca bir benzerlik gösterir. Herhangi bir WCF hizmeti işlemi başlatan bir sonlandırma işlemi veya aynı anda hem de olabilir. Ayrıca, varsayılan durumda işlemleri başlatma kez herhangi bir sayıda herhangi bir sırada çağrılabilir; oturum kurulmuş ve hizmet örneği ömrü açıkça kontrol sürece bir örneği ile ilişkili sonra hiçbir ek oturum oluşturulur (düzenleme tarafından <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> nesnesi). Son olarak, oturum ve hizmet nesnesi ile ilişkili bir durumda.  
  
 Örneğin, `ICalculatorSession` yukarıdaki örnekte kullanılan sözleşme gerektirir WCF istemcisini ilk çağrıda nesne `Clear` çağırdığındaişlemibaşkabirişlemve,öncebuWCFistemcinesnesioturumlasonlandırmak`Equals` işlemi. Aşağıdaki kod örneği, bu gereksinimlerini uygulayan bir sözleşme gösterir. `Clear` bir oturum başlatmak için önce çağrılmalıdır ve oturum ne zaman sona ereceğini `Equals` olarak adlandırılır.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Hizmetleri oturumları istemcileriyle başlatmayın. WCF istemci uygulamalarında oturum tabanlı kanal ömrü ve oturum ömrü arasında doğrudan bir ilişki bulunmaktadır. Bu nedenle, istemciler yeni oturum tabanlı kanallar oluşturarak yeni oturumlar oluşturabilirsiniz ve oturum tabanlı kanalları düzgün biçimde kapatarak oturumlarına kesmeden. Bir istemci, aşağıdakilerden birini çağırarak, bir hizmet uç noktası ile bir oturumu başlatır:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> bir çağrı tarafından döndürülen kanalda <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> tarafından oluşturulan WCF istemci nesnesinde [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
-   Her iki türü WCF istemci nesnesi üzerinde bir başlatma işlemi (varsayılan olarak, tüm işlemleri başlatma). İlk işlemi çağrıldığında, WCF istemci nesnesi, otomatik olarak kanal açar ve bir oturum başlatır.  
  
 Genellikle bir istemci, aşağıdakilerden birini çağırarak hizmet uç noktası ile bir oturumu sonlandırır:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> bir çağrı tarafından döndürülen kanalda <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> svcutil.exe tarafından oluşturulan WCF istemci nesnesi üzerinde.  
  
-   Her iki türü WCF istemci nesnesi üzerinde bir sonlandırma işlemi (varsayılan olarak, hiçbir işlem sonlandırma; sözleşme sonlandırma işlemi açıkça belirtmeniz gerekir). İlk işlemi çağrıldığında, WCF istemci nesnesi, otomatik olarak kanal açar ve bir oturum başlatır.  
  
 Örnekler için bkz: [nasıl yapılır: bir hizmet olduğundan gerektirir oturumları oluşturmak](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) yanı sıra [varsayılan hizmet davranışı](../../../docs/framework/wcf/samples/default-service-behavior.md) ve [Instancing](../../../docs/framework/wcf/samples/instancing.md) örnekleri.  
  
 İstemcileri ve oturumlar hakkında daha fazla bilgi için bkz: [bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumları InstanceContext ayarlarla etkileşim  
 Arasında bir etkileşim yoktur <xref:System.ServiceModel.SessionMode> bir sözleşme numaralandırmada ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> kanalları belirli hizmet nesneleri arasındaki ilişki denetimleri özelliği. Daha fazla bilgi için bkz: [oturumları, Instancing ve eşzamanlılık](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesneleri paylaşımı  
 Hangi oturum tabanlı kanalı kontrol edebilirsiniz veya çağrı, kendisiyle ilişkilendirilmiş <xref:System.ServiceModel.InstanceContext> kendiniz bu ilişkiyi gerçekleştirerek nesnesi. Tam bir örnek için bkz: [InstanceContextSharing](http://msdn.microsoft.com/library/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230).  
  
## <a name="sessions-and-streaming"></a>Oturumlar ve akış  
 Büyük miktarda veri aktarmak için sahip olduğunuzda, WCF akış aktarım modunda arabelleğe alma ve tamamen bellekte iletileri işleme varsayılan davranışı için uygun bir alternatiftir. Oturum tabanlı bir bağlamayla çağrıları akış sırasında beklenmeyen bir davranış elde edebilirsiniz. Tüm akış çağrılar kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, oturumlar desteklemeyen bir tek kanalı (veri birimi kanalı) yapılır. Birden çok istemci aynı hizmet nesnesi akış çağrıları üzerinden oturum tabanlı bağlama yapmak ve hizmet nesnenin eşzamanlılık modu tek ve onun örnek bağlamı modu ayarlanırsa ayarlamak `PerSession`, tüm çağrıları veri birimi kanalı ve bunu gitmeniz gerekir yalnızca bir çağrı aynı anda işlenir. Bir veya daha fazla istemciler daha sonra zaman aşımına olabilir. Her iki hizmet nesnenin ayarlayarak bu sorunun geçici çözümü `InstanceContextMode` için `PerCall` veya birden çok eşzamanlılık.  
  
> [!NOTE]
>  Kullanılabilir tek "oturumu" olduğundan MaxConcurrentSessions bu durumda herhangi bir etkisi yoktur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
