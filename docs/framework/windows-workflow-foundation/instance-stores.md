---
title: Örnek depoları
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 7ea29c3604042d773590448e31ce4ea95125ca1f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519584"
---
# <a name="instance-stores"></a>Örnek depoları
Bir örnek deposuna örnek bir mantıksal kapsayıcıdır. Örnek verileri ve meta verileri depolandığı yerdir. Bir örnek deposuna ayrılmış fiziksel depolama göstermez. Bir örnek depolama, SQL Server veritabanında kalıcı bilgi veya bellek dayanıklı olmayan durum bilgilerini içerebilir. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Somut bir iş akışı örneği verileri ve meta verileri bir SQL Server 2005 veya SQL Server 2008 veritabanına kalıcı hale getirmek sağlayan bir örnek deposuna uygulamasıdır SQL iş akışı örneği Store birlikte verilir. Buna ek olarak Windows Server App Fabric Ayrıca örnek deposunun somut bir uygulama sağlar. Daha fazla bilgi için [Windows Server App Fabric örneği Store, sorgu ve denetim sağlayıcıları](https://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 API Kalıcılık bir konak ve konak komut istekleri göndermek izin veren bir örnek deposuna arasındaki arabirimdir (örneğin, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> ve <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) örnek deposuna. Bu API'nin somut uygulama kalıcı bir sağlayıcı adı verilir. Kalıcı bir sağlayıcı konaktan isteklerini alır ve örnek deposuna değiştirir.  
  
 Konakları ve örnek depoları bir ana bilgisayar birçok örnek deposu ile kullanılabilir ve bir örnek deposuna ile birçok ana bilgisayarda kullanılabilir olacak şekilde eklenebilir. Bağımsız yaşam döngüsü üzerinde evrim geçirebileceğinden, ana bilgisayar ve örnek deposuna rağmen bir örnek deposuna genellikle belirli bir konağa kullanım düzenlerini için optimize edilmiştir. Örneğin, **WorkflowServiceHost** ve **SqlWorkflowInstanceStore** birlikte düzgün çalışacak şekilde tasarlanmıştır. Verileri ve iş akışı hizmet örneklerine meta verileri kalıcı hale getirmek ve bu örnek depoyu ile kullanmak için kendi örnek deposuna oluşturabilirsiniz **WorkflowServiceHost**. Örneğin, bir SQL Server veritabanına kaydetmeden yerine bir Oracle veritabanına bilgilerini kalıcı hale iş akışları sağlayan bir OracleWorkflowInstanceStore oluşturabilirsiniz.  
  
 Kalıcı nesneler değiştiren ek işlevlere sahip genişletilmesi konakları yaygındır. Örneğin, bir örnek Kalıcılık sistemi bir iş akışı ana bilgisayarı "Askıya Al" işlemini ve bir SQL örneği deposu destekleyen bir uzantı olabilir.  İş akışı ana bilgisayarı, standart bir komut gönderebilir gibi kaydedin veya bir iş akışı bir örneği Mağazası'ndan yüklemek veya kaydetmek veya bir iş akışı bir örnek deposuna kaydetmek için yükleme. Askıya alma uzantısı ek semantik kaydetme ve askıya alınan iş akışı örneği yüklenemiyor, iş akışı örnekleri yükleme komutları ekleyebilir. SQL örneği depolama için kalıcı bir sağlayıcı kaydetme ve iş akışı örnekleri yükleme komutları anlayan ve uygular uygun çağırarak komutları saklı kalıcı nesneleri bir SQL Server veritabanındaki tabloları değiştirme yordamları.  
  
 Bir konak, bir örnek deposunda bir örnek sahip olarak görev yapar. Bir konak aynı anda birden fazla örnek deposuna birden fazla örneğine sahip olarak çalışabilir. Ana bilgisayar örneği için örnekleriyle ilişkili anahtarları GUID'leri sağlar. Örneğini tanımlayan benzersiz bir diğer bir örnek anahtardır. Kalıcılık sistem oluşturur, güncelleştirir ve ana bilgisayar tarafından talep edilen komutları yürütür örneği sahibi bilgileri siler.  
  
 Aşağıdaki liste, konağın etkileşim Örnek Depolama ile ilgili önemli adımları içerir:  
  
1.  Elde bir **InstanceStore** bir Kalıcılık sağlayıcısı.  

2.  Çağırarak bir örneği için bir tanıtıcı elde <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> metodunda **InstanceStore**.  
  
3.  Örnek tanıtıcısını komutları çağırarak çağırma <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> metodunda **InstanceStore**.  
  
4.  İnceleme <xref:System.Runtime.DurableInstancing.InstanceView> tarafından döndürülen **InstanceStore.Execute** komutlarının sonuçlarını belirlemek için.
