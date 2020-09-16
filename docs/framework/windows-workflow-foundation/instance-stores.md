---
title: Örnek Depoları
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 26e0c28fe3061306a00e75b0498ef0781b7013c6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555802"
---
# <a name="instance-stores"></a>Örnek Depoları
Örnek deposu, örneklerin mantıksal bir kapsayıcısıdır. Örnek verilerinin ve meta verilerin depolandığı yerdir. Örnek deposu adanmış fiziksel depolama göstermez. Örnek deposu, bir bellek içinde SQL Server veritabanında veya dayanıklı olmayan durum bilgilerinde dayanıklı bilgiler içerebilir. , [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İş akışlarının örnek verileri ve meta verileri bir SQL Server 2005 veya SQL Server 2008 veritabanına kalıcı hale getirebileceği bir örnek deposunun somut bir uygulamasıdır, SQL Iş akışı örnek deposu ile birlikte gelir. Ayrıca, Windows Server App Fabric Ayrıca bir örnek deposunun somut bir uygulamasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric örnek deposu, sorgu ve denetim sağlayıcıları](/previous-versions/appfabric/ff383417(v=azure.10)).  
  
 Kalıcılık API 'SI, ana bilgisayar ile örnek deposu arasındaki arabirimdir, bu da konağın örnek deposuna komut istekleri göndermesini sağlar (örneğin, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> ve <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> ). Bu API 'nin somut uygulamasına kalıcılık sağlayıcısı denir. Kalıcılık sağlayıcısı bir konaktaki istekleri alır ve örnek deposunu değiştirir.  
  
 Konaklar ve örnek depoları, bir konağın birçok örnek depolarıyla kullanılabilmesi ve bir örnek deposunun birçok konak ile kullanılabilmesi için takılabilir. Örnek deposu genellikle belirli bir ana bilgisayarın kullanım desenleri için iyileştirilmiştir, ancak örnek deposu ve ana bilgisayar bağımsız yaşam döngülerinde geliştirilebilir. Örneğin, **WorkflowServiceHost** ve **SqlWorkflowInstanceStore** birlikte iyi çalışacak şekilde tasarlanmıştır. İş akışı hizmeti örneklerinin verilerini ve meta verilerini kalıcı hale getirmek ve bu örnek depoyu **WorkflowServiceHost**ile kullanmak için kendi örnek deponuzi oluşturabilirsiniz. Örneğin, iş akışlarının bilgileri bir SQL Server veritabanına kaydetmek yerine Oracle veritabanına kalıcı hale getirebilmenizi sağlayan bir OracleWorkflowInstanceStore oluşturabilirsiniz.  
  
 Ana bilgisayarların kalıcı nesneleri değiştiren ek işlevlerle genişletilmesi yaygındır. Örneğin, bir örnek Kalıcılık sisteminin bir iş akışı ana bilgisayarı, "askıya alma" işlemini destekleyen bir uzantı ve bir SQL örnek deposu olabilir.  İş akışı ana bilgisayarı bir örnek deposundan iş akışını kaydetmek veya yüklemek ya da bir iş akışını örnek deposuna kaydetmek için Kaydet veya yükle gibi standart bir komut gönderebilir. Askıya alma uzantısı, askıya alınmış bir iş akışı örneğinin yüklenememesi için iş akışı örneklerini kaydetme ve yükleme komutlarına ek semantik eklenebilir. SQL örneği deposu için kalıcılık sağlayıcısı, iş akışı örneklerini kaydetme ve yükleme komutlarını anlamıştır ve bir SQL Server veritabanındaki kalıcı nesnelerin tablolarını değiştiren uygun saklı yordamları çağırarak komutları uygular.  
  
 Bir ana bilgisayar örnek deposu içinde örnek sahibi görevi görür. Bir ana bilgisayar aynı anda birden fazla örnek deposuna sahip birden fazla örnek sahibi olarak davranabilir. Ana bilgisayar örneklerle ilişkili örnek anahtarlarına yönelik GUID 'Ler sağlar. Örnek anahtar, örneği tanımlayan benzersiz bir diğer addır. Kalıcılık sistemi, konaklar tarafından istenen komutları yürüten örnek sahibi bilgilerini oluşturur, güncelleştirir ve siler.  
  
 Aşağıdaki liste, örnek deposuyla ana bilgisayarın etkileşimiyle ilgili önemli adımları içerir:  
  
1. Kalıcılık sağlayıcısından bir **InstanceStore** edinin.  

2. <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> **InstanceStore**üzerinde yöntemini çağırarak bir örneğe olan tanıtıcıyı edinin.  
  
3. <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> **InstanceStore**üzerinde yöntemini çağırarak örnek tanıtıcısına karşı komutları çağırın.  
  
4. <xref:System.Runtime.DurableInstancing.InstanceView>Komutların sonuçlarını öğrenmek için **InstanceStore.Exeşirin** tarafından döndürülen ' i inceleyin.
