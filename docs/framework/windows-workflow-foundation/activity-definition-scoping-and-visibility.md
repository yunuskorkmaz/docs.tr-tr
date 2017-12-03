---
title: "Etkinlik tanımı kapsam ve görünürlük"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94ab623713a419426cbfd023c684741c69d3c8d5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="activity-definition-scoping-and-visibility"></a>Etkinlik tanımı kapsam ve görünürlük
Etkinlik tanımı kapsamı ve kapsamı gibi görünürlük ve bir nesne görünürlüğünü etkinlik üyeleri erişme olanağını diğer nesneleri ve etkinlikleri olur. Etkinlik tanımı aşağıdaki uygulamaları tarafından gerçekleştirilir:  
  
1.  Üyeleri belirleme (<xref:System.Activities.Argument>, <xref:System.Activities.Variable>, ve <xref:System.Activities.ActivityDelegate> nesneleri ve alt etkinlikleri) bir etkinlik, kullanıcılara kullanıma sunar.  
  
2.  Yürütme mantığını etkinliği uygulama  
  
 Uygulama etkinliğin tüketicilere açık değildir, ancak bunun yerine uygulama ayrıntılarını üyeleri gerektirebilir.  Benzer tür tanımı, etkinlik modeli tanımlanmakta etkinlik tanımının ilgili bir etkinlik üye görünürlüğünü nitelemek bir yazar olanak sağlar.  Bu görünürlük üye kullanım, veri kapsamı gibi yönlerini yönetir.  
  
## <a name="scope"></a>Kapsam  
 Veri kapsamı ek olarak, etkinlik modeli görünürlük, doğrulama, hata ayıklama, izleme veya izleme gibi etkinlik diğer yönlerini için erişimi kısıtlayabilirsiniz. Yürütme özelliklerini görünürlük ve yürütme özellikleri tanımının belirli bir kapsam için sınırlama kapsamı kullanın. İkincil kökleri görünürlük ve kullanma kapsamı tarafından yakalanan durum sınırlamak için bir <xref:System.Activities.Statements.CompensableActivity> kapsamına tanımının compensable etkinlikleri kullanılır.  
  
