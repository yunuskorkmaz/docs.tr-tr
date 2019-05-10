---
title: 'Nasıl yapılır: Kalıcı Olmayan Örnekleri Sorgulama'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: cbc3ec59bc0fbd8c39d351c248a664dc9231044c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584943"
---
# <a name="how-to-query-for-non-persisted-instances"></a>Nasıl yapılır: Kalıcı Olmayan Örnekleri Sorgulama
Bir hizmetin yeni bir örneği oluşturulur ve hizmette tanımlanan SQL iş akışı örneği Store davranışı olduğunu, hizmet ana bilgisayarı o hizmet örneği için bir ilk giriş örnek deposunda oluşturur. Hizmet örneği ilk kez daha sonra devam ederse, SQL iş akışı örneği Store davranış geçerli örneği durumu birlikte etkinleştirme, kurtarma ve denetim için gerekli olan ek verileri depolar.  
  
 İlk giriş örneği oluşturulduktan sonra bir örneği kalıcı değil, hizmet örneği kalıcı olmayan durumda olduğu söylenir. Tüm kalıcı hizmet örnekleri sorgulanabilir ve denetlenir. Kalıcı olmayan hizmet örnekleri sorgulanan denetlenen ne. Kalıcı olmayan bir örneği işlenmeyen bir özel durum nedeniyle askıya alınırsa sorgulanabilir ancak denetlenmedi.  
  
 Henüz kaybolacağından dayanıklı bir hizmet örnekleri aşağıdaki senaryolar kalıcı olmayan bir durumda kalır:  
  
- İlk kez örneği kalıcı önce hizmet ana bilgisayarı kilitleniyor. Örnek için ilk giriş örnek deposunda kalır. Örneği kurtarılabilir değil. İlişkili bir ileti geldiğinde, örneği tekrar etkin hale gelir.  
  
- İlk kez kalıcı önce örneği işlenmeyen bir özel durumla karşılaştığında. Aşağıdaki senaryolar ortaya  
  
    - Varsa değerini **UnhandledExceptionAction** özelliği **Abandon**, hizmet dağıtım bilgileri için örnek deposuna yazılır ve bellekten bir örneğidir. Örnek Kalıcılık veritabanı kalıcı olmayan durumda kalır.  
  
    - Varsa değerini **UnhandledExceptionAction** özelliği **AbandonAndSuspsend**, hizmet dağıtım bilgilerini Kalıcılık veritabanına yazılır ve örneği durumu içinayarlandı **Askıya**. Örneğin, iptal, sonlandırıldı veya sürdürülemez. Hizmet ana bilgisayarı henüz örneği kalıcı olmayan ve bu nedenle veritabanı girişi örneği için tam değil çünkü örneği yüklenemiyor.  
  
    - Varsa değerini **UnhandledExceptionAction** özelliği **iptal** veya **sonlandırma**, hizmet dağıtım bilgileri için örnek deposuna yazılır ve Örnek durum ayarlandığında **tamamlandı**.  
  
 Aşağıdaki bölümler, Kalıcılık SQL veritabanı'nda kalıcı olmayan örnekleri bulmak ve bu örnekler veritabanından silmek için örnek sorgular sağlar.  
  
## <a name="to-find-all-instances-not-persisted-yet"></a>Henüz kalıcı değil tüm örnekleri bulmak için  
 Aşağıdaki SQL sorgusunu kimliği ve oluşturma zamanı içinde kalıcı yapılmaz tüm örnekleri için henüz Kalıcılık veritabanına döndürür.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Tüm örnekleri henüz kalıcı değildir ve ayrıca yüklenmedi bulmak için  
 Aşağıdaki SQL sorgusunu kimliği ve oluşturma zamanı kalıcı değildir ve ayrıca yüklü olmayan tüm örnekleri için döndürür.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Henüz kalıcı değil askıya alınmış tüm örnekleri bulmak için  
 Aşağıdaki SQL sorgusunu kimliği, oluşturma zamanı, askıya alma nedeni ve askıya alınma özel durum adı kaybolacağından tüm örnekleri için ve ayrıca askıya alınma durumuna döndürür.  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Kalıcı olmayan örnekleri Kalıcılık veritabanından silmek için  
 Düzenli aralıklarla kalıcı olmayan örnekleri için örnek deposuna denetleyin ve örneği bağıntılı iletisi almaz eminseniz örnekleri örnek deposundan kaldırın gerekir. Örneğin, örnek veritabanında birkaç ay boyunca yapıldı ve iş akışı genellikle birkaç gün ömrü olduğunu bilmek, kilitlenen başlatılmamış örneği olduğunu varsaymak güvenli olurdu.  
  
 Genel olarak, yüklü değil veya askıya alınmadığından, kalıcı olmayan örnekleri silmek güvenlidir. Değil silmelisiniz **tüm** Bu örnek kümesi yalnızca oluşturulur ancak değil örnekleri içerdiğinden kalıcı olmayan örnekleri henüz kalıcı. Yalnızca yüklenen Örneğimiz vardı iş akışı hizmeti konağı bir özel durum oluştuğundan artıkları kalıcı olmayan örnekleri veya örnek kendi özel bir duruma neden silmeniz gerekir.  
  
> [!WARNING]
>  Kalıcı olmayan örnekleri örnek deposundan siliniyor deposunun boyutunu azaltır ve depolama işlemlerinin performansını iyileştirebilir.
