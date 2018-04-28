---
title: Örnek depolar
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a41c25dc3c664715bd9e811d6a21a6e3600aa8a5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="instance-stores"></a>Örnek depolar
Bir örnek deposuna örneklerinin mantıksal bir kapsayıcısıdır. Örnek veri ve meta veri depolandığı yerdir. Bir örnek deposuna ayrılmış bir fiziksel depolama göstermez. Bir örnek deposuna dayanıklı bir SQL Server veritabanında veya dayanıklı olmayan durum bilgileri bellek içerebilir. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Örnek verileri ve meta verileri bir SQL Server 2005 veya SQL Server 2008 veritabanına kalıcı hale getirmek iş akışları sağlayan bir örnek deposuna somut bir uygulamasıdır SQL iş akışı örneği deposuna birlikte verilir. Ayrıca Windows Server App Fabric ayrıca bir örnek deposuna somut bir uygulamasını sağlar. Daha fazla bilgi için bkz: [Windows Server App Fabric örnek deposu, sorgu ve denetim sağlayıcıları](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 API kalıcı bir ana bilgisayar ve komut istekleri göndermek ana bilgisayar tanır bir örnek deposuna arasındaki arabirimdir (örneğin, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> ve <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) örnek deposuna. Bu API somut uyarlamasını kalıcı bir sağlayıcı adı verilir. Kalıcılık sağlayıcı bir ana bilgisayardan isteklerini alır ve örnek deposuna değiştirir.  
  
 Konaklar ve örnek depolar; böylece bir ana bilgisayar birçok örnek depoları ile kullanılabilir ve bir örnek deposuna birçok konaklarla kullanılabilir eklenebilir. Örnek deposuna ve ana bilgisayar üzerinde bağımsız yaşam döngüsü gelişmesi ancak bir örnek deposuna genellikle belirli bir konağa kullanım desenlerini için optimize edilmiştir. Örneğin, **WorkflowServiceHost** ve **SqlWorkflowInstanceStore** birlikte çalışmak üzere tasarlanmıştır. Veri ve meta veri akışı hizmet örnekleri devam etmek ve bu örnek deposuna ile kullanmak için kendi örnek deposuna oluşturabilirsiniz **WorkflowServiceHost**. Örneğin, bir SQL Server veritabanına kaydetme yerine bir Oracle veritabanına bilgilerinin sürdürülmesi iş akışları sağlayan bir OracleWorkflowInstanceStore oluşturabilirsiniz.  
  
 Kalıcı nesneler değiştirir ek işlevsellik ile genişletilmesi konaklar için yaygın bir durumdur. Örneğin, bir örnek Kalıcılık sistemi bir iş akışı ana bilgisayar "Askıda" işlem ve bir SQL örneği deposu destekleyen uzantı olabilir.  İş akışı ana standart bir komut gönderebilir gibi kaydetmek veya bir iş akışı örneği deposundan yüklemek veya kaydetmek veya bir iş akışı bir örnek deposuna kaydetmek için yükleyin. Askıya alma uzantısı kaydetme ve askıya alınmış iş akışı örneği yüklenemiyor böylece iş akışı örnekleri yükleme komutları ek semantiği eklemek. SQL örneği depolama için Kalıcılık sağlayıcısı kaydetme ve iş akışı örnekleri yükleme komutları bilir ve bir SQL Server veritabanında kalıcı nesne tablolarını değiştirme yordamları Implements uygun çağırarak komutları depolanır.  
  
 Bir ana bilgisayar örneği deposundaki örneği sahibi olarak görev yapar. Bir ana bilgisayar aynı anda birden fazla örnek deposuna sahip birden fazla örneği sahibi olarak çalışabilir. Ana bilgisayar GUID'ler örneği için örnekleriyle ilişkili tuşlarını sağlar. Bir örneği anahtarı örneğini tanımlayan benzersiz bir diğer ad değil. Kalıcılık sistem oluşturur, güncelleştirir ve ana bilgisayarı tarafından istenen komutları yürütür gibi örneği sahibi bilgileri siler.  
  
 Aşağıdaki listede örnek deposuna ana bilgisayarın etkileşim dahil edilen önemli adımları içerir:  
  
1.  Elde bir **InstanceStore** Kalıcılık sağlayıcısından.  

2.  Bir örneği için tanıtıcı çağırarak elde <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> yöntemi **InstanceStore**.  
  
3.  Örnek tanıtıcı karşı komutları çağırarak çağırma <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> yöntemi **InstanceStore**.  
  
4.  İncelemek <xref:System.Runtime.DurableInstancing.InstanceView> tarafından döndürülen **InstanceStore.Execute** komutları sonuçlarını belirlemek için.
