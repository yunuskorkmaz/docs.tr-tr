---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: kalıcı olmayan örnekler için sorgulama'
title: 'Nasıl yapılır: Kalıcı Olmayan Örnekleri Sorgulama'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 2cef64f97b32c5f1d31fa078200bc2fe15179485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777664"
---
# <a name="how-to-query-for-non-persisted-instances"></a>Nasıl yapılır: Kalıcı Olmayan Örnekleri Sorgulama

Bir hizmetin yeni bir örneği oluşturulduğunda ve hizmet SQL Iş akışı örnek deposu davranışını tanımlıysa, hizmet ana bilgisayarı örnek deposundaki bu hizmet örneği için bir başlangıç girişi oluşturur. Daha sonra hizmet örneği ilk kez devam ederse, SQL Iş akışı örnek deposu davranışı, geçerli örnek durumunu etkinleştirme, kurtarma ve denetim için gereken ek verilerle birlikte depolar.

Örnek için ilk giriş oluşturulduktan sonra bir örnek kalıcı değilse, hizmet örneği kalıcı olmayan durumda olarak kabul edilir. Tüm kalıcı hizmet örnekleri sorgulanabilir ve denetlenebilir. Kalıcı olmayan hizmet örnekleri, hiçbir şekilde sorgulanamaz ve denetlenemez. Kalıcı olmayan bir örnek işlenmeyen bir özel durum nedeniyle askıya alınırsa, sorgulanabilir ancak denetlenemez.

Henüz kalıcı olmayan dayanıklı hizmet örnekleri, aşağıdaki senaryolarda kalıcı olmayan bir durumda kalır:

- Hizmet ana bilgisayarı, örnek ilk kez kalıcı hale gelmeden önce kilitleniyor. Örnek için başlangıç girdisi örnek deposunda kalır. Örnek kurtarılabilir değil. Bağıntılı bir ileti alınırsa, örnek tekrar etkin hale gelir.

- Örnek, ilk kez kalıcı yapmadan önce işlenmemiş bir özel durumla karşılaşır. Aşağıdaki senaryolar ortaya çıkar

  - **UnhandledExceptionAction** özelliğinin değeri **Abandon** olarak ayarlandıysa, hizmet dağıtım bilgileri örnek deposuna yazılır ve örnek bellekten kaldırılır. Örnek, kalıcılık veritabanında kalıcı olmayan durumda kalır.

  - **UnhandledExceptionAction** özelliğinin değeri, **Andsusbekleto bırakma** olarak ayarlandıysa, hizmet dağıtım bilgileri kalıcılık veritabanına yazılır ve örnek durumu **askıya alındı** olarak ayarlanır. Örnek devam ettirilemez, iptal edilemez veya sonlandırılamıyor. Örnek henüz kalıcı olmadığı için hizmet ana bilgisayarı örneği yükleyemiyor, bu nedenle örnek için veritabanı girişi tamamlanmadı.

  - **UnhandledExceptionAction** özelliğinin değeri **Cancel** veya **Terminate** olarak ayarlandıysa, hizmet dağıtım bilgileri örnek deposuna yazılır ve örnek durumu **tamamlandı** olarak ayarlanır.

Aşağıdaki bölümlerde, SQL kalıcılık veritabanında kalıcı olmayan örnekleri bulacak ve bu örnekleri veritabanından silecek örnek sorgular sağlanmaktadır.

## <a name="to-find-all-instances-not-persisted-yet"></a>Henüz kalıcı olmayan tüm örnekleri bulmak için

Aşağıdaki SQL sorgusu, kalıcılık veritabanında kalıcı olmayan tüm örneklerin KIMLIĞINI ve oluşturulma zamanını döndürür.

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Henüz kalıcı olmayan ve yüklenmeyen tüm örnekleri bulmak için

 Aşağıdaki SQL sorgusu, kalıcı olmayan ve ayrıca yüklenmeyen tüm örnekler için KIMLIK ve oluşturma saati döndürür.

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Henüz kalıcı olmayan tüm askıya alınmış örnekleri bulmak için

Aşağıdaki SQL sorgusu, kalıcı olmayan ve ayrıca askıya alınmış durumda olan tüm örnekler için KIMLIK, oluşturma saati, askıya alma nedeni ve askıya alma özel durum adını döndürür.

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Kalıcı olmayan örnekleri kalıcılık veritabanından silmek için

Örnek depolama alanını kalıcı olmayan örnekler için düzenli olarak denetlemeniz ve örneğin bağıntılı bir ileti almadığınızdan emin olmanız durumunda örnek deposundan örnekleri kaldırmanız gerekir. Örneğin, örnek veritabanında birkaç ay boyunca bulunuyorsa ve iş akışının genellikle birkaç günün ömrü olduğunu biliyorsanız, bu, kilitlenen başlatılmamış bir örnek olduğunu varsaymak güvenli olacaktır.

Genel olarak, askıya alınmamış veya yüklenmeyen kalıcı olmayan örnekleri silmek güvenlidir. Bu örnek kümesi yeni oluşturulan ancak henüz kalıcı olmayan örnekleri içerdiğinden, kalıcı olmayan **Tüm** örnekleri silmemelisiniz. Yalnızca yüklü olan kalıcı olmayan örnekleri silmeniz gerekir, çünkü yüklenen örnek olan iş akışı hizmeti ana bilgisayarı bir özel duruma neden oldu veya örnek bir özel duruma neden oldu.

> [!WARNING]
> Örnek deposundan kalıcı olmayan örneklerin silinmesi deponun boyutunu düşürür ve mağaza işlemlerinin performansını iyileştirebilir.
