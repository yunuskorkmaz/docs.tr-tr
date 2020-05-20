---
title: 'Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme'
description: İş akışları ve iş akışı hizmetleri için bir yapılandırma dosyası kullanarak, SQL Iş akışı örnek deposunu yapılandırmayı nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421520"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme

Bu konuda, iş akışları ve iş akışı hizmetleri için kalıcılığın nasıl etkinleştirileceği açıklanır.

## <a name="enable-persistence-for-workflows"></a>Iş akışları için kalıcılığı etkinleştir

Sınıfının özelliğini kullanarak bir örnek depoyu bir **WorkflowApplication** ile ilişkilendirebilirsiniz <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication> . <xref:System.Activities.WorkflowApplication.Persist%2A>Yöntemi, bir iş akışını uygulamayla ilişkili örnek deposuna kaydeder veya devam ettirir. <xref:System.Activities.WorkflowApplication.Unload%2A>Yöntemi, örnek deposunda bir iş akışı devam ettirir ve sonra örneği bellekten kaldırır. **Load** yöntemi, örnek kalıcılık deposunda depolanan iş akışı verilerini kullanarak bir iş akışını belleğe yükler.

**Persist** yöntemi aşağıdaki adımları gerçekleştirir:

1. İş akışı zamanlayıcısını duraklatır ve iş akışı boşta durumuna girene kadar bekler.

2. İş akışını devam ettirir veya kalıcılık deposuna kaydeder.

3. İş akışı zamanlayıcısını sürdürür.

 **Unload** yöntemi aşağıdaki adımları gerçekleştirir:

1. İş akışı zamanlayıcısını duraklatır ve iş akışı boşta durumuna girene kadar bekler.

2. İş akışını devam ettirir veya kalıcılık deposuna kaydeder.

3. İş akışı örneğini bellekte bırakır.

**Kalıcı** ve **kaldırma** yöntemlerinin her ikisi de iş akışı kalıcı olmayan bir bölgeden çıkana kadar kalıcı olmayan bir bölgede olduğunda engellenir. Kalıcı olmayan bölge tamamlandıktan sonra yöntem kalıcı veya kaldırma işlemine devam eder. Kalıcı olmayan bölge, zaman aşımı geçmeden önce tamamlanmazsa veya kalıcılık işlemi çok uzun sürerse, bir TimeoutException atılır.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Koddaki Iş akışı hizmetleri için kalıcılığı etkinleştir

Sınıfın **DurableInstancingOptions** üyesi, <xref:System.ServiceModel.WorkflowServiceHost> bir örnek deposunu **WorkflowServiceHost**Ile ilişkilendirmek için kullanabileceğiniz, **InstanceStore** adlı bir özelliğe sahiptir.

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

**WorkflowServiceHost** açıldığında, **DurableInstancingOptions. InstanceStore** null değilse Kalıcılık otomatik olarak etkinleştirilir.

Genellikle, bir hizmet davranışı, bir iş akışı hizmet ana bilgisayarıyla, **InstanceStore** özelliği kullanılarak kullanılacak somut örnek deposunu sağlar. Örneğin, Sqlworkflowcestorebehavior, **SqlWorkflowInstanceStore**'un bir örneğini oluşturur, yapılandırır ve **DurableInstancingOptions. InstanceStore**öğesine atar.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak Iş akışı hizmetleri için kalıcılığı etkinleştirme

Kalıcı hale getirme, App. config veya Web. config dosyanıza aşağıdaki kodu ekleyerek bir uygulama yapılandırma dosyası kullanılarak etkinleştirilebilir:

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