## <a name="definition-and-usage"></a>Tanımı ve kullanımı  
 Bir iş akışı temel etkinliğe sınıflardan devralmaya ve etkinlikten kullanarak yeni etkinlikler yazarak yazılır [yerleşik etkinlik Kitaplığı](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Bir etkinliği kullanmak için etkinlik Yazar tanımına alanının her bileşeni görünürlüğünü yapılandırmanız gerekir.  
  
### <a name="activity-members"></a>Etkinlik üyeleri  
 Etkinlik modeli bağımsız değişkenler, değişkenleri, temsilciler ve etkinlik tüketicilere kullanılabilmesini alt etkinlikler tanımlar. Bu üyelerinin her biri olarak bildirilebilir `public` veya `private`. Genel üyeler, etkinlik tüketici tarafından yapılandırılır, ancak `private` üyeleri etkinlik yazar tarafından sabit bir uygulama kullanın. Veri kapsamı için görünürlük kurallar aşağıdaki gibidir:  
  
1.  Genel üyeler ve ortak alt etkinlikler ortak üyelerine genel değişkenleri başvuruda bulunabilir.  
  
2.  Özel üyelerin ve ortak alt etkinlikler ortak üyelerine bağımsız ve özel değişkenler başvurabilirsiniz.  
  
 Bir etkinlik tüketici tarafından ayarlanabilir üyesi özel hiçbir zaman yapılmalıdır.  
  
### <a name="authoring-models"></a>Modelleri yazma  
 Özel etkinlikler kullanılarak tanımlanmış <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, veya <xref:System.Activities.AsyncCodeActivity>. Bu sınıflarından etkinlikler farklı görünürlüğe sahip farklı üye türleri getirebilir.  
  
#### <a name="nativeactivity"></a>NativeActivity  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity> kesinlik temelli kodda yazılır ve varolan etkinlikleri kullanarak isteğe bağlı olarak tanımlanabilir davranışa sahiptir. Etkinlikten türetme <xref:System.Activities.NativeActivity> çalışma zamanı tarafından gösterilen özelliklerin tümü, erişim verir. Bu tür bir aktivite herhangi bir üyesi olarak yalnızca bildirilebilir bağımsız değişkenleri dışında genel veya özel görünürlük kullanarak tanımlanabilir `public`.  
  
 Sınıf üyeleri türetilen <xref:System.Activities.NativeActivity> kullanarak çalışma zamanı bildirilen <xref:System.Activities.NativeActivityMetadata> yapısı geçirilen <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi.  
  
#### <a name="activity"></a>Etkinlik  
 Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.Activity> diğer etkinlikleri oluşturma aracılığıyla kesinlikle tasarlanmıştır davranışa sahiptir. <xref:System.Activities.Activity> Sınıfına sahip bir uygulama alt etkinlik, çalışma zamanı kullanılarak elde <xref:System.Activities.Activity.Implementation%2A>. Öğesinden türetilen bir etkinlik <xref:System.Activities.Activity> ortak bağımsız değişkenleri, genel değişkenler, içeri aktarılan ActivityDelegates ve içeri aktarılan etkinlikleri tanımlayabilirsiniz.  
  
 İçeri aktarılan ActivityDelegates ve etkinlikleri etkinlik ortak alt öğesi olarak bildirilmedi, ancak etkinlik tarafından doğrudan zamanlanamaz. Bu bilgiler, etkinlik hiçbir zaman burada yürütülmez konumda üst dönük doğrulamaları çalıştırmaktan kaçınmak için doğrulama sırasında kullanılır. Aynı zamanda, ortak alt gibi alınan alt başvurulan ve etkinliğin uygulaması tarafından zamanlanmış. Activity1 adlı bir etkinlik içe aktaran bir etkinlik içerebilir yani bir <xref:System.Activities.Statements.Sequence> kendi uygulamasında Activity1 zamanlar.  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity / AsyncCodeActivity  
 Taban sınıfı davranışı kesinlik temelli kod yazmak için kullanılır. Bu sınıftan türeyen etkinlikleri ortaya bağımsız değişken yalnızca erişimi. Bu, bu etkinlikler getirebilir yalnızca üyeleri ortak bağımsız değişkenleri şunlardır anlamına gelir. Diğer üyeleri veya görünürlüğe bu etkinlikler için geçerlidir.  
  
#### <a name="summary-of-visibilities"></a>Görünürlüğe özeti  
 Aşağıdaki tabloda, bu bölümdeki bilgiler özetlenmektedir.  
  
|Üye Türü|NativeActivity|Etkinlik|CodeActivity / AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Arguments|Ortak / özel|Ortak|Geçerli değil|  
|Değişkenler|Ortak / özel|Ortak|Geçerli değil|  
|Alt etkinlikler|Ortak / özel|Ortak, bir uygulama içinde tanımlanmış özel alt sabit.|Geçerli değil|  
|ActivityDelegates|Ortak / özel|Ortak|Geçerli değil|  
  
 Genel olarak, bir etkinlik tüketici tarafından ayarlanamaz üyesi ortak yapılmaması gerekir.  
  
### <a name="execution-properties"></a>Yürütme özellikleri  
 Bazı senaryolarda, aktivite ortak alt belirli yürütme özelliğine kapsam kullanışlıdır. <xref:System.Activities.ExecutionProperties> Koleksiyonu sağlayan bu özellik ile <xref:System.Activities.ExecutionProperties.Add%2A> yöntemi. Belirli bir özellik, tüm alt öğeleri veya yalnızca o genel kapsamlıdır olup olmadığını gösteren bir Boole parametresi bu yöntem vardır. Bu parametre ayarlanmışsa `true`, özelliği yalnızca Genel üyeler ve bunların ortak alt öğeleri ortak üyeleri için görünür olacak.  
  
### <a name="secondary-roots"></a>İkincil kökleri  
 İkincil bir kök maaş etkinliklerin durumunu yönetmek için çalışma zamanı'nın iç mekanizmadır. Zaman bir <xref:System.Activities.Statements.CompensableActivity> bitirdi çalıştıran, durumu hemen temizlenmez. Bunun yerine, maaş bölüm tamamlanana kadar durumu ikincil kök çalışma zamanı tarafından korunur. İkincil kök ile yakalanan konumu ortamları Compensable etkinlik kullanıldığı tanımı kapsamına karşılık gelir.
